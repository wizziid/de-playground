# SeaweedFS

Local single-node SeaweedFS instance with S3 protocol enabled. Used as an S3-compatible object store for the local DE sandbox.

## Setup

1. Copy `s3/s3_config_public.json` to `s3/s3_config_private.json` and replace the placeholder credentials with real values. For dev purposes, generate values with `openssl rand -hex 20` and use one string for the access key and another for the secret key.
2. Add the same credentials to your `~/.aws/credentials` under a named profile.
3. Run `docker compose up` from the root of the repo.

The private config file is gitignored — only the public template is committed.

## S3 Access

SeaweedFS exposes an S3-compatible API on port `8333`. Configure your AWS CLI profile to point at it:

```ini
# ~/.aws/credentials
[seaweed-admin]
aws_access_key_id = <your_access_key>
aws_secret_access_key = <your_secret_key>

# ~/.aws/config
[profile seaweed-admin]
endpoint_url = http://localhost:8333
```

## Buckets

Buckets are not declared in config — they must be created manually via the CLI before first use:

```bash
aws s3 mb s3://my-bucket
```

Bucket data and SeaweedFS volume data is persisted to `~/var/lib/seaweedfs/data` on the host.

## Ports

See [SeaweedFS Production Setup](https://github.com/seaweedfs/seaweedfs/wiki/Production-Setup) for a full port reference.

The master UI is available at `http://localhost:9333`. The filer UI is at `http://localhost:8888`.
