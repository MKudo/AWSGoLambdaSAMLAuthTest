# AWSGoLambdaSAMLAuthTest
==========
Test project to use SAML on AWS for MSA service with Lambda(Go)

## Description

## Requirement
- docker
  - Using localstack docker container for test
  - Using keycloak docker container for test

## Usage
1. Check your $TMPDIR environment variable. If it not exist, you need to set it. Or if it contains a symbolic link, you need to set it actual directory.
1. Wake up docker container with `./localstack/docker-compose.yml`
1. Wake up keycloak container with `./keycloak/docker-compose.yml`

### Note
I changed localstack web ui port from 8080 to 9080. 8080 is used by MySQL DB for keycloak.

## Know Issues

## Contribution

## Licence

## Author

[Kudo]
