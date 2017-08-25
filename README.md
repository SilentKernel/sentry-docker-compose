# sentry-docker-compose

This docker-compose file is an updated version of : (https://gist.github.com/mottosso/e5568a580f92ada192ad2df33ad84d68)

## How to ?
To begin generate your private key with :

```shell
docker run --rm sentry generate-secret-key
```
Then set replace "your-generated-key" with the generated key in the the file

***OPTIONAL (but do it) : You can also change the database password if you want to.***

Create the directory for your postgress data 
```shell
mkdir ./postgresql
```

Replace all variable with yours in the docker-compose.yml file (domain, email parameters ... etc, please note this docker compose file is compatible with *** nginx-proxy and nginx-companion***

Then start basic service with
```shell
docker-compose up -d redis postgres sentry
```

Launch the update of sentry (will create / update the database and ask you for your admin account)
```shell
docker exec -it [SENTRY CONTAINER] sentry upgrade
```
*** [SENTRY CONTAINER] should be sentry_sentry_1 if it's the first instance ***

Finally just launch the all stack :

`¨¨shell
docker-compose up -d
```

You can of course sho your concainer bash with
```shell
docker exec -it --user=root sentry_sentry_1 bash
```
