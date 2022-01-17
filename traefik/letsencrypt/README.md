# docker swarm + TLS with letsencrypt

* `traefik.yml` defines traefik and external network `proxy`
* `whoami.yml` and `wordpress.yml` frontend services are attached to the external network `proxy`
* `--entrypoints.web.http.redirections.entrypoint.to=web-secured` is used in `traefik.yml` to reroute all http connections to https.
* a certificate is automatically generates with letsencrypt

### deploy

```bash
docker stack deploy -c traefik.yml traefik
docker stack deploy -c whoami.yml whoami
docker stack deploy -c wordpress.yml wordpress
```
