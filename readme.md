

https://github.com/prometheus-operator/kube-prometheus#customizing-kube-prometheus


    jb init
    jb install github.com/prometheus-operator/kube-prometheus/jsonnet/kube-prometheus@release-0.9 
    wget https://raw.githubusercontent.com/prometheus-operator/kube-prometheus/release-0.9/example.jsonnet -O example.jsonnet
    wget https://raw.githubusercontent.com/prometheus-operator/kube-prometheus/release-0.9/build.sh -O build.sh