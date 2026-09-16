> [!WARNING]
> **Deprecated — do not add or update images here.**
>
> These images have been consolidated into **[portadesign/docker-library](https://github.com/portadesign/docker-library)**
> under `images/pimcore-php/`. New images are Alpine-based, published as
> `portadev/pimcore-php:<version>`, built multi-arch (`linux/amd64,linux/arm64`)
> via `scripts/build-push.sh`, and ship shared build/deploy helpers.
>
> | Deprecated here | Replacement in `docker-library` |
> |---|---|
> | `portadev/pimcore:8.0` | `portadev/pimcore-php:8.0-alpine` |
> | `portadev/pimcore:8.2` | `portadev/pimcore-php:8.2-alpine` |
> | `portadev/pimcore:8.3` | no direct equivalent — nearest is `8.4-alpine` |
> | `portadev/pimcore:8.5-fpm` | `portadev/pimcore-php:8.5-alpine` |
> | `portadev/pimcore:8.5-rr` | not migrated |
> | `portadev/pimcore-web:8.2`, `:8.4` | not migrated |
>
> **Migration is not drop-in.** The replacements run on musl instead of glibc and
> carry ImageMagick 7, so the policy file moves from `/etc/ImageMagick-6/policy.xml`
> to `/etc/ImageMagick-7/policy.xml`. See
> [`images/pimcore-php/README.md`](https://github.com/portadesign/docker-library/blob/main/images/pimcore-php/README.md)
> for the project `Dockerfile` pattern, the `/mnt/data` volume layout and the
> deploy entrypoint contract.
>
> Existing tags stay on Docker Hub so current deployments keep working. Everything
> below is kept for reference only.

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
```bash
docker build --platform=linux/amd64 -t portadev/pimcore Pimcore/php:8-3
docker tag portadev/pimcore portadev/pimcore:8.3
docker push portadev/pimcore:8.3
```
```bash
docker build --platform=linux/amd64 -t portadev/pimcore "Pimcore/php:8-5-rr"
docker tag portadev/pimcore portadev/pimcore:8.5-rr
docker push portadev/pimcore:8.5-rr
```
```bash
docker build --platform=linux/amd64 -t portadev/pimcore "Pimcore/php:8-5-fpm"
docker tag portadev/pimcore portadev/pimcore:8.5-fpm
docker push portadev/pimcore:8.5-fpm
```
3. The images should be built and pushed to the target repositories:
   - https://hub.docker.com/r/portadev/pimcore-web
   - https://hub.docker.com/r/portadev/pimcore
