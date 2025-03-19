# Set Up cAdvisor for SONiC Device:

# 1. Run cAdvisor:
```bash
docker run \
  --volume=/:/rootfs:ro \
  --volume=/var/run:/var/run:rw \
  --volume=/sys:/sys:ro \
  --volume=/var/lib/docker/:/var/lib/docker:ro \
  --publish=8080:8080 \
  --detach=true \
  --name=cadvisor \
  google/cadvisor:latest
```
# 2. Set Up SSH Tunnel:

* My tunnel path: desktop -> sonic dev vm -> str-serv-acs-14 -> DUT.
```
ssh -L 8080:localhost:8080 -J daweihuang@10.52.0.72,daweihuang@10.64.247.30 admin@10.64.246.49
```

# 3. Access cAdvisor:
* Open a web browser and navigate to `http://localhost:8080`.
* You should see the cAdvisor web interface displaying metrics for the SONiC device.