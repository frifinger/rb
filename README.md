# The internet store for Russian Brushes

Based on Spree framework (RoR).

## Delpoy (dokku):

0. Prepare dokku on server (via ssh):
  - `dokku app:create appname`
  - Install PostgreSQL on server (if required)
  - `dokku postgres:create app-db-name`
  - `dokku postgres:link app-db-name app-name`
1. Prepare git (git init, git commit)
3. `git remote add dokku dokku@your_ip:app-name`
4. `git push dokku master`
5. On server (via ssh):
  - DB migration: `dokku run app-name rake db:migrate`
  - Creating the admin: `dokku run app-name rake spree_auth:admin:create`
  - Persistent storage: `mkdir -p /storage/appname/public/spree/products`, `dokku docker-options:add appname run "-v /storage/appname/public/spree/products:/app/public/spree/products"` and `dokku ps:rebuild appname`