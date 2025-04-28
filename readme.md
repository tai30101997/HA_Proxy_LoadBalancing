# HAProxy Load Balancer Demo

This repository demonstrates a simple HAProxy load balancing setup with Docker. It includes:
- Docker Compose configuration for backend servers
- HAProxy configuration with different load balancing algorithms (Round Robin, Least Connections, etc.)

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/haproxy-load-balancer-configs.git
cd haproxy-load-balancer-configs


Run Backend Servers
  docker-compose up -d
Edit the haproxy.cfg to change the load balancing algorithm. For example:
	•	balance roundrobin
	•	balance leastconn
	•	balance random
	•	balance source
Run HAProxy with the configuration file:
  docker network create lb-net
  docker run -d --name haproxy-lb --network lb-net -p 8080:80 -v $(pwd)/haproxy.cfg:/usr/local/etc/haproxy/haproxy.cfg:ro haproxy:latest
