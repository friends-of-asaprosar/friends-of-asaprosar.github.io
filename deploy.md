---
title: Deployment
---

# Deploying an instance of REIMS2

REIMS2 consists of two parts:

- Backend written in Java with Spring Boot
- Frontend based on Vue+Vuetify+Nuxt, written in Javascript/Typescript

We use Dokku for deploying, because it's very easy and even allows nice stuff like zero downtime deployments.

## Installing REIMS with Dokku

1. Install Dokku on the server ([tutorial](https://dokku.com/docs/getting-started/installation/)). In the web setup at the end, enable VHOSTS.
2. On the developer machine:
   ```bash
   # Set git remote config
   cd reims2-backend
   git remote add dokku dokku@YOUR_DOKKU_DOMAIN.com:api
   cd reims2-frontend
   git remote add dokku dokku@YOUR_DOKKU_DOMAIN.com:frontend
   ```
3. Deploy with Dokku!
   ```bash
   git push api
   git push frontend
   ```
4. Make the API and frontend container speak with each other. **On the server**, run the following commands:
   ```bash
   # Make frontend listen on the domain
   dokku domains:set frontend YOUR_DOMAIN_NAME.com
   # Allow frontend <-> backend communication
   dokku network:create reims
   dokku network:set frontend attach-post-deploy reims
   dokku network:set api attach-post-deploy reims
   dokku network:rebuildall
   # Set the API container name URL for the frontend including the /api prefix
   dokku config:set frontend API_URL=https://api.web:5000/pvh/api/
   dokku ps:rebuild api
   dokku ps:rebuild frontend
   ```
5. That's all, REIMS2 is already deployed! To add SSL, do the following on the server:
   ```bash
   sudo dokku plugin:install https://github.com/dokku/dokku-letsencrypt.git
   # Enable HTTPS
   dokku letsencrypt:enable api
   dokku letsencrypt:enable frontend
   # Enable cronjob for letsencrypt
   dokku letsencrypt:cron-job --add
   ```

## Deploying updates of REIMS

Setup: Follow step 2 of the previous tutorial once per machine.

Deploy: Follow step 3 for deploying an update.
