# Docker Debugging with `docker events`
## Overview
Everyone uses Docker, but very few really know how to debug containers effectively. No, I’m not talking about `docker logs`, `docker inspect`, or `docker exec`. I’m talking about `docker events`. Most likely, you didn’t even know it existed. It streams **low-level Docker daemon events**, not just for your container, but for everything happening in the system.
## Common Scenario
Imagine this situation: a container keeps restarting in production, but locally everything works fine. The usual debugging ritual:
```bash
docker logs <container>   # empty
docker inspect <container> # static info
docker exec -it <container> bash # too late, container already dead
```
Sound familiar? Then you probably start tweaking the Dockerfile and running `docker run` in circles, because you’ve never used `docker events`.
## The Real Solution
Try this:
```bash
docker events --filter container=<your_container_id>
```
Sample output:
```
2025-05-04T18:20:01Z container create ...
2025-05-04T18:20:02Z container start ...
2025-05-04T18:20:03Z container health_status: unhealthy ...
2025-05-04T18:20:04Z container kill signal=SIGTERM
2025-05-04T18:20:04Z container restart
```
There it is: Healthcheck failed → container killed → Docker auto-restarted it. Your usual logs won’t show this, because the healthcheck runs outside your main process.
## Bonus Tips
Filter by time:
```bash
docker events --since 30m --until "2025-05-04T18:00:00"
```
Structured JSON output:
```bash
docker events --format '{{json .}}'
```
Full system picture:
```bash
docker events
```
## Why Not Just Metrics?
Before someone says: "In normal infra we have Grafana, Loki, Prometheus, observability, etc…" — yes, sure. Good luck debugging with them when: OOM kills happen before metrics are collected, volumes fail to mount, init container crashes, sidecar silently restarts. `docker events` sees all of it in real time.
## Key Takeaway
If you debug Docker without `docker events`, you’re not debugging — you’re guessing.
