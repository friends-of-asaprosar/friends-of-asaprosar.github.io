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
4. That's all, REIMS2 is already deployed! But we still have to change a few minor things **on the server**:
```bash
# Enable HTTPS
dokku letsencrypt:enable api
dokku letsencrypt:enable frontend
# Set the API url for the frontend including the /api prefix
dokku config:set frontend API_URL=https://api.YOUR_DOKKU_DOMAIN.com/pvh/api/
# Enable cronjob for letsencrypt
dokku letsencrypt:cron-job --add
```

## Deploying updates of REIMS

Setup: Follow step 2 of the previous tutorial once per machine.

Deploy: Follow step 3 for deploying an update.
