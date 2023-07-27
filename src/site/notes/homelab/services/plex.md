---
{"dg-publish":true,"permalink":"/homelab/services/plex/","tags":["jarvis/service, jarvis/media"],"created":"","updated":""}
---

# [Plex](https://app.plex.tv)
Plex Media Server is a powerful media organization and streaming platform. It allows users to centralize their media collection, including movies, TV shows, music, and photos, on a computer or network-attached storage (NAS) device. Plex then indexes and organizes the media, providing an intuitive interface for users to access and stream their content across various devices, such as smartphones, tablets, smart TVs, and streaming devices. With features like on-the-fly transcoding, remote access, and robust media management, Plex makes it easy to enjoy your media library anytime, anywhere.

---

## Kubernetes Config
Plex is deployed directly as a [[knowledge/kubernetes-deployment\|deployment]] using the [ghcr.io/linuxserver/plex](https://ghcr.io/linuxserver/plex) image and two [[knowledge/kubernetes-service\|services]] to expose it to the internet.

### Deployment
* The [[knowledge/priority-class\|priority class]] is set to ``high-priority`` to ensure the best possible performance, as this is one of the most sensitive and crucial services.
* ``securityContext`` is also set to use ``fsGroup: 1002`` as to not get any conflicts with the storage which resides on [[knowledge/zfs\|ZFS]] pools on the main proxmox instance. Further ```PGID``` and ```PUID``` variables are set to also match the ZFS pools.
* The container gets nvidia environment variables to be able to use the GPU.
```yml
spec:
	template:
		spec:
			priorityClassName: high-priority
			nodeSelector:
				gpu: nvidia
			securityContext:
				fsGroup: 1002
			containers:
				- env:
					- name: NVIDIA_VISIBLE_DEVICES
					  value: all
					- name: NVIDIA_DRIVER_CAPABILITIES
					  value: all
					- name: PGID
					  value: "1002"	
					- name: PUID	
					  value: "1002"
```
### Services
Two services are used, one for [[knowledge/tcp|TCP]] and one for [[knowledge/udp|UDP]].  The two are equivalent except for the different ports (not all listed here). Both are ```LoadBalancer``` types and use the ```media-ip``` address
```yml
kind: Service
apiVersion: v1
metadata:
	name: plex-tcp
	namespace: media
	annotations:
		metallb.universe.tf/allow-shared-ip: media-ip
spec:
	selector:
		app: plex
	ports:
	- port: 32400
	  targetPort: 32400
	  name: pms-web
	  protocol: TCP
	type: LoadBalancer
	loadBalancerIP: 192.168.0.122
```
### Volumes
Only ```/config``` and ```/data``` paths are used. Volume definitions can be found at [[homelab/volume-definitions]]
```yml
spec:
	template:
		spec:
			volumes:
				- name: appdata-plex
					persistentVolumeClaim:
					claimName: appdata-plex-pvc
				- name: media
					persistentVolumeClaim:
					claimName: media-pvc
			containers:
			volumeMounts:
			- mountPath: /config
			  name: appdata-plex
			- mountPath: /data
			  name: media
```
