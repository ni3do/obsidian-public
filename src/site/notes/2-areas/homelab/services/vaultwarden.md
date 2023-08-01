---
{"dg-publish":true,"permalink":"/2-areas/homelab/services/vaultwarden/","tags":["jarvis/media, jarvis/service"],"created":"","updated":""}
---

# [Bitwarden / Vaultwarden](https://vault.siwachter.com)
Bitwarden is a popular password manager that helps you securely store, organize, and access your passwords and other sensitive information. It offers a user-friendly interface and supports various platforms, including web browsers, mobile devices, and desktop applications. With Bitwarden, you can generate strong, unique passwords for each of your accounts, store them in an encrypted vault, and easily autofill login credentials whenever needed. It also provides features like secure notes, form filling, and password sharing with trusted individuals or teams. Bitwarden prioritizes security by employing end-to-end encryption to protect your data, both in transit and at rest. Additionally, it offers optional two-factor authentication for an extra layer of protection. Bitwarden is available as both a free and a premium service, with the premium version providing additional features and advanced security options.

---
## Kubernetes Config
Vaultwarden is deployed using a deployment, service and an ingress. The [Vaultwarden](vaultwarden/server:latest) image is used.

### Deployment
```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: vaultwarden
  name: vaultwarden
  namespace: vaultwarden
spec:
  template:
    metadata:
      labels:
        app: vaultwarden
    spec:
      securityContext:
        fsGroup: 1002
      volumes:
      - name: vaultwarden
        persistentVolumeClaim:
          claimName: vaultwarden-pvc
      containers:
      - env:
        - name: TZ
          value: Europe/Zurich
        - name: WEBSOCKET_ENABLED
          value: "true"
        - name: SENDS_ALLOWED
          value: "true"
        - name: SIGNUPS_ALLOWED
          value: "true"
        - name: SIGNUPS_VERIFY
          value: "true"
        - name: SIGNUPS_DOMAINS_WHITELIST
          value: "https://vault.siwachter.com"
        - name: ADMIN_TOKEN
          value: "psJTFFj6MlxECuPnuzrB+RzSqxWsdnijOdza+4W++VM1JfALa+pxwvpjyUACUNTa"
        - name: DOMAIN
          value: "https://vault.siwachter.com"
        - name: LOG_FILE
          value: "/data/vaultwarden.log"
        - name: LOG_LEVEL
          value: "warn"
        - name: EXTENDED_LOGGING
          value: "true"
        - name: PASSWORD_ITERATIONS
          value: "1000000"
        image: vaultwarden/server:latest
        imagePullPolicy: Always
        name: vaultwarden
        ports:
        - containerPort: 80
          name: vaultwarden-web  
        - containerPort: 3012
          name: vw-websocket   
        resources: {}
        volumeMounts:
        - mountPath: /data
          name: vaultwarden
          subPath: vw-data
      restartPolicy: Always
```

### Service
Vaultwarden has its own local IP
```yml
kind: Service
apiVersion: v1
metadata:
  name: vaultwarden
  namespace: vaultwarden
  annotations:
    metallb.universe.tf/allow-shared-ip: vaultwarden-ip
spec:
  selector:
    app: vaultwarden
  ports:                      
  - port: 80
    targetPort: 80
    name: vaultwarden-web
    protocol: TCP
  - port: 3012
    targetPort: 3012
    name: vw-websocket
    protocol: TCP
  type: LoadBalancer
  loadBalancerIP: 192.168.0.126
```

### Ingress
Vaultwarden is exposed under the ```vault.siwachter.com``` subdomain
```yml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: vaultwarden-ingress
  namespace: vaultwarden
  annotations:
    kubernetes.io/ingress.class: "traefik"
spec:
  rules:
  - host: vault.siwachter.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: vaultwarden
            port: 
              number: 80
```