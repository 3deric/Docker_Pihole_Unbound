# Docker_Pihole_Unbound
Docker compose yml for pihole with unbound. Requires a working docker installation.

## Basic Setup
Create folders for pihole and unbound.
```
mkdir -p pihole/{pihole,dnsmasq.d,unbound}
```
Create a *docker-compose.yml* and copy the content of docker-compose.yml into it.
```
touch docker-compose.yml
nano docker-compose.yml
```
Adjust the file for your needs.
> [!CAUTION]
> Change the password of the pihole interface!

## Unbound Setup

Unbound requires the list of primary root servers. It can be downloaded by executing the following command.
```
curl -o ./pihole/unbound/root.hints https://www.internic.net/domain/named.cache
```
Copy the *unbound.conf* into `./pihole/unbound` and adjust the config for your needs.

## Launch the container

Check if the docker-compose is valid by executing.
```
docker compose config
```
Then start the containers by running.
```
docker compose up -d
```
Check if pihole and unbound work.
```
dig @127.0.0.1 +trace www.example.com
```