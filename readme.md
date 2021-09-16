

https://github.com/prometheus-operator/kube-prometheus#customizing-kube-prometheus


    jb init
    jb install github.com/prometheus-operator/kube-prometheus/jsonnet/kube-prometheus@release-0.9 
    wget https://raw.githubusercontent.com/prometheus-operator/kube-prometheus/release-0.9/example.jsonnet -O example.jsonnet
    wget https://raw.githubusercontent.com/prometheus-operator/kube-prometheus/release-0.9/build.sh -O build.sh
    jb update
    ./build.sh example.jsonnet


    docker run --rm -v $(pwd):$(pwd) --workdir $(pwd) quay.io/coreos/jsonnet-ci jb update
    docker run --rm -v $(pwd):$(pwd) --workdir $(pwd) quay.io/coreos/jsonnet-ci ./build.sh example.jsonnet


Deploying

    kubectl create -f manifests/setup
    until kubectl get servicemonitors --all-namespaces ; do date; sleep 1; echo ""; done
    kubectl create -f manifests/

Tear Down 

    kubectl delete --ignore-not-found=true -f manifests/ -f manifests/setup

Access

    kubectl --namespace monitoring port-forward svc/prometheus-k8s 9090


Deploy resources

    kubectl config get-contexts  
    kubectl config use-context docker-desktop
    kubectl create -f deployments/setup
    kubectl create -n k8s-nginx-example -f deployments
    kubectl delete -n k8s-nginx-example -f deployments

