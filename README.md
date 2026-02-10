# custom-udi

## Build image

```
cd image

podman login registry.redhat.io

podman-compose --env-file .env build
```

*Teste*

```
podman run --rm -it quay.io/${QUAY_ORG}/${IMAGE_NAME}:${IMAGE_TAG} bash -lc '
  cat /etc/devspaces-linux-release
  az version | head -n 20
  oc version --client
  kubectl version --client
  helm version
  kind version
  cekit --version || true
  podman version
'
```