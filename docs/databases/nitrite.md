# Using Vork with Nitrite

This guide explains Vork's built-in storage option, called Nitrite. It is the easiest way to run Vork because everything happens inside the container. You do not need a separate database.

## When Nitrite is a good fit

- You are trying Vork for the first time.
- You are running Vork on one computer.
- You want the simplest possible setup.

## How it works

Nitrite stores your data in files inside the container. To make sure your data is not lost when the container restarts, Vork saves those files to a Docker volume called `vork_conf`.

You do not need to configure anything special. Nitrite is already the default.

## Start Vork with Nitrite

Use the same command from the [Docker Instructions](../docker-instructions.md) page:

```bash
docker run -d \
  --name vork-server \
  -p 8080:8080 \
  -p 8443:8443 \
  -v vork_conf:/app/conf.d \
  justvork/vork-server:latest
```

When you open `https://localhost:8443` and run the setup wizard, Nitrite is already selected.

## What happens during setup

1. Create your admin account.
2. On the database step, leave Nitrite selected.
3. Finish the remaining steps.

That is it. Vork is ready to use.

## Choosing another database

Choose your database during setup. If you want MongoDB, Redis, or Couchbase, start with that option in the setup wizard and use the matching guide in this docs section.

## A note about backups

Because Nitrite stores data inside the container's volume, your files are safe as long as the `vork_conf` volume exists. If you want a backup, copy the volume contents to another location using standard Docker backup tools.
