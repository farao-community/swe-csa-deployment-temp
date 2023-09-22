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

Multiple urls are available:
- RabbitMQ management UI on page http://localhost/utils/rabbitmq/. Default credentials are guest/guest.
- MinIO browser on page http://localhost/minio/. Default credentials are minioadmin/minioadmin.
- Use postman giving a zip and at timestamp on UCT format, to run a rao directly or to create a CSA Request message that might be sent by rabbitmq UI.

// TODO to complete with screenshots

## Deploying using Kubernetes
TODO
