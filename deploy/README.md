# Vaultwarden deployment

This folder contains a minimal production-oriented Docker Compose setup for the user's Vaultwarden fork.

## What it does

- Runs the official `vaultwarden/server:latest` container.
- Persists all Vaultwarden data in `./vw-data`.
- Binds Vaultwarden only to `127.0.0.1:8000` by default.
- Keeps the public URL, admin token, and signup setting outside Git in a local `.env` file.
- Is intended to sit behind an HTTPS reverse proxy.

## First run

1. Copy `.env.example` to `.env`.
2. Replace `DOMAIN` with the final HTTPS address.
3. Generate a long random `ADMIN_TOKEN`.
4. Start the service with Docker Compose.
5. Put an HTTPS reverse proxy in front of port 8000.
6. Create the first account.
7. Change `SIGNUPS_ALLOWED=false` and restart the container.

## Important

Do not commit the real `.env` file or the `vw-data` directory. The upstream repository already ignores `.env` and `data`; this deployment keeps its persistent data inside this deployment folder, so keep the deployment folder private on the server and back up `vw-data` regularly.

Vaultwarden's web vault requires HTTPS for normal browser use.
