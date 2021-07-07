# Docker SQS-compatible image
Docker image containing an SQS-compatible queue implementation ([ElasticMQ](https://github.com/adamw/elasticmq)) for offline development of software that uses SQS.

# Running

## Using `docker`

```
docker run -p 9324:9324 graze/sqs-local
```

You can use a custom conf file as well to override the config stored in the image.

```
docker run -p 9324:9324 -v "$PWD/elasticmq.conf:/elasticmq.conf" graze/sqs-local
```

### Multiarch

This allows you to run the image on various architectures. The recommendation would be to use this if you're trying to run thi on an Apple M1.

```
docker run -p 9324:9324 graze/sqs-local:multiarch
```

## Using `docker-compose`

```
services:
  sqs:
    image: graze/sqs-local
    ports:
      - 9324:9324
    volumes:
      - ./elasticmq.conf:/elasticmq.conf
```

### Multiarch

If you want to use the multiarch image in your docker-compose file then

```
services:
  sqs:
    image: graze/sqs-local:multiarch
    ports:
      - 9324:9324
    volumes:
      - ./elasticmq.conf:/elasticmq.conf
```

```
docker-compose up sqs
```
