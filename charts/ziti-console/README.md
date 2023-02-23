# ziti-console

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: latest](https://img.shields.io/badge/AppVersion-latest-informational?style=flat-square)

Deploy OpenZiti console as kubernetes service

## Minimal Installation

This chart deploys a pod running `ziti-console`, [the OpenZiti console](https://github.com/openziti/ziti-console/).

After adding the charts repo to Helm then you may install the chart. You must supply some values, i.e. the name the console listens on.

This is this sample from the quickstart:

```bash
helm install quickstart-console ziti-console \
     --set "ingress.enabled=true" \
     --set "ingress.hosts[0].host=quickstart-console.<example.org>" \
     --set "ingress.annotations.traefik\.ingress\.kubernetes\.io/router\.entrypoints=websecure" \
     --set "ingress.labels.ingressMethod=traefik"
    --set "settings.edgeControllers[0].name=quickstart" \
    --set "settings.edgeControllers[0].url=https://quickstart-controller-mgmt:1281" \
    --set "settings.edgeControllers[0].default=true" \

```

## Values Reference

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| fullnameOverride | string | `""` |  |
| httpContainerPort | int | `1408` |  |
| image.args | list | `[]` |  |
| image.command[0] | string | `"node"` |  |
| image.command[1] | string | `"/usr/src/app/server.js"` |  |
| image.command[2] | string | `"debug"` |  |
| image.pullPolicy | string | `"Always"` |  |
| image.pullSecrets | list | `[]` |  |
| image.repository | string | `"openziti/zac"` |  |
| ingress.annotations | object | `{}` |  |
| ingress.enabled | bool | `true` |  |
| ingress.hosts[0].host | string | `"ziti-console.domain.tld"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"Prefix"` |  |
| ingress.ingressClassName | string | `""` |  |
| ingress.labels | object | `{}` |  |
| ingress.tls | list | `[]` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext.fsGroup | int | `1000` |  |
| podSecurityContext.runAsGroup | int | `1000` |  |
| podSecurityContext.runAsUser | int | `1000` |  |
| ports[0].containerPort | int | `1408` |  |
| ports[0].name | string | `"http"` |  |
| replicas | int | `1` |  |
| resources | object | `{}` |  |
| securityContext | string | `nil` |  |
| service.annotations | object | `{}` |  |
| service.enabled | bool | `true` |  |
| service.labels | object | `{}` |  |
| service.name | string | `"http"` |  |
| service.port | int | `1408` |  |
| service.type | string | `"ClusterIP"` |  |
| settings.edgeControllers | list | `[]` |  |
| settings.fabricControllers | list | `[]` |  |
| tolerations | list | `[]` |  |

## Sample `my-values.yaml`

This is a minimal `values.yaml` sample for an k3s-enviroment using traefik as ingress loadbalancer:

```yaml
ingress:
  enabled: true
  annotations:
    traefik.ingress.kubernetes.io/router.entrypoints: websecure
  labels:
    ingressMethod: traefik
  hosts:
    - host: quickstart-console.<example.org>

settings:
  edgeControllers:
    - name: quickstart
      url: https://quickstart-controller-mgmt:1281
      default: true
```

<!-- generated with helm-docs -->