# docker swarm + TLS with traefik default certificate

* traefik will automatically create a default certificate to use for TLS if no other valid certificate is provided
* `docker stack deploy -c default.yml default`
* Open `https://whoami.127.0.0.1.nip.io`
