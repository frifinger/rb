# The internet store for Russian Brushes

Based on Spree framework (RoR).

## Delpoy (dokku):

0. Prepare dokku on server (via ssh):
  - `dokku app:create _app-name_`
  - Install PostgreSQL on server (if required)
  - `dokku postgres:create _app-db-name_`
  - `dokku postgres:link _app-db-name_ _app-name_`
1. Prepare git (git init, git commit)
3. `git remote add dokku dokku@your_ip:_app-name_`
4. `git push dokku master`
5. On server (via ssh):
  - `dokku run _app-name_ rake db:migrate`
  - `dokku run _app-name_ rake spree_auth:admin:create`