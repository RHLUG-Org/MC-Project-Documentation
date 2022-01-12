This can be used as a reference to understand how we update Minecraft and Pterodactyl versions,
so that you can do the same on your Pterodactyl server in less time.

# What we do when updating

- We currently download the latest Minecraft Paper (or Bungeecord) `server.jar` and upload it manually to each Docker container's volume on each version update.
- This is due to the way that Pterodactyl's "egg" system works, which is separate from Docker images.
    - Unfortunately (afaik), rebuilding the Pterodactyl "egg" means rebuilding the entire container (including the volume), meaning the data is destroyed without a backup. This is sort of a pterodactyl thing.
    - There may be a way to do this automatically by [customizing a few variables in the egg](https://pterodactyl.io/community/config/eggs/creating_a_custom_egg.html#egg-variables) and and [restarting the container (called "Server" in the Pterodactyl web interface)](https://github.com/pterodactyl/panel/issues/1637#issuecomment-510989515)
         - [NOTE: DO NOT USE `latest` as a value for any variable -- best practice #6 in the link here](https://developers.redhat.com/blog/2016/02/24/10-things-to-avoid-in-docker-containers)
- The host php composer, php versions, php plugins, pterodactyl panel version, etc. do have to be updated manually unless pterodactyl is run in something like a docker image (which we don't do right now)
