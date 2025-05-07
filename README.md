# Docker

# How to build the image
1. Login on your pc to the Docker account via Docker Desktop application. Credentials you can find in the Keeper under "DockerHub" record.
2. Go to the directory where the Dockerfile is located
2. Run the following command:
```bash
docker build --platform=linux/amd64 -t <local_image_name> /Path/to/Dockerfile
docker tag <local_image_name> <target_image_name>:<tag>
docker push <target_image_name>:<tag>
```
For example:
```bash
docker build --platform=linux/amd64 -t portadev/pimcore-web Pimweb/php:8-4
docker tag portadev/pimcore-web portadev/pimcore-web:8.4
docker push portadev/pimcore-web:8.4
```
3. The image should be built and pushed to the target repository: https://hub.docker.com/r/portadev/pimcore-web
