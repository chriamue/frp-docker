# frp-docker

FRP example how to use in docker-compose environment.

## quickstart

```bash
git clone https://github.com/chriamue/frp-docker.git
cd frp-docker
docker-compose build
docker-compose up
```

Add following to your /etc/hosts file, but remove it after the test:

```text
# /etc/hosts
127.0.0.1   hello.example.com
```

Now open [hello.example.com:8081](hello.example.com:8081).

You should see: Hello World from expressjs in a Docker container.

## add more services

```yaml
# docker-compose.frp.yml
services:
  web:
    image: chrispauley/express-helloworld
    frp_net:
      ipv4_address: 172.28.1.3
```

```ini
# frpc.ini
[express]
type = http
local_ip = 172.28.1.3
local_port = 8000
subdomain = web
```

```bash
docker-compose -f docker-compose.yml -f docker-compose.frp.yml up
```

## sources

[https://medium.com/@hc16/self-hosted-ngrok-alternative-using-frp-and-nginx-43ae6f325549](https://medium.com/@hc16/self-hosted-ngrok-alternative-using-frp-and-nginx-43ae6f325549)

[https://github.com/fatedier/frp](https://github.com/fatedier/frp)

[https://hub.docker.com/r/vimagick/frp/dockerfile](https://hub.docker.com/r/vimagick/frp/dockerfile)
[https://github.com/geektheripper/frp-docker](https://github.com/geektheripper/frp-docker)
