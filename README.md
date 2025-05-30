# adpro-module-11
### Reflection 1
1. Before being exposed as a service, the application cannot be accessed by minikube, raising an SVC_NOT_FOUND error. After being exposed as a service, especially after being exposed as a LoadBalancer, the deployment is given a public IP, which allows it to be accessed openly by the minikube cluster.

  Each time I open the application, a new "GET /" request is made. Naturally, the number of logs does increase every time I open the app.

2. Namespaces are used to divide cluster resources between users or applications. Whenever you run 'kubectl get' without the -n flag, the default namespace is chosen. 

  Addons and plugins, such as the Metrics API that was added earlier are typically added in the kube-system namespace in order to keep things tidy and organized.

  Because we didn't register the hello-node deployment to the kube-system namespace, it won't show up when we explicitly set the -n flag to kube-system.
