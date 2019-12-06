# Ambassador

## Create pipeline to install ambassador
- See build server on how to login
- fly -t sw set-pipeline --pipeline ambassador --config pipeline.yml -l pipeline/credentials.yml
- fly -t sw unpause-pipeline -p ambassador

## installing ambassador with helm
- https://github.com/linkyard/concourse-helm-resource

## Getting a token for helm

https://kubernetes.io/docs/tasks/access-application-cluster/access-cluster/#programmatic-access-to-the-api

APISERVER=$(kubectl config view --minify | grep server | cut -f 2- -d ":" | tr -d " ")
SECRET_NAME=$(kubectl get secrets | grep ^default | cut -f1 -d ' ')
TOKEN=$(kubectl describe secret $SECRET_NAME | grep -E '^token' | cut -f2 -d':' | tr -d " ")

https://kubernetes.io/docs/reference/access-authn-authz/authentication/#authentication-strategies

https://kubernetes.io/docs/concepts/cluster-administration/certificates/
