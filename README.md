# affordable5g-chart

Chart for affordable5g


If manually installing the service, either edit `values.yaml` or add values via command line:
```
helm install affordable5g \
    --set api.env.EDGE_SERVER_ADDRESS="http://192.168.1.1:8080"  \
    --set api.env.EDGE_SERVER_USER="edge_user" \
    --set api.env.EDGE_SERVER_PASSWORD="edge_password" \
    --set api.env.ENVIRONMENT="dev" \
    --set api.env.NETWORK_FUNCTION_ADDRESS="1.1.1.1" \
    --set api.env.NETWORK_FUNCTION_USER="net_user" \
    --set api.env.NETWORK_FUNCTION_PASSWORD="net_password" \
    --set api.env.OSM_USER="osm_user" \
    --set api.env.OSM_PASSWORD="osm_pass" \
    --set api.env.SYSTEM_USER="system_user" \
    --set api.env.SYSTEM_PASSWORD="system_password" \
-n affordable5g .
```

To access the private github's registry/repo, a k8s secret mus be created as follows:
```
kubectl create secret docker-registry regcred --docker-server=ghcr.io --docker-username=<username> --docker-password=<password> -n affordable5g
```
