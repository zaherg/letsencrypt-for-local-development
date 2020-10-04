# Docker Compose + Traefik TLS Proxy + Let's encrypt Wildcard Cert

This is an example of a solution I've used in various forms for months for local development. It's easy, flexable, and gives a near magical solution for always running HTTP apps through docker-compose with valid TLS, all on a single port with host-header SNI routing via Traefik proxy.

## Why would you want this?

- You want to use TLS locally in HTTP development
- You would like a single proxy app to all of your containers (microservices, etc.) on `80/443`
- You'd like to use domain names for all your compose services, like https://api.domain.dev without touching `/etc/hosts`
- You'd like a trusted certificate in your browsers for local dev and test of any app hostname (api, www, blog, etc.)
- You'd like this to all happen consistanly across all your dev projects


Inspired by Bret Fisher [project][]

## Requirements

1. Docker
2. Docker Compose
3. Domain Name
4. Digital Ocean account [referral link][]

## Overall Steps to Implement

1. Decide which [DNS provider][] you want to use, for me I use [Digital Ocean][]
2. Add two DNS records to your domain name DNS record, which points to your computer IP, like : `*.domain.dev 192.168.1.10 / domain.dev 192.168.1.10`.
3. Create a new environment file called `.env` which should be a copy from `.env.example` and update the values based on your project.

If you want to run the example, make sure to have an environment file called `.env.minio` which should be a copy from `.env.minio.example`

The main services are the socket and the proxy, one to protect your docker socket and the second is for [traefik][].

## Note

This is not a template, this is an example that you can study and implement.




[referral link]: https://m.do.co/c/d913cc215aeb
[Digital Ocean]: https://m.do.co/c/d913cc215aeb
[DNS provider]: https://doc.traefik.io/traefik/https/acme/#providers
[project]: https://github.com/BretFisher/compose-dev-tls
[traefik]: https://docs.traefik.io