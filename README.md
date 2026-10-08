# Nginx Load Balancer with Docker Compose

Nginx reverse proxy load balancing traffic across 3 Nginx containers, deployed on AWS EC2.

## Architecture

Client -> Nginx proxy (port 80) -> app1 / app2 / app3 (round-robin)

## Tech Stack

- AWS EC2 (Amazon Linux 2023)
- Docker & Docker Compose
- Nginx

## Project Structure

.
├── docker-compose.yml
├── nginx.conf
├── app1/index.html
├── app2/index.html
└── app3/index.html

## Prerequisites

- Docker and Docker Compose installed
- Port 80 open in the EC2 Security Group

## How to Run

git clone https://github.com/ziyan0490/nginx-loadbalancer-docker.git
cd nginx-loadbalancer-docker
docker compose up -d

## Test Load Balancing

Run this several times and watch the response change between app1, app2 and app3:

curl localhost

## Failover Test

docker stop nginx-lb-app2-1
curl localhost

Traffic continues to the remaining servers.

## Cleanup

docker compose down

## What I Learned

- How a reverse proxy distributes traffic using round-robin
- Defining multi-container setups with Docker Compose
- How failover keeps a service available when a container stops
- Opening ports with EC2 Security Groups
