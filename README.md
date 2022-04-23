# 🐳 5 steps to set up reverse proxy and HTTPS (SSL certificate) for Docker container

1. Create Docker compose file for nginx-proxy stacks same as [nginx-proxy.yaml](https://github.com/atbee/docker-https/blob/main/nginx-proxy.yaml)

2. Run nginx-proxy stacks

```bash
$ docker-compose -f nginx-proxy.yaml up -d
```

3. Add these environment variables to your container, for example [whoami.yaml](https://github.com/atbee/docker-https/blob/main/whoami.yaml)

  - VIRTUAL_HOST - *Domain to access the container*
  - VIRTUAL_PORT - *Container port*
  - LETSENCRYPT_HOST - *Domain for issuing SSL certificate by Let's Encrypt*
  - LETSENCRYPT_EMAIL - *Your email for Let's Encrypt notifications*

4. Start/Restart the container

```bash
# example
$ docker-compose -f whoami.yaml up -d
```

5. Test

Run the following command to test the reverse proxy locally

```bash
$ curl -L -H "Host: <YOUR_DOMAIN>" localhost
```

Then go to your domain on browser for HTTPS and SSL certificate verification

---

Thanks [nginx-proxy](https://github.com/nginx-proxy/nginx-proxy) for the awesome tool
