AWS Deployer Docker Image
=================================
This repository contains Docker image for running bash cli commands that are shortcuts for several AWS cli commands. They can be useful for deploying AWS CloudFormation templates in e.g. a build server.

The following command is supported:
```sh
    assume
```

[![Docker status](https://dockerbuildbadges.quelltext.eu/status.svg?organization=matsskoglund&repository=aws-deployer)](https://dockerbuildbadges.quelltext.eu/status.svg?organization=matsskoglund&repository=aws-deployer)

How to use
==========
```sh
   docker run -it matsskoglund/aws-deployer --version
```



