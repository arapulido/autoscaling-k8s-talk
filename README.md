# Autoscaling Kubernetes Workloads Talk demos

To set up the demo environment you will need a Kubernetes cluster, ideally +1.16

```
kubectl create ns fake-traffic
kubectl create secret generic datadog-secret --from-literal=api-key=<YOUR_API_KEY>
kubectl create secret generic datadog-app-key --from-literal app-key=<YOUR_APP_KEY>
kubectl create secret generic datadog-auth-token --from-literal token="<ThirtyX2XcharactersXlongXtoken>"

git clone https://github.com/arapulido/autoscaling-k8s-talk
cd autoscaling-k8s-talk

kubectl apply -f kube-state-metrics
kubectl apply -f metrics-server
kubectl apply -f ecommerce-app
kubectl apply -f vertical-pod-autoscaler
kubectl apply -f datadog
```


