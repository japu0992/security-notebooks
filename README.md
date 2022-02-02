# security-notebooks
Getting this a docker python data science environment running 
https://mybinder.org/v2/gh/japu0992/security-notebooks/main


# Using this repo: 
to launch a jupyter stack datascience noteboook:

make sure docker containers stopped running

click on security-notebooks in docker desktop

(OR)

set current working directory to "security-notebooks" folder

To build docker
```bash
docker build .....
```
Run

```bash
  docker run --rm -it -p 10000:8888 -v "${PWD}:/home/jovyan/work" jupyter/datascience-notebook:b418b67c225b
  ```

note this runs on port 10000

find link with token and open on chrome

do the same with a `docker-compose.yml` file:

if not opening

```bash
docker stop sleepy_zhukovsky
```

```bash
docker-compose up -d
version: "3.9"  # the docker-compose.yml specification version that this file uses
services:
  jupyter: # arbitrary key/name for the container
    build: . # look in the local directory for the Dockerfile
    image: deargle/my-datascience-notebook # `push` to this repository (defaults to DockerHub)
    ports:
      - "8888:8888" # publish container port 8888 to host port 8888
    volumes:
      - .:/home/jovyan/work # Mount the local directory to container-directory `/home/jovyan/work`
                            # (The jupyter-docker-stacks docs tell us to mount it here)

```
The image is here https://hub.docker.com/repository/docker/japu0992/my-data-science-notebooks

 
