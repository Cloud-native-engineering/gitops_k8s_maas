# MyBlog - Simple Sample Application

This is a simple Flask application connected to a PostgreSQL database.

> This application was initially forked from: [devops_blog](https://github.com/Cloud-native-engineering/devops_blog)

The current source code can be found here: [MyBlog Source Code](https://github.com/Cloud-native-engineering/devops_blog)

## Contents

- MyBlog
  - Deployment
  - Ingress
  - TLS
  - Service
- PostgreSQL
  - Deployment
  - PVC
  - Service

## Requirements

The following ConfigMap is required for deploying the application:

```sh
kubectl create configmap pgsql-config --from-literal=POSTGRES_DB=mydatabase --from-literal=POSTGRES_USER=m`user --from-literal=POSTGRES_PASSWORD=mypassword --namespace=myblog-yaml
```
