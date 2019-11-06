# AWSGoLambdaSAMLAuthTest
Test project to use SAML on AWS for MSA service with Lambda(Go)

## Description

## Requirement
- aws cli
  - You need to create profile name 'localstack'
    - You can use 'dummy' for access key id and secret access key
- docker
  - Using localstack docker container for test
  - Using keycloak docker container for test
- go

## Usage
1. Check your $TMPDIR environment variable. If it not exist, you need to set it. Or if it contains a symbolic link, you need to set it actual directory.
1. Wake up docker container with `./localstack/docker-compose.yml`
1. Create function for localstack test
1. Wake up keycloak container with `./keycloak/docker-compose.yml`

### localstack test function
See `src/test`. The Hello function is [sample go function](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/go-programming-model-handler-types.html).

1. Compile it ([see](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/lambda-go-how-to-create-deployment-package.html))
1. Archive it
1. Create function

```
aws lambda create-function --endpoint-url http://localhost:4574 --region us-east-1 --profile localstack --function-name test --runtime go1.x --role r1 --handler main --zip-file fileb://main.zip
```

1. Test function with aws cli

```
aws lambda --endpoint-url=http://localhost:4574 invoke --function-name test --payload '{"name":"AWS"}' log.txt
```

### Note
I changed localstack web ui port from 8080 to 9080. 8080 is used by Keycloak web ui.

## Know Issues

## Contribution

## Licence

## Author
- [Masahiko Kudo](https://github.com/MKudo)
