# Traefik config

Simple traefik + portainer deployed with Docker Swarm behind Cloudflare.

Before deploying you need to do this steps:

## Create cloudflare_email secret

Create new docker secret called 'cloudflare_email' with:

`echo "email@example.com" | docker secret create cloudflare_email -`

## Create cloudflare_api secret

Create new docker secret called 'cloudflare_api' with your [cloudlfare api]()

`echo "email@example.com" | docker secret create cloudflare_email -`

API permission:

- Zone:Read
- DNS:Read
- DNS:Edit

# Create public network

Create a new external public network with:

`docker network create --attachable true --driver overlay public-net`

We can define this network inside traefik/docker-compose.yml to let Docker create it for ourself but in this way we can remove the Traefik service without redeploy all the container inside this network.
