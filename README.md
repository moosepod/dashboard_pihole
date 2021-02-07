# dashboard_pihole

This repo contains the config for the Raspberry Pi i have running:

- pi-hole
- moosedash
- ferrif

Set so I have two subdomains pointing to the Raspberry Pi:
- dashboard.thechristensens.org
- ferrif.thechristensens.org

## Initial setup
- A Raspberry Pi 4 running Pi-Hole on Raspbian

### Reconfigure to use haproxy

The lighttpd installed with the pi-hole set to run on 8888

(as root or sudo)
- Edit /etc/lighttpd/lighttpd.conf
- Set server.port to 8888
- service lighttpd restart

### Installed haproxy

- apt-get -y install haproxy
- Configured such that
- dashboard.thechristensens.org and ferrif.thechristensens.org are acls
- default goes to 8000 (moosedash)
- anything under ferrif goes to 8088 (ferrif)
- dashboard + /admin/ goes to 8888 (pihole)
