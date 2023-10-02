# GridCapa SWE CSA deployment module
[![MPL-2.0 License](https://img.shields.io/badge/license-MPL_2.0-blue.svg)](https://www.mozilla.org/en-US/MPL/2.0/)

This repository contains temporary deployment files for SWE CSA application:

- Docker Compose scripts for test and development usage
- Kubernetes scripts for production usage

## Deploying using Docker Compose

Docker Compose scripts needs Docker (version >= 18) and docker-compose.

```bash
docker-compose up -d
```

**Be careful to your local resources if you try to deploy too many processes it could be quite heavy.**

**Available Urls:**

* **Minio:** http://localhost/minio/  Default credentials are minioadmin/minioadmin.

* **RabbitMQ:** http://localhost/utils/rabbitmq/  Default credentials are guest/guest.

* **Postman:** https://localhost/rao-integration/convert-to-request
  - Use postman giving a zip and at timestamp on UCT format, to run a rao directly or to create a CSA Request message that might be sent by rabbitmq UI.

## Deploying using Kubernetes

Some secrets are needed on the cluster as deployment prerequisites. Encrypted password can be obtained by default bcrypt algorithm.

```bash
kubectl -n csa create secret generic gridcapa-rabbitmq-credentials --from-literal='rabbitmq-user=****' --from-literal='rabbitmq-password=****'
kubectl -n csa create secret generic gridcapa-minio-credentials --from-literal='minio-access-key=****' --from-literal='minio-secret-key=****'
```

### Deployment on Azure cluster

- host: gridcapa-csa.farao-community.com
- namespace: csa

To deploy on Rte Azure cluster: 
```bash
kubectl kustomize k8s/ | ssh farao@51.137.209.168 kubectl --kubeconfig=.kube/config_new -n csa apply  -f -
```

**Available Urls:**

* **Minio:** https://gridcapa-csa.farao-community.com/minio
* **RabbitMQ:** https://gridcapa-csa.farao-community.com/utils/rabbitmq/
* **Postman:** https://gridcapa-csa.farao-community.com/rao-integration/convert-to-request

![postman-post.png](..%2F..%2F..%2FImages%2Fpostman-post.png)
