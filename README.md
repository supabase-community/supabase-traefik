# Supabase Docker with Traefik

Note: this setup is unofficial. It is supported by the Supabase community only.

This guide is covering a self-hosted Supabase setup with [Traefik](https://github.com/traefik/traefik) as a reverse proxy.

Please make sure you read the [self-hosting guide](https://supabase.io/docs/guides/self-hosting#running-supabase).

## Setup Instructions

### Cloning the Repository

First, clone this repository:

```bash
git clone --depth 1 https://github.com/supabase-community/supabase-traefik
```

Navigate to the repository folder:
```bash
cd supabase-traefik
```

### Setting Up Supabase

Get the Supabase code by cloning the Supabase repository:

```bash
git clone --depth 1 https://github.com/supabase/supabase
```

Navigate to the Docker folder:

```bash
cd supabase/docker
```

Copy the example environment variables:

```bash
cp .env.example .env
```

In the `docker-compose.yml` file, add the following to each service:

```yaml
networks:
  - supabase
```

Change the network name to match the one used by Traefik if necessary.

### Setting Up Traefik

If you haven't set up Traefik before, navigate to the Traefik directory:

```bash
cd traefik
```

Copy the example environment variables:

```bash
cp .env.example .env
```

Replace the value inside the `CF_DNS_API_TOKEN` variable. Then, edit the `traefik.yml` and `fileConfig.yml` files, replacing `domain.com`, `IPv4`, and `cloudflareEmail@gmail.com` with the appropriate values.

## Running the Setup

After configuring all the files, you can start the services using Docker Compose:

```bash
docker-compose up -d
```