# custom-udi

## Build image

```
podman login registry.redhat.io

podman-compose -f image/compose.yaml --env-file .env build
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

## Push to Quay

```
podman login quay.io

podman-compose -f image/compose.yaml --env-file .env push
```

## Configure Repository

Apply to user workspace namespace

```
oc apply -f public-yum-central-secret.yaml
```