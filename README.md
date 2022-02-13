## Ghost Quick Config

This repo is a simple example of how to quickly deploy the Ghost Blogging Webapp

The configuration includes enough to get certificate and deploy multiple instances of ghost. It starts with only two, but you can extend this and add as many as you want.


### How to use

Use the template `.env.example` file as a template. Change the hostnames, email, docker PGID, etc.

Get a token for your domain from cloudflare, and also change the `cloudflare.ini` file.

Finally, make sure to change the variables to match your in the `config/nginx/default` file (use the .example template).
### Ghost Documentation

If ever in doubt, some useful links: 
- https://ghost.org/docs/hosting/
- https://hub.docker.com/_/ghost/ 


### Checking SSL Rating

Run a cli scan to get your SSLabs grade:
```bash
docker run jumanjiman/ssllabs-scan:latest cyb3r.dev
```