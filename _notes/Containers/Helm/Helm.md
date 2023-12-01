[[Index]]
## Helm Commands/Tutorial

In this article, we will go through a step-by-step guide on how to create Helm chart and discuss its structure components and best practices.

If you want to learn helm chart basics and get hands-on with helm charts, you will love this guide.

##### Table of Contents

1.  [Prerequisites](https://devopscube.com/create-helm-chart/#prerequisites)
2.  [What is Helm Chart?](https://devopscube.com/create-helm-chart/#what-is-helm-chart)
3.  [Helm Chart Structure](https://devopscube.com/create-helm-chart/#helm-chart-structure)
4.  [Helm Chart Tutorial GitHub Repo](https://devopscube.com/create-helm-chart/#helm-chart-tutorial-github-repo)
5.  [Create Helm Chart From Scratch](https://devopscube.com/create-helm-chart/#create-helm-chart-from-scratch)
6.  [Validate the Helm Chart](https://devopscube.com/create-helm-chart/#validate-the-helm-chart)
7.  [Deploy the Helm Chart](https://devopscube.com/create-helm-chart/#deploy-the-helm-chart)
8.  [Helm Upgrade & Rollback](https://devopscube.com/create-helm-chart/#helm-upgrade-rollback)
9.  [Uninstall The Helm Release](https://devopscube.com/create-helm-chart/#uninstall-the-helm-release)
10.  [Debugging Helm Charts](https://devopscube.com/create-helm-chart/#debugging-helm-charts)
11.  [Helm Chart Possible Errors](https://devopscube.com/create-helm-chart/#helm-chart-possible-errors)
12.  [Helm Charts Best Practices](https://devopscube.com/create-helm-chart/#helm-charts-best-practices)
13.  [Conclusion](https://devopscube.com/create-helm-chart/#conclusion)

## Prerequisites

To get started with helm charts, you need to have the following.

1.  A working [Kubernetes cluster](https://devopscube.com/setup-kubernetes-cluster-kubeadm/)
2.  [Helm installed](https://devopscube.com/install-configure-helm-kubernetes/) on your workstation
3.  A valid [kubeconfig](https://devopscube.com/kubernetes-kubeconfig-file/) to connect to the cluster
4.  Working [knowledge of Kubernetes](https://devopscube.com/kubernetes-tutorials-beginners/) and YAML.

## What is Helm Chart?

For the purpose of explanation, I am choosing a very basic example of a website frontend deployment using Nginx on Kubernetes

Let’s assume you have four different environments in your project. Dev, QA, Staging, and Prod. Each environment will have different parameters for Nginx deployment. For example,

1.  In Dev and QA you might need only one replica.
2.  In staging and production, you will have more replicas with pod autoscaling.
3.  The ingress routing rules will be different in each environment.
4.  The config and secrets will be different for each environment.

Because of the change in configs and deployment parameters for each environment, you need to maintain different Nginx deployment files for each environment. Or you will have a single deployment file and you will need to write custom shell or python scripts to replace values based on the environment. But it is not a scalable approach. Here is where the helm chart comes into the picture.




![][assets/helm1.png] 

Helm charts are a combination of [Kubernetes YAML manifest](https://devopscube.com/create-kubernetes-yaml/) templates and helm-specific files. You can call it a helm package. Since the Kubernetes YAML manifest can be templated, you don’t have to maintain multiple helm charts of different environments. Helm uses the [go templating engine](https://pkg.go.dev/text/template) for the templating functionality.

You just need to have a single helm chart and you can modify the deployment parameters of each environment by just changing a single values file. Helm will take care of applying the values to the templates. We will learn more about it practically in the next sections.

At a high level, Helm Charts reduce the complexity and kubernetes manifest redundancy of each environment `(dev, uat, cug, prod)` with only one template.

## Helm Chart Structure

To understand the Helm chart, let’s take an example of Nginx deployment. To deploy Nginx on Kubernetes, typically you would have the following YAML files.

```
nginx-deployment
    ├── configmap.yaml
    ├── deployment.yaml
    ├── ingress.yaml
    └── service.yaml
```

Now if we create a Helm Chart for the above Nginx deployment, it will have the following directory structure.

```
nginx-chart/
|-- Chart.yaml
|-- charts
|-- templates
|   |-- NOTES.txt
|   |-- _helpers.tpl
|   |-- deployment.yaml
|   |-- configmap.yaml
|   |-- ingress.yaml
|   |-- service.yaml
|   `-- tests
|       `-- test-connection.yaml
`-- values.yaml
```

As you can see, the deployment YAML files are part of the template directory (highlighted in bold) and there are helm-specific files and folders. Let’s look at each file and directory inside a helm chart and understand its importance.

1.  **.helmignore:** It is used to define all the files which we don’t want to include in the helm chart. It works similarly to the `.gitignore` file.
2.  **Chart.yaml:** It contains information about the helm chart like version, name, description, etc.
3.  **values.yaml**: In this file, we define the values for the YAML templates. For example, image name, replica count, HPA values, etc. As we explained earlier only the `values.yaml` file changes in each environment. Also, you can override these values dynamically or at the time of installing the chart using `--values` or `--set` command.
4.  **charts:** We can add another chart’s structure inside this directory if our main charts have some dependency on others. By default this directory is empty.
5.  **templates:** This directory contains all the Kubernetes manifest files that form an application. These manifest files can be templated to access values from **values.yaml** file. Helm creates some default templates for [Kubernetes objects](https://devopscube.com/kubernetes-objects-resources/) like deployment.yaml, service.yaml etc, which we can use directly, modify, or override with our files.
6.  **templates/NOTES.txt:** This is a plaintext file that gets printed out after the chart is successfully deployed. 
7.  **templates/\_helpers.tpl:** That file contains several methods and sub-template. These files are not rendered to Kubernetes object definitions but are available everywhere within other chart templates for use. 
8.  **templates/tests/:** We can define tests in our charts to validate that your chart works as expected when it is installed. 

## Helm Chart Tutorial GitHub Repo

The example helm chart and manifests used in this guide are hosted on the [Helm Chart Github repo](https://github.com/techiescamp/helm-tutorial). You can clone it and use it to follow along with the guide.

```
git clone https://github.com/techiescamp/helm-tutorial.git
```

## Create Helm Chart From Scratch

To get hands-on with helm chart creation, let’s **create an Nginx helm chart** from scratch.

Execute the following command to create the chart boilerplate. It creates a chart with the name `nginx-chart` with default files and folders.

```
helm create nginx-chart
```

If you check the created chart, it will have the following files and directories.

```
nginx-chart
│   ├── Chart.yaml
│   ├── charts
│   ├── templates
│   │   ├── NOTES.txt
│   │   ├── _helpers.tpl
│   │   ├── deployment.yaml
│   │   ├── hpa.yaml
│   │   ├── ingress.yaml
│   │   ├── service.yaml
│   │   ├── serviceaccount.yaml
│   │   └── tests
│   │       └── test-connection.yaml
│   └── values.yaml
```

Let’s cd into the generated chart directory.

```
cd nginx-chart
```

We’ll **edit the files one by one** according to our deployment requirements.

#### Chart.yaml

As mentioned above, we put the details of our chart in `Chart.yaml` file. Replace the default contents of `chart.yaml` with the following.

```
apiVersion: v2
name: nginx-chart
description: My First Helm Chart
type: application
version: 0.1.0
appVersion: "1.0.0"
maintainers:
- email: contact@devopscube.com
  name: devopscube
```

1.  **apiVersion**: This denotes the chart API version. v2 is for Helm 3 and v1 is for previous versions.
2.  **name:** Denotes the name of the chart.
3.  **description:** Denotes the description of the helm chart.
4.  **Type**: The chart type can be either ‘**application**’ or ‘**library**’. Application charts are what you deploy on Kubernetes. Library charts are re-usable charts that can be used with other charts. A similar concept of libraries in programming.
5.  **Version**: This denotes the chart version. 
6.  **appVersion**: This denotes the version number of our application (Nginx). 
7.  **maintainers:** Information about the owner of the chart.

We should increment the `version` and `appVersion` each time we make changes to the application. There are some other fields also like dependencies, icons, etc. 

### templates

There are multiple files in `templates` directory created by helm. In our case, we will work on simple Kubernetes Nginx deployment.

Let’s remove all default files from the template directory.

```
rm -rf templates/*
```

We will add our Nginx YAML files and change them to the template for better understanding.

Create a `deployment.yaml` file and copy the following contents.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: "nginx:1.16.0"
          imagePullPolicy: IfNotPresent
          ports:
            - name: http
              containerPort: 80
              protocol: TCP
```

If you see the above YAML file, the values are static. The idea of a helm chart is to template the YAML files so that we can reuse them in multiple environments by dynamically assigning values to them.

To template a value, all you need to do is add the **object parameter** inside curly braces as shown below. It is called a **template directive** and the syntax is specific to the **Go templating**

```
{{ .Object.Parameter }}
```

First Let’s understand what is an Object. Following are the three Objects we are going to use in this example.

1.  **Release**: Every helm chart will be deployed with a release name. If you want to use the release name or access **release-related dynamic values** inside the template, you can use the release object.
2.  **Chart**: If you want to use any values you mentioned in the **chart.yaml**, you can use the chart object.
3.  **Values**: All parameters inside **values.yaml** file can be accessed using the Values object.

To know more about supported Objects check the [Helm Builtin Object](https://helm.sh/docs/chart_template_guide/builtin_objects/) document.

The following image shows how the built-in objects are getting substituted inside a template.

[! [helm template directive substitution workflow] (assets/helm/helm2.png)] 



First, you need to figure out what values could change or what you want to templatize. I am choosing **name**, **replicas, container name, image and imagePullPolicy** which I have highlighter in the YAML file in bold.

1.  **name:** `name: {{ .Release.Name }}-nginx` : We need to change the deployment name every time as Helm does not allow us to install releases with the same name. So we will templatize the name of the deployment with the release name and interpolate **\-nginx** along with it. Now if we create a release using the name **frontend**, the deployment name will be **frontend-nginx**. This way, we will have guaranteed unique names.
2.  **container name**: `{{ .Chart.Name }}`: For the container name, we will use the Chart object and use the chart name from the **chart.yaml** as the container name.
3.  **Replicas:** `{{ .Values.replicaCount }}` We will access the replica value from the **values.yaml** file.
4.  **image:** `"{{ .Values.image.repository }}:{{ .Values.image.tag }}"` Here we are using multiple template directives in a single line and accessing the repository and tag information under the image key from the Values file.

Similarly, you can templatize the required values in the YAML file.

Here is our final **`deployment.yaml`** file after applying the templates. The templated part is highlighted in bold. Replace the deployment file contents with the following.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ .Release.Name }}-nginx
  labels:
    app: nginx
spec:
  replicas: {{ .Values.replicaCount }}
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: {{ .Chart.Name }}
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.pullPolicy }}
          ports:
            - name: http
              containerPort: 80
              protocol: TCP
```

Create `**service.yaml**` file and copy the following contents.

```
apiVersion: v1
kind: Service
metadata:
  name: {{ .Release.Name }}-service
spec:
  selector:
    app.kubernetes.io/instance: {{ .Release.Name }}
  type: {{ .Values.service.type }}
  ports:
    - protocol: {{ .Values.service.protocol | default "TCP" }}
      port: {{ .Values.service.port }}
      targetPort: {{ .Values.service.targetPort }}
```

In the **protocol template directive**, you can see a pipe `( | )` . It is used to define the default value of the protocol as TCP. So that means we won’t define the protocol value in **`values.yaml`** file or if it is empty, it will take TCP as a value for protocol.

Create a **`configmap.yaml`** and add the following contents to it. Here we are replacing the default Nginx **index.html** page with a custom HTML page. Also, we added a template directive to replace the environment name in HTML.

```
apiVersion: v1
kind: ConfigMap
metadata:
  name: {{ .Release.Name }}-index-html-configmap
  namespace: default
data:
  index.html: |
    <html>
    <h1>Welcome</h1>
    </br>
    <h1>Hi! I got deployed in {{ .Values.env.name }} Environment using Helm Chart </h1>
    </html
```

### values.yaml

The `values.yaml` file contains all the values that need to be substituted in the template directives we used in the templates. For example, `deployment.yaml` template contains template directive to get the image repository, tag, and pullPolicy from the **`values.yaml`** file. If you check the following **`values.yaml`** file, we have repository, tag, and pullPolicy key-value pairs nested under the image key. That is the reason we used **`Values.image.repository`**

Now, replace the default **`values.yaml`** content with the following.

```
replicaCount: 2

image:
  repository: nginx
  tag: "1.16.0"
  pullPolicy: IfNotPresent

service:
  name: nginx-service
  type: ClusterIP
  port: 80
  targetPort: 9000

env:
  name: dev
```

Now we have the Nginx helm chart ready and the final helm chart structure looks like the following.

```
nginx-chart
├── Chart.yaml
├── charts
├── templates
│   ├── configmap.yaml
│   ├── deployment.yaml
│   └── service.yaml
└── values.yaml
```

## Validate the Helm Chart

Now to make sure that our chart is valid and, all the indentations are fine, we can run the below command. Ensure you are inside the chart directory.

```
helm lint .
```

If you are executing it from outside the **`nginx-chart`** directory, provide the full path of **`nginx-chart`**

```
helm lint /path/to/nginx-chart
```

If there will be no error or issue, it will show this result

```
==> Linting ./nginx
[INFO] Chart.yaml: icon is recommended

1 chart(s) linted, 0 chart(s) failed
```

To validate if the values are getting substituted in the templates, you can render the templated YAML files with the values using the following command. It will generate and display all the manifest files with the substituted values.

```
helm template .
```

We can also use `--dry-run` command to check. This will pretend to install the chart to the cluster and if there will be some issue it will show the error.

```
helm install --dry-run my-release nginx-chart
```

If everything is good, then you will see the manifest output that would get deployed into the cluster.

## Deploy the Helm Chart

When you deploy the chart, Helm will read the chart and configuration values from the `values.yaml` file and generates the manifest files. Then it will send these files to the Kubernetes API server, and Kubernetes will create the requested resources in the cluster.

Now we are ready to install the chart.

Execute the following command where `**nginx-release**` is release name and `**nginx-chart**` is the chart name. It installs **`nginx-chart`** in the default namespace

```
helm install frontend nginx-chart
```

You will see the output as shown below.

```
NAME: frontend
LAST DEPLOYED: Tue Dec 13 10:15:56 2022
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
```

Now you can check the release list using this command:

```
helm list
```

Run the kubectl commands to check the deployment, services, and pods.

```
kubectl get deployment
kubectl get services
kubectl get configmap
kubectl get pods
```

We can see the deployment **`frontend-nginx`**, **`nginx-service`** and pods are up and running as shown below.

[! [validate helm chart deployment] (assets/helm/helm3.png)] 


We discussed how a single helm chart can be used for multiple environments using different **`values.yaml`** files. To install a helm chart with external `**values.yaml**` file, you can use the following command with the `--values` flag and path of the values file.

```
helm install frontend nginx-chart --values env/prod-values.yaml
```

When you have Helm as part of your CI/CD pipeline, you can write custom logic to pass the required values file depending on the environment.

## Helm Upgrade & Rollback

Now suppose you want to modify the chart and install the updated version, we can use the below command:

```
helm upgrade frontend nginx-chart
```

For example, we have changed the replicas from 2 to 1. You can see the revision number is 2 and only 1 pod is running.

[! [helm chart upgrade] (assets/helm/helm4.png)] 

Now if we want to roll back the changes which we have just done and deploy the previous one again, we can use the rollback command to do that.

```
helm rollback frontend
```

The above command will roll back the helm release to the previous one.

[! [helm chart rollback] (assets/helm/helm5.png)] 


After the rollback, we can see 2 pods are running again. Note that helm takes the rollback as a new revision, that’s why we’re getting the revision as 3.

If we want to roll back to the specific version we can put the revision number like this.

```
helm rollback <release-name> <revision-number>
```

For example,

```
helm rollback frontend 2
```

## Uninstall The Helm Release

To uninstall the helm release use uninstall command. It will remove all of the resources associated with the last release of the chart.

```
helm uninstall frontend
```

We can package the chart and deploy it to Github, S3, or any other platform.

```
helm package frontend
```

## Debugging Helm Charts

We can use the following commands to debug the helm charts and templates.

1.  **`helm lint:`** This command takes a path to a chart and runs a series of tests to verify that the chart is well-formed.
2.  **`helm get values:`** This command will output the release values installed to the cluster.
3.  **`helm install --dry-run:`** Using this function we can check all the resource manifests and ensure that all the templated are working fine.
4.  **`helm get manifest:`** This command will output the manifests that are running in the cluster.
5.  **`helm diff:`** It will output the differences between the two revisions.

```
helm diff revision nginx-chart 1 2
```

## Helm Chart Possible Errors

If you try to install an existing helm package, you will get the following error.

```
Error: INSTALLATION FAILED: cannot re-use a name that is still in use
```

To update or upgrade the release, you need to run the upgrade command.

If you try to install a chart from a different location without giving the absolute path of the chart you will get the following error.

```
Error: non-absolute URLs should be in form of repo_name/path_to_chart
```

To rectify this, you should execute the helm command from the directory where you have the chart or provide the absolute path or relative path of the chart directory.

## Helm Charts Best Practices

Following are some of the best practices to be followed when developing a helm chart.

1.  Document your chart by adding comments and a **README** file as documentation is essential for ensuring maintainable Helm charts.
2.  We should name the Kubernetes manifest files after the Kind of object i.e deployment, service, secret, ingress, etc.
3.  Put the chart name in lowercase only and if it has more than a word then separate out with hyphens (-)
4.  In values.yaml file field name should be in lowercase.
5.  Always wrap the string values between quote signs.
6.  Use Helm version 3 for simpler and more secure releases. Check [this document](https://helm.sh/docs/topics/v2_v3_migration/) for more details

## Conclusion

To summarize,

1.  We discussed the Helm Chart and its structure in detail.
2.  We created a helm chart from scratch and deployed it.
3.  Also learned how to upgrade, roll back, and uninstall it.

Helm is a very useful package manager for Kubernetes. When you have different environments with custom deployment requirements, helm provides a great way to templatize kubernetes manifests as per our needs.

Helm-specific functionalities like chart dependencies and chart reusability make it one of the good kubernetes tools.

An alternative to Helm is Kustomize. It does not use templating but it uses the concept of overlays. Refer to the [Kustomize tutorial](https://devopscube.com/kustomize-tutorial/) to learn more.

Also, if you check our [learning kubernetes](https://devopscube.com/learn-kubernetes-complete-roadmap/) guide, we have mentioned helm as must learn tool for Kubernetes package management.


## Adding custom Helm chart repositories

```yaml
apiVersion: helm.openshift.io/v1beta1
kind: HelmChartRepository
metadata:
  name: <name>
spec:
 # optional name that might be used by console
 # name: <chart-display-name>
  connectionConfig:
    url: <helm-chart-repository-url>
```

## Example 

```yaml
cat <<EOF | oc apply -f -
apiVersion: helm.openshift.io/v1beta1
kind: HelmChartRepository
metadata:
  name: azure-sample-repo
spec:
  name: azure-sample-repo
  connectionConfig:
    url: https://raw.githubusercontent.com/Azure-Samples/helm-charts/master/docs
EOF
```

## Installing a Helm chart on an OpenShift Container Platform cluster
Prerequisites
You have a running OpenShift Container Platform cluster and you have logged into it.

You have installed Helm.

Procedure
Create a new project:


```bash
$ oc new-project vault
```



Add a repository of Helm charts to your local Helm client:

```bash
$ helm repo add openshift-helm-charts https://charts.openshift.io/
```



Example output

"openshift-helm-charts" has been added to your repositories
Update the repository:

```bash
$ helm repo update
```



## Install an example HashiCorp Vault:

```bash
$ helm install example-vault openshift-helm-charts/hashicorp-vault
```


```bash
Example output

NAME: example-vault
LAST DEPLOYED: Fri Mar 11 12:02:12 2022
NAMESPACE: vault
STATUS: deployed
REVISION: 1
NOTES:
Thank you for installing HashiCorp Vault!
Verify that the chart has installed successfully:
```


```bash
$ helm list
Example output

NAME         	NAMESPACE	REVISION	UPDATED                                	STATUS  	CHART       	APP VERSION
example-vault	vault    	1       	2022-03-11 12:02:12.296226673 +0530 IST	deployed	vault-0.19.0	1.9.2
```

Links: https://devopscube.com/create-helm-chart/ https://github.com/techiescamp/helm-tutorial.git https://github.com/cptmorgan-rh/install-oc-tools 

[[Index]]
