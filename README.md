# Django Tenant SaaS Example.

This application enables Django powered websites to have multiple tenants via PostgreSQL schemas. A vital feature for every Software-as-a-Service website.

Django provides currently no simple way to support multiple tenants using the same project instance, even when only the data is different. Because we don’t want you running many copies of your project, you’ll be able to have:

    Multiple customers running on the same instance

    Shared and Tenant-Specific data

    Tenant View-Routing
    
Base of TiBillet.re


## Installation for test :

```shell
cd Docker/Development
cp env_example .env

# populate .env file with your variables.

docker-compose --build up -d

# Go inside the Django Container :
docker exec -ti tibillet_django bash

# --> within the container :
  # on crée la DB :
  python manage.py migrate
  
  # on crée le premier tenant "demo" :
  python manage.py create_demo_tenant
  
  # Web Server ( only for test and dev ! )
  python /DjangoFiles/manage.py runserver_plus 0.0.0.0:8002
   
  # For localhost, edit your /etc/host ( or equivalent if you don't use a Debian like OS ) with :
127.0.0.1       tibillet-local.me
127.0.0.1       www.tibillet-local.me
127.0.0.1       demo.tibillet-local.me
```

Test with http://www.tibillet-local.me:8002 and http://demo.tibillet-local.me:8002
