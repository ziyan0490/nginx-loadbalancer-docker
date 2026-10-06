# Nginx Load Balancer with Docker Compose

Nginx reverse proxy load balancing traffic across 3 Nginx containers on AWS EC2.

## Tech
AWS EC2 (Amazon Linux 2023), Docker, Docker Compose, Nginx

## How it works
Client -> Nginx proxy (port 80) -> app1 / app2 / app3 (round-robin)

## Run
docker compose up -d
curl localhost

## Failover test
docker stop nginx-lb-app2-1
Traffic continues to the remaining servers.
