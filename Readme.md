# pihole

A pihole setup using docker compose and traefik

## Known Issues:

### bind: address already in use

Error message:
`Error starting userland proxy: listen tcp4 0.0.0.0:53: bind: address already in use`

Fix:
https://github.com/pi-hole/docker-pi-hole#installing-on-ubuntu


Uncomment and change to no in `/etc/systemd/resolved.conf`  (everything is commented out by default): `DNSStubListener=no`


```bash
sudo sed -r -i.orig 's/#?DNSStubListener=yes/DNSStubListener=no/g' /etc/systemd/resolved.conf

sudo sh -c 'rm /etc/resolv.conf && ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf'

sudo systemctl restart systemd-resolved
```
