# tutorial-aws-symfony-ci
$(aws ecr get-login --no-include-email --region eu-west-1)

Stage
docker build -t tutorial-aws-symfony-ci:stg -f Dockerfile.stg .
docker tag tutorial-aws-symfony-ci:stg 254002134964.dkr.ecr.eu-west-1.amazonaws.com/tutorial-aws-symfony-ci:stg
docker push 254002134964.dkr.ecr.eu-west-1.amazonaws.com/tutorial-aws-symfony-ci:stg
docker run -p 80:80 tutorial-aws-symfony-ci:stg

Prod
docker build -t tutorial-aws-symfony-ci:prod .
docker tag tutorial-aws-symfony-ci:prod 254002134964.dkr.ecr.eu-west-1.amazonaws.com/tutorial-aws-symfony-ci:prod
docker push 254002134964.dkr.ecr.eu-west-1.amazonaws.com/tutorial-aws-symfony-ci:prod
docker run -p 80:80 tutorial-aws-symfony-ci:prod


Add role AmazonEC2ContainerRegistryReadOnly to aws-elasticbeanstalk-ec2-role in IAM

Get docker login by:
aws ecr get-login --region eu-west-1 --no-include-email


Add EB_REGION (eu-west-1)  variable to CircleCI
https://circleci.com/gh/mkulygin/tutorial-aws-symfony-ci/edit#env-vars

Check docker login:
docker login -u AWS -p * https://254002134964.dkr.ecr.eu-west-1.amazonaws.com
eval $(aws ecr get-login --region eu-west-1 --no-include-email)

Test branch