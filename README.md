# adpro-module-11
### Reflection 1
1. Before being exposed as a service, the application cannot be accessed by minikube, raising an SVC_NOT_FOUND error. After being exposed as a service, especially after being exposed as a LoadBalancer, the deployment is given a public IP, which allows it to be accessed openly by the minikube cluster.

  Each time I open the application, a new "GET /" request is made. Naturally, the number of logs does increase every time I open the app.

2. Namespaces are used to divide cluster resources between users or applications. Whenever you run 'kubectl get' without the -n flag, the default namespace is chosen. 

  Addons and plugins, such as the Metrics API that was added earlier are typically added in the kube-system namespace in order to keep things tidy and organized.

  Because we didn't register the hello-node deployment to the kube-system namespace, it won't show up when we explicitly set the -n flag to kube-system.

### Reflection 2
1. The recreate deployment strategy simply winds down all running pods, then starts creating new pods from scratch. This leads to downtime, but better consistency between deployments, as there is no chance that different users are accessing different versions of the application at one time. 

  The rolling update strategy gradually replaces old pods, making sure that new pods are healthy before putting them in place of the old pods. This allows for virtually no downtime, but might cause inconsistency between application versions for a short period of time while the old pods are still running.

pods, then starts creating new pods from scratch. This leads to downtime, but better consistency between deployments, as there is no chance that different users are accessing different versions of the application at one time. 

  The rolling update strategy gradually replaces old pods, making sure that new pods are healthy before putting them in place of the old pods. This allows for virtually no downtime, but might cause inconsistency between application versions for a short period of time while the old pods are still running.

pods, then starts creating new pods from scratch. This leads to downtime, but better consistency between deployments, as there is no chance that different users are accessing different versions of the application at one time. 

  The rolling update strategy gradually replaces old pods, making sure that new pods are healthy before putting them in place of the old pods. This allows for virtually no downtime, but might cause inconsistency between application versions for a short period of time while the old pods are still running.

2. In order to redeploy the application using the Recreate strategy, I first run `kubectl edit deployment spring-petclinic-rest`. This opens a Vim editor in which I can edit the YAML file. I change the `strategy` key to have the `type: Recreate`.

  After editing the manifest file, I simply run `kubectl rollout restart deploment spring-petclinic-rest`. This restarts all pods from the spring-petclinic-rest deployment.

3. **Attached in the GitHub repository**

4. The benefits of using a k8s manifest file lies in its reproducibility. Other than using the same docker image, which ensures consistent builds across devices, the manifest file also ensures deployment environment consistency.

  Furthermore, manifest files can be stored in version control using Git. This allows the versioned sharing of manifest files between developers to ensure a consistent development experience.

  The main benefit of using version control in this case is that it allows easier rollbacks to a previous version if needed.
