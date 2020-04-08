## Docker

```
# build image
docker image build -t appt:1 .

# spin up container
docker container run -itd --rm \
    -v $(pwd):/app \
    -v /app/node_modules \
    -p 3000:3000 -e CHOKIDAR_USEPOLLING=true \
    --name appt appt:1

# spin up container with docker-compose
docker-compose up -d --build

# clean up
docker container stop appt
docker-compose down

# build production ready image
docker image build -f Dockerfile.prod -t appt:prod .

# spin up production ready container
docker container run -it --rm -p 80:80 --name appt appt:prod
docker-compose -f docker-compose.prod.yml up -d --build

# clean up
docker container stop appt
docker-compose -f docker-compose.prod.yml down
```
