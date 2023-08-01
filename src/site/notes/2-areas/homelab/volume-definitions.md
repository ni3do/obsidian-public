---
{"dg-publish":true,"permalink":"/2-areas/homelab/volume-definitions/","tags":["jarvis/media"],"created":"","updated":""}
---

# Volume Definitions
Volume definitions are pairs of [[3-ressources/computer-science/kubernetes/kubernetes-persistent-volume\|PersistensVolumes]] and [[3-ressources/computer-science/kubernetes/kubernetes-persistent-volume-claim\|PersistentVolumeClaims]].

## Existing mappings
| File                                                                        | pv-name              | pvc-name              | capacity | path                    | server        |
| --------------------------------------------------------------------------- | -------------------- | --------------------- | -------- | ----------------------- | ------------- |
| [[2-areas/homelab/volume-mappings/appdata-deluge\|appdata-deluge]]       | appdata-deluge-pv    | appdata-deluge-pvc    | 100Gi    | /data/appdata/deluge    | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/appdata-overseerr\|appdata-overseerr]] | appdata-overseerr-pv | appdata-overseerr-pvc | 100Gi    | /data/appdata/overseerr | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/appdata-plex\|appdata-plex]]           | appdata-plex-pv      | appdata-plex-pvc      | 200Gi    | /data/appdata/plex      | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/appdata-prowlarr\|appdata-prowlarr]]   | appdata-prowlarr-pv  | appdata-prowlarr-pvc  | 100Gi    | /data/appdata/prowlarr  | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/appdata-radarr\|appdata-radarr]]       | appdata-radarr-pv    | appdata-radarr-pvc    | 100Gi    | /data/appdata/radarr    | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/appdata-sabnzbd\|appdata-sabnzbd]]     | appdata-sabnzbd-pv   | appdata-sabnzbd-pvc   | 100Gi    | /data/appdata/sabnzbd   | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/appdata-sonarr\|appdata-sonarr]]       | appdata-sonarr-pv    | appdata-sonarr-pvc    | 100Gi    | /data/appdata/sonarr    | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/appdata-tautulli\|appdata-tautulli]]   | appdata-tautulli-pv  | appdata-tautulli-pvc  | 128Gi    | /data/appdata/tautulli  | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/cache\|cache]]                         | cache-pv             | cache-pvc             | 1Ti      | /data/cache             | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/download\|download]]                   | download-pv          | download-pvc          | 2Ti      | /data/download          | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/media\|media]]                         | media-pv             | media-pvc             | 26Ti     | /data/media             | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/nextcloud-data\|nextcloud-data]]       | nextcloud-data-pv    | nextcloud-data-pvc    | 1Ti      | /data/nextcloud-data    | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/nextcloud-mariadb\|nextcloud-mariadb]] | nextcloud-mariadb-pv | nextcloud-mariadb-pvc | 128Gi    | /data/nextcloud-mariadb | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/nextlcoud-config\|nextlcoud-config]]   | nextcloud-config-pv  | nextcloud-config-pvc  | 256Gi    | /data/nextcloud-config  | 192.168.0.112 |
| [[2-areas/homelab/volume-mappings/vaultwarden\|vaultwarden]]             | vaultwarden-pv       | vaultwarden-pvc       | 64Gi     | /data/vaultwarden       | 192.168.0.112 |

{ .block-language-dataview}

## Persistent Volume
Example definition for the base media storage:
```yml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: media-pv
  namespace: media
  labels:
    storage: nfs
spec:
  claimRef:
    name: media-pvc
    namespace: media
  capacity:
    storage: 26Ti
  accessModes:
    - ReadWriteMany
  persistentVolumeReclaimPolicy: Retain
  nfs:
    server: 192.168.0.112
    path: /data/media
```
## Persistent Volume Claim
Example definition for the base media storage:
```yml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: media-pvc
  namespace: media
spec:
  accessModes:
    - ReadWriteMany
  resources:
    requests:
      storage: 26Ti
  storageClassName: ""
  selector:
    matchLabels:
      storage: "nfs"
```