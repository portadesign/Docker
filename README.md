# Docker

# How to build the image
1. Login on your pc to the Docker account via Docker Desktop application. Credentials you can find in the Keeper under "DockerHub" record.
2. Go to the directory where the Dockerfile is located
2. Run the following command:
```bash
docker build --platform=linux/amd64 -t <local_image_name> .
docker tag <local_image_name> <target_image_name>:<tag>
docker push <target_image_name>:<tag>
```
3. The image should be built and pushed to the target repository
