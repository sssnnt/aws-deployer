AWS Deployer Docker - Docker Image
=================================
This repository contains an extension of the aws-deployer docker image that adds possiblity to use the serverless framework and nodejs/npm.

Check out the serverless framework [here](https://serverless.com)
The serverless framework is a nice tool to support you when you for example use aws lambdas.


How to use
==========
Same as [``aws-deployer``](../aws-deployer) image.

## Example gitlab-ci.yml stage

build:
    stage: build
    image: aws-deployer:serverless
    script:
        - assume -a ${account} -r ${deployRole} -p assumed-profile
        - npm install
        - serverless deploy -v --stage test


## Links
[Docker image on Dockerhub](https://hub.docker.com/r/scaniadevtools/aws-deployer/)

__Happy Hacking__

*Scania Devtools Team*

## Want to contribute?
Go to the [CONTRIBUTING]("../CONTRIBUTING.md") page.
