# Deploying to Kubernetes

> NOTE: The provided `config/workload.yaml` file uses the Git URL for this sample. When you want to modify the source, you must push the code to your own Git repository and then update the `spec.source.git` information in the `config/workload.yaml` file.

## Deploying to Kubernetes as a TAP workload with Tanzu CLI

If you make modifications to the source, push these changes to your own Git repository.

When you are done developing your app, you can simply deploy it using:

```
tanzu apps workload apply -f config/workload.yaml
```

If you would like deploy the code from tyour local working directory you can use the following command:

```
tanzu apps workload create spring-petclinic -f config/workload.yaml \
  --local-path . \
  --source-image <REPOSITORY-PREFIX>/spring-petclinic-source \
  --type web
```

## Accessing the app deployed to your cluster

Determine the URL to use for the accessing the app by running:

```
tanzu apps workload get spring-petclinic
```

To access the deployed app use the URL shown under "Workload Knative Services".

This depends on the TAP installation having DNS configured for the Knative ingress.
