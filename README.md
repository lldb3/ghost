## Ghost Quick Config

This repo is a simple example of how to quickly deploy the Ghost Blogging Webapp

The configuration includes enough to get certificate and deploy multiple instances of ghost. It starts with only two, but you can extend this and add as many as you want.


### How to use

Use the template `.env.example` file as a template. Change the hostnames, email, docker PGID, etc.

Get a token for your domain from cloudflare, and also change the `cloudflare.ini` file.

Finally, make sure to change the variables to match your in the `config/nginx/default` file (use the .example template).

#### Sub domain v.s different domains

When using multiple domains you have two choices:

1. Use a distinct secondary domain, i.e: `one.com`, `two.com`
2. Use a subdomain from yours, i.e: `one.com` and `two.one.com`

In the first case, you may want your main domain `myblog.com` to have the main ghost instance, and host something else at `myotherblog.com`. 
In this scenario, use the `EXTRA_DOMAINS` option in the swag container, specifying your secondary domain.

In the second case, you may want everything under the same domain name. This scenario is favorable if you are considering using more than one subdomain, because you can either use the `SUBDOMAINS` option with your subdomain name, or better, directly generate a wilcard certificate: `*.myblog.com`. Which will work with an infinite number of domains under `myblog.com`.
To achieve this, use the `SUBDOMAINS=wildcard` option, it's that simple.

### Ghost Documentation

If ever in doubt, some useful links: 
- https://ghost.org/docs/hosting/
- https://hub.docker.com/_/ghost/ 

### Checking SSL Rating

Run a cli scan to get your SSLabs grade:
```bash
docker run --rm -ti  drwetter/testssl.sh CLI-OPTIONS
```