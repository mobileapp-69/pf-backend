# Preflight Backend

## Database Setup

- `pnpm install`
- Create `.env` from `.env.example`
- DB container
  - `pnpm run eol` to set the correct line endings (Windows)
  - `chmod +x ./scripts/*.sh` to make scripts executable (Linux/Mac)
  - `docker compose --env-file ./.env -f docker-compose-db.yml up -d` to start the database

## Drizzle Setup

- `pnpm run db:push`
- `pnpm run db:generate`
- `pnpm run db:migrate`
- `pnpm run db:prototype`

# Setup Express.js Backend

- Make sure that you already have DB running
- `pnpm install`
- `pnpm run dev`

# Cloudflare Tunnel

- Fill in the `.env` file with your Cloudflare Tunnel credentials
- `docker compose --env-file ./.env -f docker-compose-tunnel.yml up -d`
- `docker compose --env-file ./.env -f docker-compose-tunnel.yml down`

# Containerization (Express.js appplication) and test

- Make `.env.test` from `.env.test.example`
- `docker compose --env-file ./.env.test -f docker-compose-backend.yml up -d --force-recreate --build`

# Push to dockerhub

- `docker tag preflight-backend [DOCKERHUB_ACCOUNT]/preflight-backend:latest`
- `docker push [DOCKERHUB_ACCOUNT]/preflight-backend:latest`
