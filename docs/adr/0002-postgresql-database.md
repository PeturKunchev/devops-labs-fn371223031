# 0002. Use PostgreSQL for persistent note storage

**Status:** Accepted

## Context

The application needs persistent storage for notes. In-memory storage loses data when the application restarts, so a database is needed.

## Decision

Use PostgreSQL as the application's database. Run PostgreSQL as a Docker Compose service using the `postgres:17-alpine` image. The application connects to the database through the `DATABASE_URL` environment variable, using the Compose service name `db`. A named volume stores the database files persistently.

## Consequences

Notes persist across application and container restarts as long as the named volume is preserved. The application depends on PostgreSQL being healthy before it starts. Database credentials are stored in `.env`, which is excluded from Git, while `.env.example` documents the required variables.
