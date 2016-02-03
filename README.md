# registry-v2
Docker compose file and assets for deploying Docker Registry V2

## Deploy with docker compose

You need to install the latest *stable* release for compose. You may obtain that from [here](https://github.com/docker/compose/releases).

```

# to run interactive
docker-compose up

# to run in the background
docker-compose up -d
```

## Use registry

```
# login to registry
docker login localhost:6000

# enter Username / Password / email: admin / password / yourid@email.coms

# You should get a message like this: 
WARNING: login credentials saved in /home/youruser/.docker/config.json
Login Succeeded

# Test uploading an image
docker pull hello-world
...

# Re-tag image with registry fqdn

docker tag hello-world localhost:6000/hello-world

# Push image
docker push localhost:6000/hello-world 
```

## Known issues

This registry deployment comes with *sample self-signed certificates*. As such, you need to set the `--insecure-registry=<your-domain:port>` if you want to deploy this in a machine and access it from a different one over a network. 

Moreover, it is recommended that you *don't use* self-signed certificates and instead use certificates from a known and trusted CA.