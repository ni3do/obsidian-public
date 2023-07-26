---
{"dg-publish":true,"permalink":"/homelab/services/plex/","tags":["jarvis/service, jarvis/media"],"created":"","updated":""}
---

# [Plex](https://app.plex.tv)
Plex Media Server is a powerful media organization and streaming platform. It allows users to centralize their media collection, including movies, TV shows, music, and photos, on a computer or network-attached storage (NAS) device. Plex then indexes and organizes the media, providing an intuitive interface for users to access and stream their content across various devices, such as smartphones, tablets, smart TVs, and streaming devices. With features like on-the-fly transcoding, remote access, and robust media management, Plex makes it easy to enjoy your media library anytime, anywhere.
## Kubernetes Config
Deployed directly as a deployment using the [[homelab/nvidia-runtime-class\|nvidia runtime class]] and two services to expose it to the internet.

The [[priority-class\|priority class]] is set to ``high-priority`` to ensure the best possible performance, as this is one of the most sensitive and crucial services.
``securityContext`` is also set to use ``fsGroup: 1002`` as to not get any conflicts with the storage which resides on [[zfs\|ZFS]] pools on the main proxmox instance.
The container gets nvidia environment variables to be able to use the GPU.
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
```
