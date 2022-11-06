# misskeytools

This repository contains various tools for interacting with Misskey.

## Setup

We run `Misskey` via `docker-compose`.

**Note**: This is not a secure setup for Misskey, this is just for local development.

First setup the local DNS entries for `misskey.internal`:

```bash
echo "127.0.0.1 misskey.internal" | sudo tee -a /etc/hosts
# Optional: For Mastodon testing
echo "127.0.0.1 mastodon.internal" | sudo tee -a /etc/hosts
```

Then start the `Misskey` instance:
  
```bash
docker compose up -d
```

### Mastodon Setup

Migrate the database:

```bash
docker compose run --rm mastodon bundle exec rake db:migrate
```

Create the initial user:

```bash
# Password will be shown after this command is ran, exactly once.
docker compose run --rm mastodon bin/tootctl accounts create testuser --email testuser@example.com --confirmed --role Owner
```

## License

[Apache 2.0](LICENSE)
