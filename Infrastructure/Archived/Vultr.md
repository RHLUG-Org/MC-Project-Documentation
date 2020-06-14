# Vultr Hosting
The MC server was hosted on many individual virtual computers (called "nodes" here) on Vultr using the below infrastructure from April 9, 2020 to May 9, 2020.

Estimated cost was around $50-100/month, depending on how many users are using it at one time.

We used up the 1 month of free trial credits.

## Server Diagram
The servers were structured like this:

![Vultr infrastructure](https://raw.githubusercontent.com/RHLUG-Org/MC-Project-Documentation-and-Scripts/master/Infrastructure/Archived/Vultr%20infrastructure.png)

(You can also download the .drawio file)

A node is a physical machine, while a "service" is something like a web server or a Minecraft server hosted on a particular port.

(i.e. a "service" would be something that users or developers would use on the Web that's not just visible "on the server",
meaning an outward/user-facing service.)

## Server Hardware
### Panel Node

We anticipated that this one generally has a lot of traffic going to it (people using web panel + Bungeecord routing), so it has dedicated hardware (not virtualized).

#### Specs

Vultr High Frequency

128 GB SSD (this one is an NVMe SSD)

2 CPU cores

4 GB memory

3 TB bandwidth limit/month

Price: $24/mo

Dedicated IP price: additional $2/mo ($0.003/hr) (you can find this on Vultr's web panel)

Has 2 Dedicated IPs (we purchased 1 of them and 1 of them came with the node)

### Overworld

Overworld was a temporary name, it is like the overworld in Minecraft. It would have hosted the creative and survival servers.

We anticipated that this one has the most traffic going to it, so it has dedicated hardware (not virtualized).

#### Specs

Vultr High Frequency

256 GB SSD (this one is an NVMe SSD)

3 CPU cores

8 GB memory

4 TB bandwidth limit/month

Price: $48/mo

### Lobby

Wouldn't be used often but expected a bit of foot traffic at the beginning so we cheaped out on this one.

#### Specs

Vultr Compute (Skylake had "up to 50%" (according to Vultr) performance increase so we upgraded to the $10 one instead of the $5 one)

55 GB SSD (this one is an NVMe SSD)

1 CPU core

2 GB memory

2 TB bandwidth limit/month

Price: $10/mo
