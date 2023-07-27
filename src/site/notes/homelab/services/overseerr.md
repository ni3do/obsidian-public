---
{"dg-publish":true,"permalink":"/homelab/services/overseerr/","tags":["jarvis/service, jarvis/media"],"created":"","updated":""}
---

# [Overseerr](https://overseerr.siwachter.com)
Overseerr is a self-hosted service that allows users to manage and request content for their media server. It integrates with popular media server applications like Plex, Emby, and Jellyfin, providing a user-friendly interface for requesting and tracking TV shows and movies. Users can create requests and vote on existing ones, helping to prioritize content additions. Overseerr also supports user authentication, allowing administrators to control access and manage user permissions. With its intuitive interface and customization options, Overseerr simplifies the process of content requests and management for media server enthusiasts.

---

## Kubernetes Config
Overseerr is deployed with a [[knowledge/computer-science/kubernetes/kubernetes-deployment\|deployment]], [[knowledge/computer-science/kubernetes/kubernetes-service\|service]] and an [[knowledge/computer-science/kubernetes/kubernetes-ingress\|ingress]]. The docker container is pulled from ```lscr.io/linuxserver/overseerr:latest```.

### Deployment
* ``securityContext`` is also set to use ``fsGroup: 1002`` as to not get any conflicts with the storage which resides on [[knowledge/computer-science/zfs|ZFS]] pools on the main proxmox instance. Further ```PGID``` and ```PUID``` variables are set to also match the ZFS pools.
* [Linuxserver docker mods](https://hub.docker.com/r/linuxserver/mods) are used to set the overseerr theme (this is native for this service but done for all other used services from linuxserver)
* Port ```5055``` is opened from the container
```yml
spec:
	template:
		spec:
			securityContext:
		        fsGroup: 1002
		    containers:
		    - env:
			    - name: PGID
		          value: "1002"
		        - name: PUID
		          value: "1002"
		        - name: DOCKER_MODS
		          value: ghcr.io/gilbn/theme.park:overseerr
		        - name: TP_THEME
		          value: overseerr
		        - containerPort: 5055
		          name: overseerr-web
```

### Service
One ```LoadBalancer``` service is used, which uses the shared ```media-ip```.
```yml
kind: Service
apiVersion: v1
metadata:
  name: overseerr
  namespace: media
  annotations:
    metallb.universe.tf/allow-shared-ip: media-ip
spec:
  selector:
    app: overseerr
  ports:                      
  - port: 5055
    targetPort: 5055
    name: overseerr-web
    protocol: TCP
  type: LoadBalancer
  loadBalancerIP: 192.168.0.122
```

### Ingress
[[homelab/traefik\|Traefik]] is used to expose the service on the subdomain [overseerr.siwachter.com](https://overseerr.siwachter.com).
```yml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: overseerr-ingress
  namespace: media
  annotations:
    kubernetes.io/ingress.class: "traefik"
spec:
  rules:
  - host: overseerr.siwachter.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: overseerr
            port: 
              number: 5055
```