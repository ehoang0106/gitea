# Gitea Docker Setup

Docker Compose configuration for running [Gitea](https://gitea.io/), a self-hosted Git service.

## Prerequisites

- Docker and Docker Compose
- MySQL database

## Quick Start

1. Copy the environment file:
   ```bash
   cp .env.example .env
   ```

2. Edit `.env` with your MySQL credentials:
   ```
   DB_HOST=your_mysql_host
   DB_NAME=gitea
   DB_USER=your_db_user
   DB_PASSWORD=your_db_password
   ```

3. Start Gitea:
   ```bash
   docker-compose up -d
   ```

4. Access at http://localhost:3000

## Ports

- **3000**: Web interface
- **222**: SSH for Git operations

## Data

All data is stored in the `./gitea` directory.

## Commands

```bash
docker-compose up -d      # Start
docker-compose down       # Stop
docker-compose logs -f    # View logs
docker-compose restart    # Restart
```

### SSH Set Up

`Gitea` uses port `222` for SSH connections.

To get the ssh authentication working, you need to add the following to your `~/.ssh/config` file (create one if it doesn't exist):

```
Host [your-gitea-host]
  HostName [your-gitea-domain-or-ip]
  User git
  Port 222
  IdentityFile [the-path-to-your-ssh-private-key]
  IdentitiesOnly yes
```
