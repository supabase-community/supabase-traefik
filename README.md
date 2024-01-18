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

### Setting Up Traefik

If you haven't set up Traefik before, navigate to the Traefik directory:

```bash
cd traefik
```

Copy the example environment variables:

```bash
cp .env.example .env
```

In the `.env`, replace all the variable values to your own.


After configuring all the files, you can start Traefik using Docker Compose:

```bash
docker-compose up -d
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

After configuring all the files, you can start the Supabase services using Docker Compose:

```bash
docker-compose up -d
```