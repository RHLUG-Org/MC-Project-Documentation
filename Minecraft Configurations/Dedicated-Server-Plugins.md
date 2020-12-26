# On Bungeecord server only
Bungeecord, RedirectPlus BungeeCord plugin (for /server command), FabricProxy (for going to the PvP server)

# On Lobby server only
Multiverse-Core for disabling hunger (who wants to starve while browsing for a server, right?)

# On Lobby, PvE, Creative servers
LuckPerms, SimplePortals, Essentials, FastAsyncWorldEdit

# On PvE/Creative servers
[EasyBed](https://github.com/pengooin/EasyBed/)

# On PvP server only
We use the Fabric Server and Fabric API for loading mods on PvP.

Player Roles for Fabric (permissions, [allows permission level 2 in the Fabric API to be set for "admins" to allow the Flan plugin to work](https://fabricmc.net/wiki/tutorial:commands#some_example_commands_examples)), Flan (land claims, used bedrock and spawner for claim and info to prevent players in PvP from claiming their own land), Phosphor/Lithium (server-side performance), [Fabric-Language-Kotlin](https://www.curseforge.com/minecraft/mc-mods/fabric-language-kotlin/download/3136960) (required for Gunpowder), Gunpowder, GunpowderTeleport (for /home, /warp spawn, and /tpa), GunpowderSleepVote (to match EasyBed)

Temporary plugins for server maintenance (they'll only be installed when maintenance is going on to avoid permissions conflicts): WorldEdit

This list helped us immensely: https://gist.github.com/comp500/12417ee3685f6204362e933c9bcde603

# LuckPerms configuration
This uses a MariaDB database with the 'global' configuration, where the Bungeecord server maintains the 'master list of permissions' to be sent to all servers.

We use per-server permissions with LuckPerms using `include-global: true` while setting the individual server names.
