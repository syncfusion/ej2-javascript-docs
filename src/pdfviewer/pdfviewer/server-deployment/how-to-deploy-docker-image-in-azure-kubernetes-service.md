---
title: "azure kubernetes service"
component: "PDF Viewer"
description: "Learn about deploy the Web API controller docker image in Azure Kubernetes Service"
---

# Deploy pdfviewer-server container in Azure Kubernetes Service

## Prerequisites

* Have [`Azure account`](https://azure.microsoft.com/en-gb/) and [`Azure CLI`](https://docs.microsoft.com/en-us/cli/azure/?view=azure-cli-latest) setup in your environment.

* Run the following command to open the Azure login page. Sign into your [`Microsoft Azure account`](https://azure.microsoft.com/en-gb/).

```azurecli
az login
```

**Step 1:** Create a resource group.

Create a resource group using the [`az group create`](https://docs.microsoft.com/en-us/cli/azure/group#az-group-create) command.

The following example creates a resource group named pdfviewerresourcegroup in the eastus location.

```azurecli
az group create --name pdfviewerresourcegroup --location "East US"
```

**Step 2:** Create AKS cluster.

Use the [`az aks create`](https://docs.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest#az-aks-create) command to create an AKS cluster. The following example creates a cluster named pdfviewercluster with one node.

```azurecli
az aks create --resource-group pdfviewerresourcegroup --name pdfviewercluster --node-count 1
```

**Step 3:** Connect to the cluster.

Install the [`kubectl`](https://kubernetes.io/docs/reference/kubectl/kubectl/) into the workspace using the following command.

```azurecli
az aks install-cli
```

To configure kubectl to connect to your Kubernetes cluster, use the [`az aks get-credentials`](https://docs.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) command. This command downloads credentials and configures the Kubernetes CLI to use them.

```azurecli
az aks get-credentials --resource-group pdfviewerresourcegroup --name pdfviewercluster
```

**Step 4:** Create services and deployments.

[`Kubernetes Services`](https://kubernetes.io/docs/concepts/services-networking/service/) and [`Deployments`](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) can be configured in a file. To run the PDF Viewer server, you have to define a Service and a Deployment pdfviewerserver. To do this, create the pdfviewer-server.yaml file in the current directory using the following code.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: pdfviewerserver
  name: pdfviewerserver
spec:
  replicas: 1
  selector:
    matchLabels:
      app: pdfviewerserver
  strategy: {}
  template:
    metadata:
      labels:
        app: pdfviewerserver
    spec:
      containers:
      - image: syncfusion/pdfviewerserver:latest
        name: pdfviewerserver
        ports:
        - containerPort: 80
        env:
        - name: SYNCFUSION_LICENSE_KEY
          value: "YOUR_LICENSE_KEY"
---
apiVersion: v1
kind: Service
metadata:
  labels:
    app: pdfviewerserver
  name: pdfviewerserver
spec:
  ports:
  - port: 80
    targetPort: 80
  selector:
    app: pdfviewerserver
  type: LoadBalancer
```

**Step 5:** To create all Services and Deployments needed to run the PDF Viewer server, execute the following.

```console
kubectl create -f ./pdfviewer-server.yaml
```

Run the following command to get the Kubernetes cluster deployed with service details and copy the external IP address of the PDF Viewer service.

```console
kubectl get all
```

Browse the copied external IP address and navigate to the PDF Viewer Web API control `http://<external-ip>/api/pdfviewer`. It returns the default get method response.

**Step 6:** Append the Kubernetes service running the URL `http://<external-ip>/api/pdfviewer` to the service URL in the client-side PDF Viewer control. For more information about how to get started with the PDF Viewer control, refer to this [`getting started page`](https://ej2.syncfusion.com/javascript/documentation/pdfviewer/getting-started/?).

For more details about the Azure Kubernetes service, please look deeper into [`Microsoft Azure Kubernetes Service`](https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough) for a production-ready setup.