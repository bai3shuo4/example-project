# Shift Convert Command

## OpenShift Template Processing

If you don't have the rendered OpenShift YAML files, you can use the following command to process the template with all parameters:

```bash
# Process the template with all parameters
oc process -f example-template.yaml --local \
  -p APP_NAME=example-app \
  -p NAMESPACE=default \
  -p REPLICAS=2 \
  -p IMAGE_NAME=registry.tce.com/raphaelbai/nginx-example \
  -p IMAGE_TAG=v2 \
  -p CONTAINER_PORT=80 \
  -p SERVICE_PORT=80 \
  -p ROUTE_HOST=example.local \
  -p CONFIG_VALUE="This is a sample config value." \
  -p SECRET_USERNAME=c2VjcmV0LXVzZXI= \
  -p SECRET_PASSWORD=c2VjcmV0LXBhc3N3b3Jk
```

This command will process the template and generate the necessary Kubernetes resources with the specified parameters.

### Splitting Combined YAML Files

If the OpenShift template processing outputs all resources into a single YAML file, you can use the `split_yaml.sh` script to split it into individual files:

```bash
# Split the combined YAML file into separate files
./split_yaml.sh combined-resources.yaml ./split-resources/

# The script will create individual files for each resource in the specified directory
```

The `shift convert` command converts OpenShift resources to Kubernetes native YAML format.

## Basic Usage

```bash
shift convert -i yaml -o yaml <source_path> <output_path>
```

## Example

Convert OpenShift resources to Kubernetes YAML format:

```bash
# Directory structure
openshift-resources/
├── app1-deployment.yaml
├── app2-deployment.yaml
├── app1-service.yaml
├── app2-service.yaml
├── app-route.yaml
└── app-config.yaml

# Run the conversion
shift convert -i yaml -o yaml ./openshift-resources/ ./kubernetes-resources/

# Output directory structure
kubernetes-resources/
├── app1-deployment.yaml
├── app2-deployment.yaml
├── app1-service.yaml
├── app2-service.yaml
├── app-route.yaml
└── app-config.yaml
```

This will:
- Read all YAML files from the `openshift-resources` directory
- Convert them to Kubernetes native format (OpenShift Route will be converted to Kubernetes Ingress)
- Save the converted resources in the `kubernetes-resources` directory 