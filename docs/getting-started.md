# Getting Started

If you want to get Vork running quickly, you are in the right place.

This guide walks you through your first Docker run, the setup wizard, and your first login.

## Before you begin

You only need two things:

- Docker installed on your computer.
- A web browser.

## Step 1: Start Vork in Docker

Open a terminal and run:

```bash
docker run -d \
  --name vork-server \
  --restart unless-stopped \
  -p 8080:8080 \
  -p 8443:8443 \
  -v vork_conf:/app/conf.d \
  justvork/vork-server:latest
```

This downloads and starts Vork.

Vork uses **Nitrite** for first startup (a built-in local data store), so you can start right away without setting up a separate database first.

## Step 2: Open Vork in your browser

Go to:

- https://localhost:8443

On first visit, your browser will warn you about a security certificate.

That is expected for local first-time setup. Continue to the site.

## Step 3: Complete the setup wizard

When Vork opens for the first time, it guides you through setup.

Follow the prompts to:

1. Create your admin account.
2. Choose your database option.
3. Set up optional notification providers (you can skip and return later).

Take your time here. You can keep it simple and use defaults if you are just exploring.

## Step 4: First login

After setup is complete, sign in with the admin account you just created.

You will then land in the main Vork interface and can start exploring.

## What to do next

A few good first steps:

- Open the chat interface and try your first prompt.
- Explore the admin area.
- Read the [Docker Instructions](docker-instructions.md) to learn more about running Vork with Docker and choosing a database.

## Need help?

If something does not look right:

- Make sure Docker is running.
- Re-run the `docker run` command above.
- Check that port `8443` is free on your machine.
