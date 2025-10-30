# Postman + Newman Git Setup (Multi-Env, Parallel CI)

This repo stores a Postman collection and runs it in GitHub Actions across **dev, staging, and prod** in **parallel**.

## Structure
```
postman/
  collections/
  environments/
.github/workflows/
```

## Environments
- `dev.postman_environment.json` (safe to commit; local defaults)
- `staging.postman_environment.template.json` (placeholders; safe to commit)
- `prod.postman_environment.template.json` (placeholders; safe to commit)

In CI, templates are converted into `*.local.json` using GitHub Variables/Secrets.

## GitHub Variables/Secrets to set
- Variables: `STAGING_API_BASE_URL`, `PROD_API_BASE_URL`
- Secrets: `STAGING_API_KEY`, `PROD_API_KEY`

## Local Usage
```bash
npm install
npm run postman:dev
# With your own staging/prod values, you can also run:
npm run postman:staging
npm run postman:prod
```
