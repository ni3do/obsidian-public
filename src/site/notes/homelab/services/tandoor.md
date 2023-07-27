---
{"dg-publish":true,"permalink":"/homelab/services/tandoor/","tags":["jarvis/media, jarvis/service"],"created":"","updated":""}
---

# [Tandoor](https://recipes.siwachter.com)
Tandoor Recipe Manager is a versatile and comprehensive tool designed to help users organize and manage their recipes. It offers a user-friendly interface that allows users to input, store, and categorize their recipes for easy retrieval. With Tandoor, users can add detailed information such as ingredients, instructions, cooking times, and serving sizes to each recipe. The tool also provides advanced features like ingredient scaling, meal planning, and shopping list generation, making it convenient for users to plan and prepare meals. Tandoor Recipe Manager is a valuable resource for individuals looking to streamline their recipe management process and enhance their cooking experience.

---
## Kubernetes Config
Tandoor is deployed using the Kubernetes installation method from their [docs](https://docs.tandoor.dev/install/kubernetes/).
Only minimal changes are done, one important one is to add ```securityContext``` to access the [[knowledge/zfs|ZFS]] pools where the persistent data is stored.
### Service
The service has its own local IP.
```yml
apiVersion: v1
kind: Service
metadata:
  name: recipes
  labels:
    app: recipes
    tier: frontend
  annotations:
    metallb.universe.tf/allow-shared-ip: tandoor-ip
spec:
  selector:
    app: recipes
    tier: frontend
    environment: production
  ports:
  - port: 80
    targetPort: 80
    name: http
    protocol: TCP
  - port: 8080
    targetPort: 8080
    name: gunicorn
    protocol: TCP
  type: LoadBalancer
  loadBalancerIP: 192.168.0.125

```

### Ingress
Tandoor is exposed to the ```recipes.siwachter.com``` subdomain using [[homelab/traefik|traefik]].
```yml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  annotations:
    kubernetes.io/ingress.class: "traefik"
  name: recipes
spec:
  rules:
  - host: recipes.siwachter.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: recipes
            port:
              number: 8080
      - path: /media
        pathType: Prefix
        backend:
          service:
            name: recipes
            port:
              number: 80
      - path: /static
        pathType: Prefix
        backend:
          service:
            name: recipes
            port:
              number: 80
```