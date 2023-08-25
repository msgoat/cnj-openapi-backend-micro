# cnj-openapi-backend-micro

Cloud native Java backend based on Eclipse MicroProfile using MP OpenAPI feature to document REST APIs.

## Status

![Build status](https://codebuild.eu-west-1.amazonaws.com/badges?uuid=eyJlbmNyeXB0ZWREYXRhIjoiTmh5RjJzNTlmSktpakk2eXorZUh6OUVUTDlVd0NhOGVoSElrMUVoeVEzeWdwWld1SVoxQm93aXBzaU5vYWg3OCtvcUE4RU5JbVdZMVhvazh0Tkk5VEZrPSIsIml2UGFyYW1ldGVyU3BlYyI6InVjbXJ2UEpWcGUxczl0b0wiLCJtYXRlcmlhbFNldFNlcmlhbCI6MX0%3D&branch=main)

## Release Information

A changelog can be found in [changelog.md](changelog.md).

## Docker Pull Command

`docker pull docker.cloudtrain.aws.msgoat.eu/cloudtrain/cnj-openapi-backend-micro`

## Synopsis

### Static vs. generated OpenAPI files

In this showcase, [MP OpenApi feature](https://github.com/eclipse/microprofile-open-api) is used to demonstrate the `Code First` approach
of documenting REST API according to the OpenAPI standard: the actual OpenAPI specification file is generated from
annotated application code. The generated OpenAPI specification file is served by MP OpenApi via `/openapi` in YAML format.

To demonstrate the `API First` or `Contract First` approach as well, a static OpenAPI specification file has been
added (see [openapi.yml](src/main/resources/META-INF/openapi.yml)) to the application code. The MP OpenAPI automatically
serves the static file as well.

MP OpenAPI supports a combination of both approaches: The `openapi.yml` file may be a fragment containing only the
static parts the OpenAPI specification. Fragments will be merged with the OpenAPI data generated from annotated code.

## HOW-TO build this application locally

If all prerequisites are met, just run the following Maven command in the project folder:

```shell 
mvn clean verify -P pre-commit-stage
```

Build results: a Docker image containing the showcase application.

## HOW-TO start and stop this showcase locally

In order to run the whole showcase locally, just run the following docker commands in the project folder:

```shell 
docker compose up -d
docker compose logs -f 
```

Press `Ctlr+c` to stop tailing the container logs and run the following docker command to stop the showcase:

```shell 
docker compose down
```

## HOW-TO demo this showcase

The showcase application will be accessible:
* locally via `http://localhost:38080`
* remotely via `https://train2023-dev.k8s.cloudtrain.aws.msgoat.eu/cloudtrain/cnj-openapi-backend-micro` (if the training cluster is up and running)

The OpenAPI specification of the exposed REST API is available at URI `/openapi`.
