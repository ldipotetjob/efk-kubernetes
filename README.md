# Logging in Kubernetes with Elasticsearch, Kibana, and Fluentd

## Minikube environment 

Download repo <br/> 
Start minikube cluster <br/>
**minikube start --cpus 4 --memory 8g**

```bash
# create namespaces  
kubectl create namespace logging
# create an elasticsearch deployment and a service to access it   
kubectl create -f kubernetes/elastic.yaml -n logging
# getting url access to elasticsearch 
# minikube service elasticsearch --url -n logging
# checking that elastic search is properly installed 
curl $(minikube service elasticsearch --url -n logging)
# create a kibana deployment and a service to access it   
kubectl create -f kubernetes/kibana.yaml -n logging
# getting url access to kibana in our browser: 
minikube service kibana --url -n logging
# create a fluentd daemonset  
kubectl create -f kubernetes/fluentd-daemonset.yaml
```
deprecated api ref. https://kubernetes.io/blog/2019/07/18/api-deprecations-in-1-16/

Check out the blog post: https://mherman.org/blog/logging-in-kubernetes-with-elasticsearch-Kibana-fluentd/
