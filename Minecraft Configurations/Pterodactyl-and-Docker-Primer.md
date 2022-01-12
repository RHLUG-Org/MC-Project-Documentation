This can be used as a reference to understand how our server works when fixing a problem or updating Minecraft servers,
so that you can do the same on your Pterodactyl server in less time.

Specifically, we detail how Pterodactyl and Docker work together
to make it easier to manage and upgrade Java versions on multiple Minecraft servers.

# Docker image information
- Docker images are a base operating system (and all of its data) ready to run (think, Ubuntu running with Java 17). They are immutable (read only).
    - This provides some security/consistency as the same OS, same Java version, same other software is installed. If you update the image, you update Ubuntu, Java, etc.
    - So, using Docker means less things to maintain (less playing with config when installing stuff or doing sudo apt updates/upgrades on Linux). Instead, change the Docker image you use and reboot to update. (Think, 1 vs 100 things to do)
- **IMPORTANT**: Changing the "base docker image" in Pterodactyl will not overwrite the existing data, which is stored on a volume or container
- It's best practice to not install extra software or update software in the **writable partition of docker containers**. Install software in images instead.
    - **IMPORTANT**: do not confuse "writable partition of docker containers" with a docker "container", which contains the writable portion, 1 or more volumes, and 1 or more docker images.
    - You can find a different image or customize the Dockerfile to install more software in a docker image

# Anything specific to Pterodactyl's setup and not Docker's setup
- Pterodactyl has it set up such that volumes are where the Minecraft data is stored (in `/srv/daemon-data/<container uid>` or whatever)
    - Docker volumes are basically "mounts" to somewhere in the host Linux filesystem. Think of them like having a link to a USB thumb drive in a certain directory.
- From https://stackoverflow.com/a/26833005 (the answer confuses the "container" terminology a bit, but this info is right):
> You can store data either on host (in directory mounted as volume) or in special data-only container(s).

# See also
## Introduction to the Docker system
Intro to docker images/how to build a docker image: https://jfrog.com/knowledge-base/a-beginners-guide-to-understanding-and-building-docker-images/

Docker best practices: https://developers.redhat.com/blog/2016/02/24/10-things-to-avoid-in-docker-containers

Why use **Docker images** for updating Java versions?: https://medium.com/sroze/why-i-think-we-should-all-use-immutable-docker-images-9f4fdcb5212f

## Further/advanced reading
Custom pterodactyl dockerfiles (WARNING INCOMPLETE, reference only): https://pterodactyl.io/community/config/eggs/creating_a_custom_image.html

Why are volumes better than containers for storing data?: https://docs.docker.com/develop/dev-best-practices/#where-and-how-to-persist-application-data

It's better to not install software in a running container and use `docker commit` to put the software in a new image (I made this mistake once with the wiki server): https://stackoverflow.com/a/51763737

It's faster to keep images small (i.e. separate containers is better if you want, say, pterodactyl and a LUG web server in a docker container): https://docs.docker.com/develop/dev-best-practices/#how-to-keep-your-images-small
