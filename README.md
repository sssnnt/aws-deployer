[![Docker status](https://dockerbuildbadges.quelltext.eu/status.svg?organization=matsskoglund&repository=aws-deployer)](https://hub.docker.com/r/matsskoglund/aws-deployer/builds/)

AWS Deployer Docker Image
=================================
This repository contains Docker image for running AWS cli commands that assumes a IAM role baked into one cli commands. They can be useful for deploying AWS CloudFormation templates in e.g. a build server where the build server need to assume some other role to deploy.


How to use
==========
#### Showing usage.
```sh
> docker run -it matsskoglund/aws-deployer --help
  assume [-h|--help] [-v|--version] -a|--account <aws account number> [-r|--role <IAM role>] [-p|--profile <aws cli profile name>] []

  Assumes a role in the specified AWS account and creates temporary credentials in the named profile.
    -h|--help      prints this help
    -v|--version   prints the current version of this script
    -a|--account   the AWS account number to deploy to. (mandatory)
    -r|--role      the IAM role to assume
    -p|--profile   the name of the resulting aws cli profile to use
```

#### Showing script version.

```sh
> docker run -it matsskoglund/aws-deployer --version
  assume version 1.0.0
```

#### Assuming an AWS role.

The example below is a Gitlab ``.gitlab-ci.yml`` file in a project where an AWS CloudFormation template named ``cloudformation-template.yml`` is validated in the AWS account *123456789012* by assuming the ``arn:aws:iam::123456789012:role/DeployRole`` role that must exist in the AWS account and have ``cloudformation:ValidateTemplate`` permissions. 

```yml
image: matsskoglund/docker-aws-deployer

stages:
  - validate-template 

validate-template-in-account-123456789012: 
  stage: validate-template

  before_script:
    - assume --account 123456789012 --profile assumed-profile
  script:
    - aws cloudformation validate-template --template-body file://cloudformation-template.yml --region eu-west-1 --profile assumed-profile
```
The account number (*123456789012* in this example) can be located in the AWS console when logged into the account by selecting   *"Support"->"Support Center"* in the menu.  


### Start a bash session inside the container.
Starting a bash session in the container can be useful for debugging purposes.

```sh
   > docker run -it matsskoglund/aws-deployer bash
   bash-4.3#
```



