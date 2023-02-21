# Upgrade de version Sentry
```bash
cd self-hosted
git add .
git stash
git pull
git checkout 23.2.0
git stash pop # Use vim to edit conflicts
./install.sh
```

# Redémarrage
```bash
cd self-hosted
docker-compose down
docker-compose up -d
```

# Configuration (mail, ip, ...)
2 fichiers à modifier :
- self-hosted/.env
- self-hosted/sentry/config.yml

# Backup
## Lien : https://develop.sentry.dev/self-hosted/backup/
```bash
docker-compose run --rm -T -e SENTRY_LOG_LEVEL=CRITICAL web export > sentry/backup.json
docker-compose run --rm -T web import /etc/sentry/backup.json
```
