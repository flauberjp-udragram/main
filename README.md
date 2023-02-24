## About

This repository is the result of transforming a monolith app in a microservices one, where in the end it is served using DevOps best practices with the usage of circleci and kubernetes with high scalability and availability.

It contains docker compose files to generate builds, one to up the services locally using docker, and on k8s-files directory, files used to run it on kubernetes.

To make it work in group, download the microservices repositories listed below, and on the same directory download this project, this way you should be good to use the files the way they are.

**Attention**: This project uses kubernetes secrets (_aws-secrets.yaml_, and _env-secrets.yaml_), they were removed for security purpuse, you need to use your values.

- Microservices:

  - [udagram-api-feed](https://github.com/flauberjp-udragram/udagram-api-feed)
  - [udagram-api-user](https://github.com/flauberjp-udragram/udagram-api-user)
  - [udagram-frontend](https://github.com/flauberjp-udragram/udagram-frontend)
  - [udagram-reverseproxy](https://github.com/flauberjp-udragram/reverseproxy)

- Original monolith
  - [udagram-frontend](https://github.com/flauberjp/udagram-frontend)
  - [udagram-backend](https://github.com/flauberjp/udagram-backend)
