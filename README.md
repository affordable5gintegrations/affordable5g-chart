# affordable5g-chart

Chart for affordable5g

To access the private github's registry/repo, a k8s secret must be created.
Note the '--dry-run'. The following command wont actualy create the secret, but will allow the user to access the docker config json in a base64 string that can be used later (in either `values.yml` or via command line)
```
kubectl create secret docker-registry regcred --docker-server=ghcr.io --docker-username=<username> --docker-password=<password> -n affordable5g -o yaml --dry-run

apiVersion: v1
data:
  .dockerconfigjson: eyJhdXRocyI6eyJnaGNyLmlvIjp7InVzZXJuYW1lIjoiXHUwMDNjdXNlcm5hbWVcdTAwM2UiLCJwYXNzd29yZCI6Ilx1MDAzY3Bhc3N3b3JkXHUwMDNlIiwiYXV0aCI6IlBIVnpaWEp1WVcxbFBqbzhjR0Z6YzNkdmNtUSsifX19
kind: Secret
metadata:
  creationTimestamp: null
  name: regcred
  namespace: affordable5g
type: kubernetes.io/dockerconfigjson
```


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
    --set api.dockerconfigjson="eyJhdXRocyI6eyJnaGNyLmlvIjp7InVzZXJuYW1lIjoiXHUwMDNjdXNlcm5hbWVcdTAwM2UiLCJwYXNzd29yZCI6Ilx1MDAzY3Bhc3N3b3JkXHUwMDNlIiwiYXV0aCI6IlBIVnpaWEp1WVcxbFBqbzhjR0Z6YzNkdmNtUSsifX19" \
-n affordable5g .
```

