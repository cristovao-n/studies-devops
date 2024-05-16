# Docker

## Dockerfile

### dev.Dockerfile:

Preparing Phase:

-   npm install
-   npx prisma generate

Execution Phase:

-   npm run dev

### prod.Dockerfile:

Preparing Phase:

-   npm install
-   npx prisma generate

Execution Phase:

-   npm run build
-   npm start

## Image

Pulling an image: IMAGE_NAME:TAG
By default it'll pull images from DockerHub, but this behavior is customizable.

Alpine images are extremely lightweight and are great for the container execution
Standard images are suitable as an entry point for the build of the image

Docker images are stored in `/var/lib/docker/overlay2`

See downloaded images on your machine  
`docker images`

Build an image according to a Dockerfile in current directory  
`docker build -t image-name:tag .`  

Build an image according to a `*.Dockerfile`  
`docker build -t image-name:tag -f *.Dockerfile .`  

> OBS: https://stackoverflow.com/questions/30179716/what-are-none-repository-and-tags-why-do-they-appear-when-i-use-docker-build
> It's a good practice to always build an image with a new tag, to avoid <none> issues

## Container

Run a container from an image  
`docker run -p 3000:3000 image-name:tag`

Run a container in detached mode  
`docker run -p 3000:3000 -d image-name:tag`

Run a container from an image overriding the CMD command  
`docker run -p 3000:3000 -it image-name:tag sh`  

List running containers
`docker ps`  

List exited containers  
`docker ps -a`  

Get container logs  
`docker logs CONTAINER_ID`  
