1. Switch to minikube docker environment.
    ```bash
    eval $(minikube docker-env)
    ```

1. Build docker image.
    ```
    docker build -t hello-world:0.1 webapp/
    docker image ls hello-world
    ```

1. Deploy webapp to minikube/kubernetes cluster.
    ```
    kubectl apply -f webapp-deployment.yml
    ```

1. Verify deployment objects.
    ```
    kubectl get all -l app=webapp
    ```

    or    

    ```
    kubectl get deployment -l app=webapp
    kubectl get svc -l app=webapp
    kubectl get pods -l app=webapp
    ```

1. Scale down deployment.
    ```
    kubectl scale deployment/webapp-deployment --replicas=1
    kubectl get pods -l app=webapp
    ```

1. Verify the service.
    ```bash
    curl $(minikube ip):$(kubectl get svc -l app=webapp -o=jsonpath='{.items[0].spec.ports[0].nodePort}')
    ```

1. Cleanup
    ```
    kubectl delete deployment webapp-deployment
    ```

    or

    ```bash
    kubectl delete all -l app=webapp
    ```

1. Verify cleanup.
    ```
    kubectl get all -l app=webapp
    ```

1. Reset environment.
    ```bash
    eval $(minikube docker-env -u)
    ```
