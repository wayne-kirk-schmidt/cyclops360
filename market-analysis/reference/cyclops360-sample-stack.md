# CyclOps360: Backend Architecture and Orchestration

## Confirmed Architecture Stack

| Component       | Technology                             |
| --------------- | -------------------------------------- |
| Database        | PostgreSQL                             |
| Cache/Queue     | Redis                                  |
| Stream Bus      | Kafka                                  |
| Object Storage  | MinIO                                  |
| Orchestration   | Docker Swarm                           |
| Delivery Target | Local build (single-node Docker Swarm) |

## Microservices Structure

* core-api
* web-admin-ui
* discovery-agent
* cmdb-service
* alert-engine
* snapshot-manager
* automation-engine
* auth-service
* reporting-logs

Each service is scaffolded and will later be implemented in containers, communicating via Docker overlay network.

## Data Flow (First Pass)

1. discovery-agent observes and collects device data
2. Sends device info to cmdb-service for asset tracking
3. snapshot-manager checks configuration diffs and baselines
4. alert-engine applies rules and ML-based alerts
5. automation-engine runs orchestrated tasks based on user triggers or alert rules
6. web-admin-ui displays system state via core-api

## Deployment Readiness

* Docker Compose file includes PostgreSQL, Redis, Kafka (with Zookeeper), and MinIO
* Overlay network enabled for inter-service communication
* Docker Swarm support for local testing and scalable production rollout
* Service folders created for all microservices
* README provides command to deploy locally via Docker Swarm

```bash
docker swarm init
docker stack deploy -c docker-compose.yml cyclops360
```

