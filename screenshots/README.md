# Screenshots

To help review your infrastructure, please include the following screenshots in this directory::

## Deployment Pipeline

- DockerHub showing containers that you have pushed
  - Dockerhub listing images for each created microservice: _flauberjp/udagram-frontend_, _flauberjp/udragram-reverseproxy_, _flauberjp/udagram-api-feed_, and _flauberjp/udagram-api-user_
    ![printscreen of images on DockerHub](./evidences/dockerhub_evidence.PNG)
- GitHub repository’s settings showing your Travis webhook (can be found in Settings - Webhook)

  - reverseproxy
    - circleci webhook
      ![printscreen of circleci webhook](./evidences/web-hook-reverseproxy.PNG)
    - circleci config file
      ![printscreen of circleci config file](./evidences/circle-ci-configuration-for-reverseproxy.PNG)
  - udagram-api-feed
    - circleci webhook
      ![printscreen of circleci webhook](./evidences/web-hook-udagram-api-feed.PNG)
    - circleci config file
      ![printscreen of circleci config file](./evidences/circle-ci-configuration-for-udagram-api-feed.PNG)
  - udagram-api-user
    - circleci webhook
      ![printscreen of circleci webhook](./evidences/web-hook-udagram-api-user.PNG)
    - circleci config file
      ![printscreen of circleci config file](./evidences/circle-ci-configuration-for-udagram-api-user.PNG)
  - udagram-frontend
    - circleci webhook
      ![printscreen of circleci webhook](./evidences/web-hook-udagram-frontend.PNG)
    - circleci config file
      ![printscreen of circleci config file](./evidences/circle-ci-configuration-for-udagram-frontend.PNG)

- Travis CI showing a successful build and deploy job
  - Circle CI pipelines for all 4 repositories
    ![printscreen of circle ci pipelines](./evidences/Circle_CI_interface_evidence.PNG)

## Kubernetes

- To verify Kubernetes pods are deployed properly
  ![kubectl get pods output printscreen](./evidences/output-get-pods.PNG)
- To verify Kubernetes services are properly set up
  ![kubectl describe services output printscreen](./evidences/output-describe-services.PNG)

- To verify that you have horizontal scaling set against CPU usage
  ![kubectl describe hpa output printscreen](./evidences/output-describe-hpa.PNG)

- To verify that you have set up logging with a backend application
  - Customer submitted a request, which CorrelationId was eb31f9b1-b379-494b-9359-9f129b4be06b, what could identify him. It was send as part of the haders from a request from the browser.
    - In the image below, you see that in the request header we inserted a correlation id.
      ![kubectl get pods output printscreen](./evidences/frontend-header-request.png)
    - In the image below, we have the logs of the pod that handled the request, and by doing it a log printing the correlation id was printed as log.
      ![kubectl get pods output printscreen](./evidences/backend-feed-logs.png)
