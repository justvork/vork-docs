# Using Vork with Couchbase

This guide helps you run Vork with Couchbase. Couchbase is a distributed database designed for large or growing setups where data is spread across multiple servers.

## When Couchbase is a good fit

- You already use Couchbase in your organization.
- You expect your data to grow across several servers.
- You want a database built for distribution and clustering.

## What you need

- Docker installed.
- A folder for your Compose file.

## Create a Compose file

In an empty folder, create a file named `compose.yaml` and paste the following:

```yaml
services:
  couchbase:
    image: couchbase:community-7.6.2
    restart: unless-stopped
    ports:
      - "8091:8091"
      - "11210:11210"
    volumes:
      - couchbase_data:/opt/couchbase/var

  vork:
    image: justvork/vork-server:latest
    restart: unless-stopped
    depends_on:
      - couchbase
    ports:
      - "8080:8080"
      - "8443:8443"
    environment:
      COUCHBASE_HOST: couchbase
      COUCHBASE_PORT: 8091
      COUCHBASE_BUCKET: vork
      COUCHBASE_USERNAME: Administrator
      COUCHBASE_PASSWORD: password
    volumes:
      - vork_conf:/app/conf.d

volumes:
  couchbase_data:
  vork_conf:
```

This file starts Couchbase and Vork together. You may want to change the example username and password to something stronger.

## Start everything

Open a terminal in the same folder as your `compose.yaml` file and run:

```bash
docker compose up -d
```

Couchbase may take a little longer to start than the other databases. When it is ready, open:

```
https://localhost:8443
```

You can also open Couchbase's own web console at:

```
http://localhost:8091
```

Use it to finish the initial Couchbase setup if this is the first time you are running it.

## Configure Vork during setup

When the setup wizard appears:

1. Create your admin account.
2. On the database step, choose Couchbase.
3. Enter these details:
   - **Host:** `couchbase`
   - **Port:** `8091`
   - **Bucket:** `vork`
   - **Username:** the Administrator name from your Compose file.
   - **Password:** the matching password from your Compose file.
4. Save and continue.

## If you already finished setup

Database choice is made during setup. If you want to use Couchbase, start a fresh setup flow and choose Couchbase there.

## Stop everything

```bash
docker compose down
```

Your data stays in the Docker volumes `couchbase_data` and `vork_conf`.

## A few helpful notes

- Keep `vork_conf` mounted as a volume so your settings survive container restarts.
- Make sure the Couchbase bucket exists and that the user has permission to read and write data.
- Couchbase's query service must be turned on, because Vork uses it for list and search operations.
