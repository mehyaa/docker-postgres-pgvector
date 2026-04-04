# PostgreSQL with pgvector

[pgvector](https://github.com/pgvector/pgvector) extension injected into official PostgreSQL images.

This repository provides Dockerfiles and automated builds for PostgreSQL with the `pgvector` extension across multiple PostgreSQL versions and OS variants.

## Supported Tags

The images are available on GitHub Container Registry (`ghcr.io`).

| PostgreSQL Version | OS Variant | Target Tag |
| :--- | :--- | :--- |
| **18** | Alpine, Bookworm, Trixie | `18-alpine`, `18-bookworm`, `18-trixie` |
| **17** | Alpine, Bookworm, Trixie | `17-alpine`, `17-bookworm`, `17-trixie` |
| **16** | Alpine, Bookworm, Trixie | `16-alpine`, `16-bookworm`, `16-trixie` |
| **15** | Alpine, Bookworm, Trixie | `15-alpine`, `15-bookworm`, `15-trixie` |
| **14** | Alpine, Bookworm, Trixie | `14-alpine`, `14-bookworm`, `14-trixie` |
| **13** | Alpine, Bookworm, Trixie | `13-alpine`, `13-bookworm`, `13-trixie` |

## Usage

### Quick Start

Run a container with the image (e.g., Postgres 18 Alpine variant):

```bash
docker run --name pg-vector -e POSTGRES_PASSWORD=mysecretpassword -p 5432:5432 -d ghcr.io/mehyaa/postgres-pgvector:18-alpine
```

### Enable Extension

After starting the container, you must enable the extension in your database:

```sql
CREATE EXTENSION IF NOT EXISTS vector;
```

### Docker Compose Example

```yaml
services:
  db:
    image: ghcr.io/mehyaa/postgres-pgvector:18-alpine
    environment:
      POSTGRES_PASSWORD: mysecretpassword
      POSTGRES_DB: mydb
    ports:
      - "5432:5432"
```

## OS Variants

- **Alpine**: Based on `alpine`. Lightweight and small footprint.
- **Bookworm**: Based on `debian:bookworm` (current stable).
- **Trixie**: Based on `debian:trixie` (testing).

## Building Locally

To build a specific version locally:

```bash
docker build -t postgres-pgvector:18-alpine ./18/alpine
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
