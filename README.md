# IdentityServer 4 as Docker container

For testing purpose only

Prebuilt image is pushed to `hpcsc/identity-server:0.0.1`

## Run

```
docker run -p 80:80 hpcsc/identity-server:0.0.1
```

This image by default loads config files at `/app/config` folder
Default config files define:

- 2 clients: `full-access-client` and `read-only-client`, with the same secret: `secret`
- 1 api resource `api` with 2 scopes `api.full_access` and `api.read_only`

## To request a token

`POST` to `/connect/token` with following information:
- Basic authentication
    - Username: `full-access-client` or `read-only-client`
    - Password: `secret`
- Body form data (`x-www-form-urlencoded`)
    - `grant_type`: `client_credentials`
    - `scope`: `api.full_access` or `api.read_only`