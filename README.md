
 kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}'
 
 kubectl port-forward -n istio-system $(kubectl get pod -n istio-system -l app=jaeger -o jsonpath='{.items[0].metadata.name}') 16686:16686
 
 kubectl  port-forward  $(kubectl get pod -n istio-system -l app=kiali   -o jsonpath='{.items[0].metadata.name}')   -n istio-system 20001

 kubectl  port-forward  -n istio-system   $(kubectl -n istio-system get pod -l app=grafana    -o jsonpath='{.items[0].metadata.name}') 3000



 kubectl delete gateway mesh-gateway
  
 kubectl delete virtualservice enterprise-vs
 kubectl delete virtualservice corporate-vs
 
 
 kubectl delete DestinationRule enterprise
 kubectl delete DestinationRule corporate
 
 
 kubectl delete -n default service enterprise
 kubectl delete -n default service corporate
 
 
 kubectl delete -n default deployment  enterprise-v1
 kubectl delete -n default deployment  enterprise-v2
 kubectl delete -n default deployment  corporate-v1
 kubectl delete -n default deployment  corporate-v2