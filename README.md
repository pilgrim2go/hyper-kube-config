# kube-auth-store

kube-auth-store - Provides a secure serverless API to store and retrieve k8s cluster credentials objects. kube-auth-store leverages AWS Secrets Manager for storing credential information. No trust API configuration requiring API key for access

## Post cluster and creds
```bash
kubectl config view --flatten -o json \
  | \
  http post \
  http://xxxxxxxx.execute-api.us-west-2.amazon.aws.com/dev/clusters/add \
  X-Api-Key:xxxx
```

## Remove cluster and creds
```bash
http post \
  https://xxxxxxxx.execute-api.us-west-2.amazonaws.com/dev/clusters/remove \
  X-Api-Key:xxxx \
  cluster_name=k8s-clustehr.cloud
```

## Get user creds

```bash
http get \
  https://xxxxx.execute-api.us-west-2.amazonaws.com/dev/clusters/get-k8-config?foo-cluster.cloud \
  X-Api-Key:xxxx 
```

## Requirements

* [Serverless](https://serverless.com/) - Serverless Framework
* [Docker](https://docker.com) - For serverless deploy
* [HTTPie](https://httpie.org/) - recommended for API client

### Deploying 

```bash
sls deploy \
  --stage dev \
  --product k8s \
  --owner myteam@foo.cloud \
  --team myteam \
  --environment dev
```