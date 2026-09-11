# Using Vork with MongoDB Atlas

This guide helps you connect Vork to MongoDB Atlas. Atlas is MongoDB's managed database service, which means MongoDB runs on MongoDB's servers instead of on your own computer.

## When Atlas is a good fit

- You do not want to run and maintain your own MongoDB server.
- You need your data available from anywhere.
- You want automatic backups and scaling handled by MongoDB.

## What you need

- A MongoDB Atlas account. You can create one for free at [mongodb.com/atlas](https://www.mongodb.com/atlas).
- A database user and a cluster ready to use.
- Your Atlas connection URI.

## Get your connection URI from Atlas

1. Log in to Atlas and open your cluster.
2. Click **Connect**.
3. Choose **Drivers**.
4. Select **Java** (the version does not matter for Vork).
5. Copy the connection string. It looks like this:

```
mongodb+srv://myUser:myPassword@cluster0.xxxxx.mongodb.net/?retryWrites=true&w=majority
```

6. Replace `<password>` with your database user's actual password.
7. Make sure the URI includes your database name before the question mark. For Vork, use `vork`:

```
mongodb+srv://myUser:myPassword@cluster0.xxxxx.mongodb.net/vork?retryWrites=true&w=majority
```

## Start Vork with your Atlas URI

You can pass the URI to Vork using an environment variable. Create a `compose.yaml` file like this:

```yaml
services:
  vork:
    image: justvork/vork-server:latest
    restart: unless-stopped
    ports:
      - "8080:8080"
      - "8443:8443"
    environment:
      DB_BACKEND: mongo
      MONGO_URI: mongodb+srv://myUser:myPassword@cluster0.xxxxx.mongodb.net/vork?retryWrites=true&w=majority
    volumes:
      - vork_conf:/app/conf.d

volumes:
  vork_conf:
```

Replace the URI with your own.
Keep `DB_BACKEND: mongo` so Vork activates the MongoDB backend.

Start Vork:

```bash
docker compose up -d
```

## Configure Vork during setup

When the setup wizard appears:

1. Create your admin account.
2. On the database step, choose MongoDB.
3. Paste your Atlas connection URI into the **MongoDB Connection URI** field.
4. Save and continue.

## Allow Atlas to accept connections from Vork

Atlas only accepts connections from allowed IP addresses.

1. In Atlas, go to **Network Access**.
2. Click **Add IP Address**.
3. Add the public IP address of the computer or server running Vork.
4. For testing, you can choose **Allow Access from Anywhere**, but this is less secure.

If Vork cannot connect, this is the most common cause.

## Security notes

- Your Atlas URI contains your database password. Keep it private.
- Do not save the URI in a public file or version control repository.
- Use a dedicated database user for Vork rather than your Atlas account owner.

## If you already finished setup

Database choice is made during setup. If you want to use Atlas, start a fresh setup flow and choose MongoDB, then enter your Atlas URI.

## Troubleshooting

If Vork cannot connect:

- Double-check the URI and password.
- Make sure Atlas **Network Access** allows your server's IP.
- Check that the database user has read and write permissions.
- Verify the cluster name in the URI matches your Atlas cluster.
