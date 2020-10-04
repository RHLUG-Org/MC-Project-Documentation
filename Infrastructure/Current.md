# Server Specs
|Part Type       |Part Name                |Price   |Actual Price    |Link/Notes                                                                                                                         |
|----------------|-------------------------|--------|----------------|-----------------------------------------------------------------------------------------------------------------------------------|
|Processor       |Ryzen 9 3900X            |$470.00 |$470.00         |https://www.amazon.com/AMD-Ryzen-3900X-24-Thread-Processor/dp/B07SXMZLP9/                                                          |
|Cooler          |Included in case         |Included|Included in case|                                                                                                                                   |
|Motherboard     |X470D4U                  |Included|Included in case|290 separately                                                                                                                     |
|Ram             |CT16G4DFD832A 32GB 2x16GB|$128.00 |$126.54         |On AsRock's QVL list for this motherboard: https://www.amazon.com/Crucial-Single-PC4-25600-Unbuffered-288-Pin/dp/B07Q4FX2D5        |
|PSU             |Case PSU                 |Included|Included in case|400W                                                                                                                               |
|Drive           |Sabrent Rocket Q 1TB     |$120.00 |$119.98         |https://www.amazon.com/Sabrent-Rocket-Internal-Performance-SB-RKTQ-1TB/dp/B07ZZYWTBP                                               |
|Case            |AsRock Rack 1U4LW-X470   |$691.00 |$686.99         |https://www.newegg.com/asrock-1u4lw-x470-amd-am4-socket-ryzen-series-cpus-and-ryzen-7nm-cpus/p/N82E16816775005                     |
|Shipping Costs  |                         |$17.62  |$4.99           |(for the case on Newegg only)                                                                                                      |
|Tax             |7%                       |$98.63  |$65.36          |Can be avoided if tax-exempt status can be obtained                                                                                |
|                |                         |        |                |                                                                                                                                   |
|Total           |                        |$1,525.25|$1,468.90       |                                                                                                                                   |
|                |                         |        |                |                                                                                                                                   |
|LUG Contribution|$500.00                  |        |                |                                                                                                                                   |
|Requested Funds |$1,025.25                |        |                |                                                                                                                                   |
|Actual Funds    |$1,525.00                |        |                |                                                                                                                                   |

# Hardware Setup
The server runs VMWare ESXi (bare-metal hypervisor).

One of the VMs for Minecraft has Ubuntu 18.04 LTS installed on it (with Linux kernel 4.15).

That Ubuntu VM has Nginx installed with the Pterodactyl web server for Minecraft management.

A visual of the "layers" of the layout:
* Outer Layer: Hardware
* Inner Layer (OS): VMWare ESXi
* Inner Layer (Web Server): Pterodactyl
* Inner Layer (Pterodactyl "Node"): Pterodactyl defines a "node" to be a group of resources that can be allocated to "servers" at any time.
* Inner Layer (Minecraft "Servers"): Individual Docker containers

# Pterodactyl Setup
We use MariaDB (MySQL according to the setup script, but still functions the same), Redis for caching, and the built in PHP mail function (as we don't care about getting emails from the panel).

5 servers on one node.

Each server is for:

* Bungeecord
* Lobby world
* PvP world
* PvE world
* Creative world

Each runs on one CPU core with a high clock speed for no lag between servers. 

Each is given a different amount of disk space for worlds depending on usage. As they grow, we will increase the disk space for each one.

For this reason, our servers allow for 5% memory over-allocation and 20% disk over-allocation (in case one of them uses up a lot).

We use the [PterodactylAutoStart](https://github.com/Alteiria/pterodactylAutoStart) script to auto-start servers once the actual VM reboots. This uses the Pterodactyl **Account** API.
