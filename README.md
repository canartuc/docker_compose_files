# Docker Compose Files

A collection of Docker Compose configurations for common development services.

## Available Services

### PostgreSQL + Adminer
**Directory:** `postgres/`

Basic PostgreSQL database with Adminer web UI for database management.

```bash
cd postgres && docker-compose up -d
```

| Service   | Port | Description          |
|-----------|------|----------------------|
| PostgreSQL| 5432 | Database server      |
| Adminer   | 8080 | Web-based DB admin   |

**Credentials:** `dbuser` / `dbpassword` / `testdb`

---

### Kafka + Debezium + PostgreSQL (CDC Pipeline)
**Directory:** `kafka_debezium_postgres/`

Complete Change Data Capture (CDC) stack for streaming database changes to Kafka.

```bash
cd kafka_debezium_postgres && docker-compose up -d
```

| Service         | Port | Description                    |
|-----------------|------|--------------------------------|
| Zookeeper       | 2181 | Kafka coordination             |
| Kafka           | 9092 | Message broker                 |
| PostgreSQL      | 5432 | Debezium-enabled database      |
| Debezium Connect| 8083 | CDC connector REST API         |

**Credentials:** `dbuser` / `dbpassword` / `testdb`

---

### Stirling-PDF
**Directory:** `stirling_pdf/`

Self-hosted PDF manipulation and processing tool.

```bash
cd stirling_pdf && docker-compose up -d
```

| Service      | Port | Description              |
|--------------|------|--------------------------|
| Stirling-PDF | 8080 | PDF tool web interface   |

**Note:** Update volume paths in `docker-compose.yml` before running.

**Source:** https://github.com/Stirling-Tools/Stirling-PDF

## Usage

```bash
# Start a service
cd <service_directory> && docker-compose up -d

# Stop a service
docker-compose down

# View logs
docker-compose logs -f

# Remove volumes (reset data)
docker-compose down -v
```

## License

See [LICENSE](LICENSE) file.
