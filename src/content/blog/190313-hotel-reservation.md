---
title: 'Hotel Reservation API'
description: 'Basic REST API CRUD with Spring Boot for hotel reservations'
pubDate: '2019-03-13T01:22:34.123Z'
heroImage: 'https://i.imgur.com/yd18Ajcl.png'
categories: ['Spring Boot']
tags: ['Java', 'Docker', 'Maven', 'PostgreSQL']
author: '["pabloarak"]'
---

API ([Github](https://github.com/pabloarak/HotelReservation)) built with Spring Boot to manage hotel reservations.

For develop purpose you need Java 8, Maven 3.6, Eclipse IDE, Docker and a container of Postgres 9.6. Remember change credentials into application.yaml. Then for run and test the project:

```sh
clean install spring-boot:run
```

For production change the final directory into docker configuration in pom.xml. Remember change credentials into application-prod.yaml. Then for generate the docker image:

```sh
clean install docker:build
```

And for run in your production environment (You need a docker container with Postgres 9.6):

```sh
docker run -d --name COMPONENT_NAME --add-host=postgres_server:SERVER_IP -p SERVER_PORT:CONTAINER_POSTGRES_PORT PROJECT_IMAGE_NAME:latest
```

If you wish see the log:

```sh
docker logs -f COMPONENT_NAME
```

My Docker image is in [my docker hub](https://hub.docker.com/r/pabloarak/hotel-reservation).

Spring Security Login:

![Imgur](https://i.imgur.com/5NsIeQn.png)

The repository is in [Github](https://github.com/pabloarak/HotelReservation).
