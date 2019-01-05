# discourse
Discourse application for IndieHosters network

# How to use this image

The easiest is to use our `docker-compose.yml`.

Make sure you have [docker-compose](http://docs.docker.com/compose/install/) installed. And then:

```
docker network create lb_web
git clone https://github.com/indiehosters/discourse.git
cd discourse
./scripts/install
docker-compose up
```

Once it is done, you can open your browser and connect to the IP of the container: http://container_ip.

If you want to access it via the IP of the HOST, add this line to `docker-compose.yml`:
```
web:
...
  ports:
    - "80:80"
...
```

You can now access your instance on the port 80 of the IP of your machine.

## Accees it from Internet

We recommend the usage of TLS.

Once it is done, you can connect to the port of the host by adding this line to `docker-compose.yml`:
```
web:
...
  ports:
    - "443:443"
    - "80:80"
...
```

##Environment variables

./scripts/install expects certain environment variables to be in place.
You will be asked for these values if they do not already exist.

```
VIRTUAL_HOST=host-domain
DISCOURSE_SMTP_ADDRESS=smtp-host
DISCOURSE_SMTP_USER_NAME=smtp-host-username
DISCOURSE_SMTP_PASSWORD=smtp-host-password
DISCOURSE_DB_PASSWORD=postgres-database-password
POSTGRES_PASSWORD=postgres-database-password
SUBNET=0
POSTGRES_VERSION=10.6
```

You can prepopulate these environment variables by copying example.env to .env and changing the values to suit your environment.

