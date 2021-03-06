# testapp-package

This package provides a test application to validate Knative functionality.

## Components

* testappapp

## Configuration

The following configuration values can be set to customize the testappapp installation.

### Global

| Value | Required/Optional | Description |
|-------|-------------------|-------------|
| `namespace` | Optional | The namespace in which to deploy testappapp. |
| `wildcard_domain` | Required | The wildcard DNS domain in which applications will be exposed.|
| `privileged_clusterrole_name` | Optional | If PSPs are enabled on the cluster, this is the name of the privileged clusterrole that allows our test app to start |


## Usage Example

Just delpoy the package and test it. There should be an `ingress` ready to use in the `namespace` you used. 

## Develop checklist

1. Update your [config.json](./config.json) with the package info
2. Add [overlays](./src/bundle/config/overlays/) and [values](./src/bundle/config/values.yaml)
3. Test your bundle: `ytt --data-values-file src/example-values/minikube.yaml  -f target/bundle/config` providing a sample values file from [example-values](./src/examples-values/)
4. Build your bundle `./hack/build.sh`
5. Add it to the [failk8s-repo](https://github.com/failk8s-packages/failk8s-repo) and publish the new repo and test the package from there, or [test with local files](./target/test)

**NOTE**: `develop` versions will not be image locked and will have a version of 0.0.0+develop to comply with semver.