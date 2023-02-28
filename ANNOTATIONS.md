## udagram-api-user

- Command to generate docker image:

docker build -t flauberjp/udagram-api-user:v1 .

- Command to run the image:

docker run --env=POSTGRES_HOST=database-1.ccqi1xutvahh.us-east-1.rds.amazonaws.com --env=AWS_PROFILE=DEPLOYED --env=AWS_REGION=us-east-1 --env=AWS_ACCESS_KEY_ID=AKIA2Q5B5NILFYU3L4YA --env=AWS_SECRET_ACCESS_KEY=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 --env=AWS_MEDIA_BUCKET=udagram-flauberjp-dev --env=JWT_SECRET=helloworld --env=POSTGRES_USERNAME=postgres --env=POSTGRES_PASSWORD=postgres --env=POSTGRES_DATABASE=database-1 -p 8081:8081 -d flauberjp/udagram-api-user:v1

## udagram-api-feed

- Command to generate udagram-api-feed docker image:

docker build -t flauberjp/udagram-api-feed:v1 .

- Command to run the image:

docker run --env=POSTGRES_HOST=database-1.ccqi1xutvahh.us-east-1.rds.amazonaws.com --env=AWS_PROFILE=DEPLOYED --env=AWS_REGION=us-east-1 --env=AWS_ACCESS_KEY_ID=AKIA2Q5B5NILFYU3L4YA --env=AWS_SECRET_ACCESS_KEY=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 --env=AWS_MEDIA_BUCKET=udagram-flauberjp-dev --env=JWT_SECRET=helloworld --env=POSTGRES_USERNAME=postgres --env=POSTGRES_PASSWORD=postgres --env=POSTGRES_DATABASE=database-1 -p 8082:8082 -d flauberjp/udagram-api-feed:v1

## udagram-reverseproxy

- Command to generate docker image:

docker build -t flauberjp/udagram-reverseproxy:v1 .

- Command to run the image:

docker run -p 8080:8080 -d flauberjp/udagram-reverseproxy:v1

## udagram-frontend

- Command to generate docker image:

docker build -t flauberjp/udagram-frontend:v1 .

- Command to run the image:

docker run -p 8080:8080 -d flauberjp/udagram-frontend:v1

# docker compose

- to build images from the composition. Run this command from the directory where you have the "docker-compose-build.yaml" file present
  docker-compose -f docker-compose-build.yaml build --parallel

- to start:
  docker compose up

- to stop:
  docker compose stop

- to remove unused and dangling images
  docker image prune --all

# application

- Local Link: http://localhost:8100

# how to create secret

Use this as basic yaml file:
apiVersion: v1
data:
AWS_ACCESS_KEY_ID: QUtJQTJRNUI1TklMRllVM0w0WUEK
AWS_SECRET_ACCESS_KEY: eFpId3M1MEdLN2dwUGtOOFdJc3hZeDA0Yk1qZjhBcUNNTkVJdEpKTDEwMQo=
kind: Secret
metadata:
name: env-secrets
type: Opaque

The value of AWS_ACCESS_KEY_ID need to be in base64, you can do that by using: echo "AKIA2Q5B5NILFYU3L4YA" | base64

# Kubernetes env variables and secrets

- Kubernetes ConfigMaps. Link: https://kubernetes.io/docs/concepts/configuration/configmap/

- Delete a configmap itself from Kubernetes. Link: https://stackoverflow.com/questions/59300475/delete-a-configmap-itself-from-kubernetes
  kubectl delete configmap my-cofigmap -n namespacename

- Kubernetes Secrets. Link: https://kubernetes.io/docs/concepts/configuration/secret/

- Deleting a Secret. Link: https://www.oreilly.com/library/view/kubernetes-cookbook-2nd/9781788837606/7b5207f3-b8d3-4ada-982a-55278875c1eb.xhtml

- Secrets Management in Kubernetes. Link: https://medium.com/avmconsulting-blog/secrets-management-in-kubernetes-378cbf8171d0

- Can't create Secret in Kubernetes: illegal base64 data at input. Link: https://stackoverflow.com/a/53395285/6771132

- Kubernetes pod gets recreated when deleted. Link: https://stackoverflow.com/a/44273280/6771132
  kubectl get deployments --all-namespaces
  kubectl delete -n NAMESPACE deployment DEPLOYMENT

- Check the logs – kubectl logs. Link: https://sysdig.com/blog/debug-kubernetes-crashloopbackoff/
  kubectl logs <mypod> --all-containers
- Debug Running Pods -> Debugging with container exec. Link: https://kubernetes.io/docs/tasks/debug/debug-application/debug-running-pod/#container-exec
  kubectl exec ${POD_NAME} -- bash

# Ionic and prod

- Ionic and prod: https://ionicframework.com/docs/cli/commands/build
  -- > _build locally: ionic serve -- prod_
  -- > _run locally: ionic serve -- prod_

# Logs

- Microservices logging best practices every team should know. Link: https://www.techtarget.com/searchapparchitecture/tip/5-essential-tips-for-logging-microservices
- Kubernetes log aggregation. Link: https://blog.logrocket.com/kubernetes-log-aggregation/
- Logging Architecture. Link: https://kubernetes.io/docs/concepts/cluster-administration/logging/#cluster-level-logging-architectures
- All Things Kubernetes: Painless Log Aggregation. Link: https://medium.com/rafay-systems/all-things-kubernetes-painless-log-application-aggregation-e2a7c75d3cba

# Kubernetes Dashboard UI

- [Deploy and Access the Kubernetes Dashboard](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)
- [Creating sample user, and get authentication token.](https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md)
  - To get token:
    > kubectl -n kubernetes-dashboard create token admin-user\_
- [How to Monitor Kubernetes With the Official Dashboard.](https://www.howtogeek.com/devops/how-to-monitor-kubernetes-with-the-official-dashboard/)
- [Tutorial: Deploy the Kubernetes Dashboard (web UI)](https://docs.aws.amazon.com/eks/latest/userguide/dashboard-tutorial.html)

# Cors

- https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Headers

# Intercepto

- https://www.edgesidesolutions.com/angular-interceptors/
- https://www.npmjs.com/package/uuid

# Metric

- [In AWS EKS, HPA (horizontal-pod-autoscaler) failed to get cpu utilization.](https://stackoverflow.com/a/69177173/6771132)
  > _kubectl top pods_
- [Installing the Kubernetes Metrics Server.](https://docs.aws.amazon.com/eks/latest/userguide/metrics-server.html)
- [Kubernetes HPA on AKS is failing with error 'missing request for cpu'.](https://stackoverflow.com/questions/62800892/kubernetes-hpa-on-aks-is-failing-with-error-missing-request-for-cpu)
  > kubectl logs -n kube-system -l k8s-app=metrics-server --container metrics-server

### References

- How do I pass environment variables to Docker containers? Link: https://stackoverflow.com/questions/30494050/how-do-i-pass-environment-variables-to-docker-containers

- AWS S3 JavaScript SDK getSignedUrl returns base path only. Link: https://stackoverflow.com/questions/29044817/aws-s3-javascript-sdk-getsignedurl-returns-base-path-only

- Creating a Dockerfile. Link: https://www.educative.io/collection/page/6630002/6521965765984256/6553354502668288

- Dockerfile - set ENV to result of command. Link: https://stackoverflow.com/questions/34911622/dockerfile-set-env-to-result-of-command

- How to set aws cli environment variables: https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-envvars.html

- Loading Credentials in Node.js from Environment Variables. Link: https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/loading-node-credentials-environment.html

- How to Generate a Presigned S3 URL via AWS CLI. Link: https://stackoverflow.com/questions/45869240/how-to-generate-a-presigned-s3-url-via-aws-cli

- Building from Docker Compose file. Link: https://docs.docker.com/build/bake/compose-file/

- Stopping docker containers and cleanup: https://phase2.github.io/devtools/common-tasks/stopping-containers-and-cleanup/

- Ways to set environment variables in Docker Compose. Link: https://docs.docker.com/compose/environment-variables/set-environment-variables/

- How to Kill a Process in Windows. Link: https://linuxhint.com/kill-process-windows/

- Use the tasklist command to see the list of running processes in Windows. Link: https://www.digitalcitizen.life/command-prompt-advanced-commands-system-information-managing-active-tasks/

- Configuring the Nginx Error and Access Logs. Link: https://linuxize.com/post/nginx-log-files/

- How to re-enable CircleCI for a GitHub organization. Link: https://circleci.com/docs/github-integration/#how-to-re-enable-circlecip-for-a-github-organization

- Is it possible for image to have multiple tags? Link: https://stackoverflow.com/a/56905333

- How To Migrate a Docker Compose Workflow to Kubernetes. Link: https://www.digitalocean.com/community/tutorials/how-to-migrate-a-docker-compose-workflow-to-kubernetes

- Run Ubuntu Linux containers on Windows. Link: https://ubuntu.com/tutorials/windows-ubuntu-hyperv-containers#1-overview

- How do I expose the Kubernetes services running on my Amazon EKS cluster? Link: https://aws.amazon.com/premiumsupport/knowledge-center/eks-kubernetes-services-cluster/

# Horizontal Pod Autoscaler (HPA)

- kubectl autoscale deployment backend-feed --cpu-percent=50 --min=2 --max=4
  - _kubectl delete hpa backend-feed_
- [How to fix failed get resource metric in Kubernetes HPA.](https://aptakube.com/blog/how-to-fix-failedgeteesourcemetric-hpa)
- [How to fix failed get resource metric in Kubernetes HPA](https://aptakube.com/blog/how-to-fix-failedgeteesourcemetric-hpa)

### References:

- https://stackoverflow.com/questions/37133114
- how-do-i-update-a-kubernetes-autoscaler
- https://schoolofdevops.github.io/ultimate-kubernetes-bootcamp/pods-health-probes/
- https://blog.logrocket.com/how-to-implement-a-health-check-in-node-js/
- https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/
- https://stackoverflow.com/questions/60038914/simple-healthcheck-endpoint-in-nginx-server-container

# kubectl set image

# JavaScript heap out of memory

- [JavaScript heap out of memory while running a Nodejs app on App Platform](https://www.digitalocean.com/community/questions/javascript-heap-out-of-memory-while-running-a-nodejs-app-on-app-platform)
- [Kubernetes CrashLoopBackOff — How to Troubleshoot](https://foxutech.medium.com/kubernetes-crashloopbackoff-how-to-troubleshoot-940dbb16bc84)
- [Node.js Memory Limits - What You Should Know](https://blog.appsignal.com/2021/12/08/nodejs-memory-limits-what-you-should-know.html)
- [How to solve JavaScript heap out of memory error](https://sebhastian.com/javascript-heap-out-of-memory/)
