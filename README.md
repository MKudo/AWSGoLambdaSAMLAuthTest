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
### Set up your System environment
1. Check your $TMPDIR environment variable. If it not exist, you need to set it. Or if it contains a symbolic link, you need to set it actual directory.

### Start docker
1. Wake up docker container with `./docker/docker-compose.yml`

#### Note
I changed keycloak web ui port from 8080 to 8090. 8080 is used by localstack's dashboard.

### Set up services
#### Install localstack test function
This process is testing your localstack staetus. Then you can skip this process.

See `src/test`. The Hello function is [sample go function](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/go-programming-model-handler-types.html).

1. Compile it ([see](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/lambda-go-how-to-create-deployment-package.html))
1. Archive it
1. Create function

```
aws lambda create-function --endpoint-url http://localhost:4574 --region us-east-1 --profile localstack --function-name test --runtime go1.x --role r1 --handler main --zip-file fileb://main.zip
```

1. Test function with aws cli

```
aws lambda invoke --endpoint-url=http://localhost:4574 --function-name test log.txt
```
#### Install auth function
Choice `Custom Authorizer` or `handler`.

##### With custom authorizer
You can use API gateway's custom authorizer. This lambda function will be called when API gateway accept the request.

##### With auth handler
Or you can use simple handler for your application. In this case, you need to make utility function to check token was expired or not.

#### Add client in keycloak
Add this test application as client to keycloak.

#### Make user in keycloak
Make new user for test in keycloak.

## Know Issues

## Contribution

## Licence

## Author
- [Masahiko Kudo](https://github.com/MKudo)
