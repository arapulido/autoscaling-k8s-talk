# Autoscaling Kubernetes Workloads Talk demos

To set up the demo environment you will need a Kubernetes cluster, +1.19

```
kubectl create ns fake-traffic
kubectl create ns ecommerce

git clone https://github.com/arapulido/autoscaling-k8s-talk
cd autoscaling-k8s-talk

kubectl apply -f ecommerce-app
kubectl apply -f metrics-server
kubectl apply -f vertical-pod-autoscaler
kubectl apply -f watermarkpodautoscaler

export DD_API_KEY=<YOUR_DATADOG_API_KEY>
export DD_APP_KEY=<YOUR_DATADOG_APP_KEY>
helm install datadog --set datadog.appKey=$DD_APP_KEY --set datadog.apiKey=$DD_API_KEY datadog/datadog --values datadog/values.yaml
```

For the DatadogMetrics section, you will need to upgrade your Datadog Helm release:

```
helm upgrade datadog --set datadog.appKey=$DD_APP_KEY --set datadog.apiKey=$DD_API_KEY datadog/datadog --values datadog/values-crd.yaml
```


