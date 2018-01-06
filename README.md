# Testdriven-app

## what is this?

I'm following the tutorial series at testdriven.io on microservices with docker, flask, and react

## Notes

(runnin in xonsh shell)

### to set the env:
execx($(docker-machine env testdriven-prod).replace('export ', '$'))

### build sequence
docker-compose -f docker-compose-prod.yml up -d --build
docker-compose -f docker-compose-prod.yml run users-service python manage.py recreate_db
docker-compose -f docker-compose-prod.yml run users-service python manage.py seed_db
docker-compose -f docker-compose-dev.yml run users-service python manage.py test

### connect to postgres
docker exec -ti users-db psql -U postgres -W