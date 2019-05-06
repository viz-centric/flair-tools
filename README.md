# Flair Tools

Tools needed for simulating flair application

## Steps to follow

`Optional`: Start the reverse proxy by running the below command. This step is required
if SSL gRPC connection is required between services.

```sh
docker-compose -f traefik.yml pull
docker-compose -f traefik.yml up -d
```

`Mandatory`: Start the flair application by running the following command

```sh
docker-compose -f flair-app.yml pull
docker-compose -f flair-app.yml up -d
```

Wait approximately 5 minutes before all containers start.

> **Note**: The `latest` tag is pulled down for each docker image

## Cleaning up the environment

Run the following commands
```sh
docker-compose -f flair-app.yml down
docker-compose -f traefik.yml down
```

## Deleting old images

For fetching the latest docker images please fo the following

```sh
docker rmi <image you want to delete>
```

## Access

If the application is started with the reverse proxy, app will be available at: [https://localhost/flairbi/#/](https://localhost/flairbi/#/), if not at [http://localhost:8002/#/](http://localhost:8002/#/)

```yaml
Credentials:
    Username: flairadmin
    Password: admin
```

> **Note**: 
> If the application dosent seem to show up, please check if the docker containers are working as expected. If any of them are down, please raise an ISSUE in github and we will fix it for you as always :smile:
> You can also contact us at admin@vizcentric.com

## Enable SSL 

It is possible to enable SSL connection between services that use gRPC, such as bi - engine - cache. In order
to do so, please enable `GRPC_SSL_ENABLED` properties to `true` in `flair-app.yml`.