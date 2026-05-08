# Infra

Local infrastructure for the DE playground, managed via Docker Compose.

Each tool has its own subdirectory containing a Compose file and any config it needs. The top-level `compose.yaml` includes them all.

## Tools

- [SeaweedFS](./seaweedfs/README.md) — S3-compatible object storage

## Usage

```bash
docker compose up        # start everything
docker compose up seaweed  # start a specific service
docker compose down      # stop everything
```

State is declarative where possible — tool config lives in this repo. See each tool's README for setup steps.
