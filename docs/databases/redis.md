# Using Vork with Redis

This guide helps you run Vork with Redis. Redis is a fast, lightweight database often used for caching and simple data storage. It is a good choice if you already use Redis elsewhere or want an external store without much overhead.

## When Redis is a good fit

- You already have Redis running in your environment.
- You want a simple external data store.
- You prefer a database known for speed and low resource use.

## What you need

- Docker installed.
- A folder for your Compose file.

## Create a Compose file

In an empty folder, create a file named `compose.yaml` and paste the following:

```yaml
services:
  redis:
    image: redis:7
    restart: unless-stopped
    command: ["redis-server", "--appendonly", "yes"]
    volumes:
      - redis_data:/data
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 10s
      timeout: 5s
      retries: 5

  vork:
    image: justvork/vork-server:latest
    restart: unless-stopped
    depends_on:
      redis:
        condition: service_healthy
    ports:
      - "8080:8080"
      - "8443:8443"
    environment:
      REDIS_HOST: redis
      REDIS_PORT: 6379
      # Optional: only add this if Redis requires a password
      # REDIS_PASSWORD: your-password
    volumes:
      - vork_conf:/app/conf.d

volumes:
  redis_data:
  vork_conf:
```

This file tells Docker to start Redis and Vork together. Vork waits until Redis is healthy before it starts.

## Start everything

Open a terminal in the same folder as your `compose.yaml` file and run:

```bash
docker compose up -d
```

After a short wait, open:

```
https://localhost:8443
```

## Configure Vork during setup

When the setup wizard appears:

1. Create your admin account.
2. On the database step, choose Redis.
3. Enter these details:
   - **Host:** `redis`
   - **Port:** `6379`
   - **Password:** only if you enabled one above.
4. Save and continue.

## If you already finished setup

Database choice is made during setup. If you want to use Redis, start a fresh setup flow and choose Redis there.

## Stop everything

```bash
docker compose down
```

Your data stays in the Docker volumes `redis_data` and `vork_conf`.

## A few helpful notes

- Keep `vork_conf` mounted as a volume so your settings survive container restarts.
- If you enable Redis authentication, make sure the password matches in both the Compose file and the Vork settings.
