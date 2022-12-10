# Chart for webapp deployment

### Run lint command to check for syntax errors
    helm lint .

### Check output of the chart. This is a command to check template output:
    helm template . -f values-override.yaml
  
### Dry run the application (--dry-run --debug). The server will render the template and return a manifest file
    helm install appdeployment --create-namespace --namespace your-namespace --debug --dry-run ./ -f values-override.yaml

### After dry run install the helm chart using the command below
    helm install appdeployment --create-namespace --namespace your-namespace ./ -f values-override.yaml

### Update the chart if any changes are done, creates a new version and renders chart in kubernetes Cluster
    helm upgrade --install appdeployment --create-namespace --namespace assignment-grp2 ./ -f values-override.yaml \
    --set dockerConfigJson=add-docker-config-secret-variable 

### Delete helm chart
    helm uninstall appdeployment -n your-namespace

### Port forward to a desired port
    kubectl port-forward service/{{ include "appdeployment.name" . }}-service 3200:3200 --namespace=your-namespace

### Working with another job
    Added job 2 for webapp

### Added credentials
    Added job 2 for webapp