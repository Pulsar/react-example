# Notes

## Create containers with compose

**To do it with docker you do the following:**

- Create the image

```bash
docker build -t react-example .
```

- Build the container

```bash
docker run -it -v ${PWD}:/usr/src/app -v /usr/src/app/node_modules/ -p 300de_modules/ -p 3000:3000 --rm react-example
```

The same thing can be done with docker-compose

```yml
version: '3.7'

services:

  react-app:
    container_name: app-react
    build:
      context: .
      dockerfile: Dockerfile
    volumes:
      - '.:/usr/src/app'
      - '/usr/src/app/node_modules'
    ports:
      - '3000:3000'
    enviroment:
      - NODE_ENV=development
```

## Mount folders

```bash
docker run -d --mount type=bind,source=/home/user/Git-Repos/example/src,target=/var/data nginx
```

Check mount

```bash
docker exec <container-id> ls -ls /var/data
```