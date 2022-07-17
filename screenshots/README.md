# Screenshots
To help review your infrastructure, please include the following screenshots in this directory::

## Deployment Pipeline
* DockerHub showing containers that you have pushed
![Dockerhub](DockerhubFinala.PNG)
* GitHub repository’s settings showing your Travis webhook (can be found in Settings - Webhook)
* Travis CI showing a successful build and deploy job
![Travis success](travisbuildsuccess.PNG)

![Travisbuild](TravisCIbuiltandpush.PNG)

## Kubernetes
* To verify Kubernetes pods are deployed properly
```bash
kubectl get pods
```
![getpods](kbctlgetpods.PNG)
* To verify Kubernetes services are properly set up
```bash
kubectl describe services
```
![user](describeservice1.PNG)
![frontend](describeservicefrontend.PNG)
![kubernates](describeserviceskubernates.PNG)
![feed](describeservices.PNG)
![publicreverse](describeservicepublicreverseproxy.PNG)
![reverseproxy](describeservicesreverseproxy.PNG)
* To verify that you have horizontal scaling set against CPU usage
```bash
kubectl describe hpa
```

![userhpa](hpaBackendUser.PNG)
![hpafrontend](hpaFrontend.PNG)
![hpareverseproxy](hpaReverseproxy.PNG)
* To verify that you have set up logging with a backend application
```bash
kubectl logs {pod_name}
```
![podlog](kbctlpodlogs.PNG)
