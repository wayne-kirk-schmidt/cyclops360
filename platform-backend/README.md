# CyclOps360 Backend

## Core Infrastructure

This setup includes:
- PostgreSQL (persistent data)
- Redis (caching and task coordination)
- Kafka + Zookeeper (message streaming)
- MinIO (object storage)

## Microservices (to be implemented)

- core-api
- web-admin-ui
- discovery-agent
- cmdb-service
- alert-engine
- snapshot-manager
- automation-engine
- auth-service
- reporting-logs

## Deployment Instructions (Local - Docker Swarm)

```bash
docker swarm init
docker stack deploy -c docker-compose.yml cyclops360
```
