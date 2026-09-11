# Docker Instructions

This guide helps you run Vork with Docker. If you have already followed the [Getting Started](getting-started.md) steps, you are already using Docker. This page goes a little deeper and explains your choices.

## What is Docker?

Docker is a tool that packages an app so it runs the same way on any computer. You do not need to install Java, databases, or other software by hand. Docker handles it for you.

If Docker is new to you, do not worry. The commands below are copy-and-paste friendly.

## The fastest way to try Vork

This single command downloads and starts Vork on your computer:

```bash
docker run -d \
  --name vork-server \
  --restart unless-stopped \
  -p 8080:8080 \
  -p 8443:8443 \
  -v vork_conf:/app/conf.d \
  justvork/vork-server:latest
```

After a few moments, open your browser and go to:

```
https://localhost:8443
```

Your browser may show a security warning the first time. That is normal for a local setup. You can safely continue.

### What the command does

- `docker run` starts a new container.
- `-d` runs it in the background.
- `--name vork-server` gives it a friendly name.
- `--restart unless-stopped` makes Docker start it again if the app exits.
- `-p 8080:8080` and `-p 8443:8443` let you reach Vork from your browser.
- `-v vork_conf:/app/conf.d` saves your settings so they survive restarts.
- `justvork/vork-server:latest` is the official Vork image.

## Stop and start Vork

To stop Vork:

```bash
docker stop vork-server
```

To start it again:

```bash
docker start vork-server
```

To remove the container completely:

```bash
docker rm vork-server
```

Removing the container does not delete your settings because they live in the `vork_conf` volume.

## Why you might want Docker Compose

A single `docker run` command is great for trying Vork. For day-to-day use, many people prefer Docker Compose. Compose lets you describe your whole setup in one file and start everything with one command.

The main reason to use Compose is to add an external database. Vork supports four storage options:

- **Nitrite** — built in, no extra container needed. This is the default.
- **MongoDB** — a popular database that works well for shared or production setups.
- **Redis** — a fast, lightweight database often used for caching and key-value storage.
- **Couchbase** — a distributed database designed for scaling across many servers.

Each option has its own guide in the next section.

## Choose your database

Pick the guide that matches your needs:

- [Nitrite (built-in)](databases/nitrite.md) — easiest option, no extra setup.
- [MongoDB](databases/mongodb.md) — good for running MongoDB in Docker on your own machine.
- [MongoDB Atlas](databases/mongodb-atlas.md) — good if you prefer MongoDB's managed cloud service.
- [Redis](databases/redis.md) — good if you already use Redis or want a simple external store.
- [Couchbase](databases/couchbase.md) — good for distributed or enterprise setups.

## Updating Vork

To get the latest version, pull the newest image and recreate your container:

```bash
docker pull justvork/vork-server:latest
docker stop vork-server
docker rm vork-server
docker run -d \
  --name vork-server \
  --restart unless-stopped \
  -p 8080:8080 \
  -p 8443:8443 \
  -v vork_conf:/app/conf.d \
  justvork/vork-server:latest
```

Your settings stay safe in the `vork_conf` volume.

## Need help?

If Vork does not start:

- Make sure Docker is running.
- Check that ports `8080` and `8443` are not already in use by another app.
- Run `docker logs vork-server` to see what the container is reporting.
