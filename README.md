# POC

- Resources [https://www.serverless.com/framework/docs/guides/compose]

## Commands

- limit the number of services that are deployed concurrently

```bash
    serverless deploy --verbose --max-concurrency 5
```

- deploy specific service only

```bash
    serverless deploy --service=sns
    # Shortcut alternative
    serverless sqs:deploy
```

- tail logs of all functions across services

```bash
    serverless logs --tail
```

- tail logs of specific function in specific service

```bash
    serverless logs --service=sns --function=hello
 
    # Shortcut alternative
    serverless sns:logs --function=world
```

- serverless also has built in plugins for working offline
- to run a specific service offline

```bash
    serverless sns:offline
```

- The outputs of a service are stored locally (in the .serverless/ directory). If a colleague deployed changes that changed the outputs of a service, you can refresh your local state via the refresh-outputs command:

```bash
    serverless refresh-outputs
```

- remove all services

```bash
    serverless remove
```

- remove specific service

```bash
    serverless sns:remove
```

- view outputs of all services

```bash
    serverless outputs
```

- view info of all services

```bash
    serverless info
```

## FAQ

### Is multi-region deployment possible via Compose?

- It is possible to deploy different services to different regions. For example, deploy service frontend to us-east-1 and service backend to eu-west-3.

- However, Compose currently does not support deploying the same service to multiple regions. The reason is that each service is packaged in the .serverless/ directory. If the same service was to be deployed in parallel to different regions, package artifacts would conflict and overwrite each others.

### Handle Multiple Bucket Creation for deployment Issue

- Create a bucket yourself and specify as the deployment bucket and serverless will use them
