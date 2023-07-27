---
{"dg-publish":true,"permalink":"/homelab/services/nextcloud/","tags":["jarvis/media, jarvis/service"],"created":"","updated":""}
---

# [Nextcloud](https://cloud.siwachter.com)
Nextcloud is an open-source, self-hosted personal cloud platform that allows you to securely store, share, and access your files, documents, photos, and other data. With Nextcloud, you have full control over your data, as it can be installed on your own server, giving you privacy and security. It offers features similar to popular cloud storage services, such as file synchronization, file sharing, collaboration tools, and calendar and contact management. Nextcloud also provides a range of additional apps and integrations, making it a versatile solution for individuals, families, and small businesses looking to have their own personal cloud.

---

## Kubernetes Config
Nextcloud is deployed via Helm chart from [official Nextlcoud repository](https://github.com/nextcloud/helm/tree/main/charts/nextcloud) 
### Base Config
* ```cloud.siwachter.com``` subdomain is used to host nextcloud
* ``securityContext`` is also set to use ``fsGroup: 1002`` as to not get any conflicts with the storage which resides on [[knowledge/zfs\|ZFS]] pools on the main proxmox instance. Further ```PGID``` and ```PUID``` variables are set to also match the ZFS pools.
* Many ```php``` configs are set. There are still some thins to configure, external ips are not seen by nextcloud, only sees internal ip of traefik. **This is not yet final!**
* ```skeletondirectory``` is set empty to not create base file structure when creating new users
```yml
nextcloud:
  host: cloud.siwachter.com
  username: admin
  password: choose-a-strong-password
  update: 0
  datadir: /var/www/html/data
  podSecurityContext:
    fsGroup: 1002
    runAsUser: 1002
  containerSecurityContext:
    fsGroup: 1002
    runAsUser: 1002
  configs:
    custom.config.php: |-
        <?php
        $CONFIG = array (
          'filelocking.enabled' => 'true',
          'loglevel' => '1',
          'log_type' => 'file',
          'trusted_domains' =>
            [
              'localhost',
              'cloud.siwachter.com',
              '10.42.2.27'
            ],
          'trusted_proxies' =>
            [
              '10.42.0.0/24',
              '10.42.1.0/24',
              '10.42.2.0/24',
              '10.42.3.0/24',
              '10.43.1.0/24',
              '10.42.2.27'
            ],
          'forwarded_for_headers' =>
            [
              'CF-CONNECTING-IP',
              'Cf-Connecting-Ip'
            ],
          'overwrite.cli.url' => 'https://cloud.siwachter.com',
          'skeletondirectory' => '',
        );
```

### Service
Service is set up as ```LoadBalancer``` and uses it's own designated IP. ```externalTrafficPolicy``` is set to ```Local``` in the attempt to get nextcloud to see the external IP **Not working!!**
```yml
service:
  type: LoadBalancer
  port: 80
  loadBalancerIP: 192.168.0.124
  annotations:
    metallb.universe.tf/allow-shared-ip: nextcloud
  spec:
    externalTrafficPolicy: Local
```

### Persistence
Persistence is enabled by using designated volumes on the [[knowledge/zfs|ZFS]] pools.
```yml
persistence:
  # Nextcloud Data (/var/www/html)
  enabled: true
  existingClaim: nextcloud-config-pvc
  accessMode: ReadWriteOnce
  # size: 256
  nextcloudData:
    enabled: true
    existingClaim: nextcloud-data-pvc
    accessMode: ReadWriteOnce
    size: 1Ti
```

### Ingress Config
The ingress is configured to use [[homelab/traefik\|Traefik]]. ```preserve-host``` annotation is set in attempt to let nextcloud see external ip **Not working atm!**
```yml
ingress:
  enabled: true
  annotations:
    kubernetes.io/ingress.class: "traefik"
    traefik.ingress.kubernetes.io/preserve-host: "true"
  labels: {}
```

### External Database Config
The internal Database is disabled, as advised in production enviroments.
**Should swap to use [[homelab/kubernetes-secret\|Kubernetes Secret]]**

```yml
externalDatabase:
  enabled: true
  ## Supported database engines: mysql or postgresql
  type: mysql
  ## Database host
  host: nextcloud-mariadb
  ## Database user
  user: nextcloud
  ## Database password
  password: choose-a-strong-password
  ## Database name
  database: nextcloud
  ## Use a existing secret
  existingSecret:
    enabled: false
    # secretName: nameofsecret
    # usernameKey: username
    # passwordKey: password
```

### MariaDB 
MariaDB is the chosen external database.
* ```podSecurityContext``` and ```containerSecurityContext``` are set to ensure smooth access to the [[knowledge/zfs|ZFS]] pools.
* Corresponding [[homelab/kubernetes-persistent-volume-claim|PVC]] is mapped
```yml
mariadb:
  enabled: true
  port: 3306
  db:
    name: nextcloud
    user: nextcloud
    password: choose-a-strong-password
    rootPassword: choose-a-strong-password
  primary:
    podSecurityContext:
      enabled: true
      fsGroup: 1002
      runAsUser: 1002
    containerSecurityContext:
      enabled: true
      fsGroup: 1002
      runAsUser: 1002
    persistence:
      enabled: true
      existingClaim: nextcloud-mariadb-pvc
      accessMode: ReadWriteOnce
      size: 128Gi
```

### Redis
Redis is enabled
```yml
redis:
  enabled: true
  usePassword: false
```

### Cronjob
Cronjob is enabled with default settings.
```yml
cronjob:
  enabled: true
  # Every 15 minutes
  # Note: Setting this to any any other value than 15 minutes might
  #  cause issues with how nextcloud background jobs are executed
  schedule: "*/15 * * * *"
  annotations: {}
  # Set curl's insecure option if you use e.g. self-signed certificates
  curlInsecure: false
  failedJobsHistoryLimit: 5
  successfulJobsHistoryLimit: 2
```

### Prometheus Exporter / Metrics
Values are left at defaults.
```yml
metrics:
  enabled: true
  replicaCount: 1
  https: true
  timeout: 5s
  image:
    repository: xperimental/nextcloud-exporter
    tag: v0.3.0
    pullPolicy: IfNotPresent
  service:
    type: ClusterIP
    annotations:
      prometheus.io/scrape: "true"
      prometheus.io/port: "9205"
    labels: {}
```