# Docker-Nagios

Docker image for Nagios

Nagios Core 4.4.6 running on Debian Buster slim image with NRPE

### Configurations
Nagios Configuration lives in /opt/nagios/etc
NagiosGraph configuration lives in /opt/nagiosgraph/etc

### Install

```sh
docker pull fikolis/nagios:latest
```

### Running

Run with the example configuration with the following:

```sh
docker run --name nagios4 -p 0.0.0.0:8080:80 fikolis/nagios:latest
```

alternatively you can use external Nagios configuration & log data with the following:

```sh
docker run --name nagios4  \
  -v /path-to-nagios/etc/:/opt/nagios/etc/ \
  -v /path-to-nagios/var:/opt/nagios/var/ \
  -v /path-to-custom-plugins:/opt/Custom-Nagios-Plugins \
  -v /path-to-nagiosgraph-var:/opt/nagiosgraph/var \
  -v /path-to-nagiosgraph-etc:/opt/nagiosgraph/etc \
  -p 0.0.0.0:8080:80 fikolis/nagios:latest
```

There are a number of environment variables that you can use to adjust the behaviour of the container:

| Environamne Variable | Description |
|--------|--------|
| MAIL_RELAY_HOST | Set Postfix relayhost |
| MAIL_INET_PROTOCOLS | set the inet_protocols in postfix |
| NAGIOS_FQDN | set the server Fully Qualified Domain Name in postfix |
| NAGIOS_TIMEZONE | set the timezone of the server |

For best results your Nagios image should have access to both IPv4 & IPv6 networks 

#### Credentials

The default credentials for the web interface is `nagiosadmin` / `nagios`




