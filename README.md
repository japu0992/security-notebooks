# security-notebooks
Getting this a docker python data science environment running 

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/japu0992/security-notebooks/main)


# Using this repo: 

The built image is [hosted on Docker-Hub](https://hub.docker.com/repository/docker/japu0992/my-data-science-notebooks).

## Using this repo
### With `docker`
Build:

```bash
docker build --rm -t jupyter/my-datascience-notebook .
# this line builds the image 
```

Run:

```bash
docker run --rm -it -p 10000:8888 -v "${PWD}:/home/jovyan/work" jupyter/datascience-notebook:b418b67c225b
# - Should publish port 10000
# - Should mount the local directory as a volume in the
#   container's home directory
# - Should `--rm` container when done
# - Should use `-it` mode
```

### With `docker-compose`
Build and run:

```bash
docker-compose up
version: "3.9"  # the docker-compose.yml specification version that this file uses
services:
  jupyter: # arbitrary key/name for the container
    build: . # look in the local directory for the Dockerfile
    image: japu0992/my-datascience-notebook # `push` to this repository (defaults to DockerHub)
    ports:
      - "10000:8888" # publish container port 10000 to host port 8888
    volumes:
      - .:/home/jovyan/work # Mount the local directory to container-directory `/home/jovyan/work`
                            # (The jupyter-docker-stacks docs tell us to mount it here)

```




