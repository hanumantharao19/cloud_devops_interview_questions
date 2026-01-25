## 1. What is Helm?
- Helm is a package manager for Kubernetes that helps you deploy and manage applications easily.

## 2. What is a Helm chart?

- A Helm chart is a collection of YAML files that define a Kubernetes application.

## 3. Why do we use Helm?

- To simplify Kubernetes deployments, manage versions, and reuse configurations.

## 4. What problem does Helm solve?

- It reduces complexity of managing multiple Kubernetes YAML files.

## 5. What is a Helm release?

- A release is a running instance of a Helm chart in a Kubernetes cluster.

## 6. What is Chart.yaml?

- It contains metadata about the chart like name, version, and description.

## 7. What is values.yaml?

- It stores default configuration values for the chart.

## 8. What is templates/ directory?

- It contains Kubernetes manifest templates.

## 9. What is charts/ directory?

- It stores dependent charts (subcharts).

## 10. How do you install a Helm chart?
```
helm install <releasename> <helmchartname>
```
## 11. Command to list Helm releases?
```
helm list
```
## 12. How to uninstall a Helm release?
```
helm uninstall <release-name>
```
## 13. How to upgrade a Helm release?
- helm upgrade is used to update an existing Helm release when there are changes in the chart, configuration values, or application version.
```
helm upgrade <release-name> <chart-path>
```
## 14. How do you override values in Helm, and which method has higher priority?
- You can override Helm values using a values file (-f values.yaml) or directly from the command line using --set.
- When both are used, --set always has higher priority and overrides values from values.yaml.
```
helm install myapp ./my-chart -f values-prod.yaml
```
or
```
helm install myapp ./my-chart --set replicaCount=3
```

## 15. Which templating language does Helm use?
 - Go templating language.

## 16. What is {{ .Values }}?
- Used to access values from values.yaml.

## 17. What is {{ .Release.Name }}?

- Returns the release name.

## 18. What is {{ .Chart.Name }}?

- Returns the chart name.

## 19 Why do we use conditionals in Helm charts, and how do they work?

- Conditionals in Helm charts allow you to enable or disable Kubernetes resources dynamically based on values in values.yaml or parameters passed during installation.

## 20 What are Helm hooks, and how are they used?
- Helm hooks are special annotations in templates that allow you to run Kubernetes resources at specific points in a release lifecycle (e.g., pre-install, post-install, pre-upgrade).

- They are commonly used for tasks like database migrations, validations, or setup jobs, and can fail the installation if the hook job fails.


## 21 What is helm rollback, and why do we use it?
- helm rollback is used to revert a Helm release to a previous working version if a deployment fails or causes issues.
```
- helm rollback <release-name> <revision-number>
```
## 22. How to see release history?
- helm history <release>

## 23. What is a Helm repository?

- A storage location for Helm charts.

## 24. How to add a repo?
- helm repo add

## 25. How to list repos?
- helm repo list

## 26. How to update repos?
- helm repo update

## 27. How does Helm communicate with cluster?

- Using Kubernetes API.

## 28 Does Helm support namespaces, and what happens if you use --create-namespace on an existing namespace?
- Helm supports namespaces using the --namespace flag.
- By adding --create-namespace, Helm will create the namespace if it doesn’t exist. If the namespace already exists, Helm simply uses it and does not throw an error.
```
helm install myapp ./my-chart --namespace dev --create-namespace
```

## 29 Where does Helm store release information, and how is it managed?

- Helm stores release information as Kubernetes Secrets (or ConfigMaps in Helm v2) in the namespace where the release is deployed.
- These secrets contain metadata, manifest templates, and values, which Helm uses for upgrades, rollbacks, and tracking release history.

```
kubectl get secrets -n <namespace> | grep sh.helm.release
```
## 30 What is the purpose of helm lint, and why do we use it?
- helm lint is used to validate the structure, syntax, and best practices of a Helm chart before deployment.
```
helm lint <chart-name>
```
or
```
helm lint <chart-name> -f dev-value.yaml
```
## 31 What is Helm templating, and why do we use it?
- Helm templating is used to create dynamic Kubernetes YAML files using variables and logic instead of hardcoding values.
- It is mainly used to review, debug, or validate the generated manifests before
```
helm template myapp ./my-chart
```
or
```
helm template myapp ./my-chart -f values-dev.yaml
```


## 32 How do you perform a dry-run of a Helm install, and why is it used?
- A dry-run lets you perform a trial run of a Helm install without actually deploying any resources.
- It is used to test templates, values, and manifests before performing a real deployment, helping catch errors early.

```
helm install <release-name> <chart-path> --dry-run
```
## 33. How to check failed releases?
helm list --failed


## 34. How to deploy same app to multiple environments?

- You deploy the same chart using different values files for each environment.
This allows you to customize settings like replica count, resource limits, and URLs without changing the chart itself.

```
# Deploy to dev environment
helm install myapp-dev ./my-chart -f values-dev.yaml

# Deploy to QA environment
helm install myapp-qa ./my-chart -f values-qa.yaml

# Deploy to production
helm install myapp-prod ./my-chart -f values-prod.yaml
```

## 35 What is the purpose of helm get, and how do you use it?
- helm get helps inspect deployed Helm releases, including their values, manifests, hooks, and other details for debugging or auditing.

```
helm get all <release-name>
```

