# Using Vork with MongoDB

This guide helps you run Vork with MongoDB. MongoDB is a popular database that works well when you want Vork to share data across multiple machines or when you prefer an external database.

## When MongoDB is a good fit

- You are running Vork in more than one place and want them to share the same data.
- You already have backup and maintenance routines for MongoDB.
- You want Vork's data stored outside the container.
- You want to use a managed MongoDB service such as MongoDB Atlas.

## What you need

- Docker installed.
- A folder for your Compose file.
- A MongoDB connection URI. This is a single string that tells Vork how to reach your database.

## What is a connection URI?

A connection URI is one line that contains everything Vork needs to connect:

```
mongodb://user:password@host:27017/database
```

For MongoDB Atlas, it looks like this:

```
mongodb+srv://user:password@cluster0.xxxxx.mongodb.net/database
```

You can get this string from your MongoDB provider. Atlas shows it on the cluster screen under **Connect**.

## Create a Compose file

In an empty folder, create a file named `compose.yaml` and paste the following:

```yaml
services:
  mongodb:
    image: mongo:8
    restart: unless-stopped
    volumes:
      - mongodb_data:/data/db
    healthcheck:
      test: ["CMD", "mongosh", "--quiet", "--eval", "db.adminCommand('ping').ok"]
      interval: 10s
      timeout: 5s
      retries: 5

  vork:
    image: justvork/vork-server:latest
    restart: unless-stopped
    depends_on:
      mongodb:
        condition: service_healthy
    ports:
      - "8080:8080"
      - "8443:8443"
    environment:
      DB_BACKEND: mongo
      MONGO_URI: mongodb://mongodb:27017/vork
    volumes:
      - vork_conf:/app/conf.d

volumes:
  mongodb_data:
  vork_conf:
```

This file tells Docker to start two services: MongoDB and Vork. Vork waits until MongoDB is ready before it starts.
`DB_BACKEND: mongo` tells Vork to use MongoDB instead of the default Nitrite backend.

## Start everything

Open a terminal in the same folder as your `compose.yaml` file and run:

```bash
docker compose up -d
```

After a minute or two, open:

```
https://localhost:8443
```

## Configure Vork during setup

When the setup wizard appears:

1. Create your admin account.
2. On the database step, choose MongoDB.
3. Paste your connection URI into the **MongoDB Connection URI** field. For the local Compose example above, use:
   ```
   mongodb://mongodb:27017/vork
   ```
   For MongoDB Atlas, paste the URI from your Atlas cluster.
4. Save and continue.

## Using MongoDB Atlas

If you prefer not to run your own MongoDB container, you can point Vork at Atlas:

1. In your Atlas project, go to **Database** → **Connect** → **Drivers**.
2. Copy the URI and replace `<password>` with your database user's password.
3. Make sure the URI ends with `/vork` (or the database name you want to use).
4. Paste the URI into Vork's MongoDB Connection URI field.

Also check Atlas **Network Access** and allow the IP address of the server running Vork.

## If you already finished setup

Database choice is made during setup. If you want to use MongoDB, start a fresh setup flow and choose MongoDB there.

## Stop everything

```bash
docker compose down
```

Your data stays in the Docker volumes `mongodb_data` and `vork_conf`.

## A few helpful notes

- Keep `vork_conf` mounted as a volume so your settings survive container restarts.
- The connection URI contains your password, so protect it like any secret. Do not commit it to public version control.
- If the connection fails, double-check the URI, your database user's permissions, and any network allow lists.
