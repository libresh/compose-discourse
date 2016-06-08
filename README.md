# discourse
Discourse application for IndieHosters network

# How to use this image

The easiest is to use our `docker-compose.yml`.

Make sure you have [docker-compose](http://docs.docker.com/compose/install/) installed. And then:

```
git clone https://github.com/indiehosters/discourse.git
cd discourse
# edit variables:
vi env
docker-compose run app bash -c "sleep 3 && rake db:migrate assets:precompile"
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
