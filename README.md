# Task 5: Kubernetes Cluster Deployment with Minikube

## Objective
In this task, I have learned how to build and deploy a Node.js application using Kubernetes on a local Minikube cluster. The steps include setting up Docker, creating Kubernetes YAML files for deployment and services, and deploying the application.

---

## Tools & Technologies
- **Docker**: To create a container image of the Node.js application.
- **Minikube**: To create a local Kubernetes cluster.
- **kubectl**: To interact with Kubernetes and manage the app.
- **Node.js**: For the backend application.

---

## Steps

### 1. **Set Up Docker**
- Built a Docker image for the Node.js app using a `Dockerfile`.
- Pushed the image to Docker Hub (`sppranam/my-node-app:latest`).

### 2. **Set Up Minikube**
- Installed Minikube and started a local Kubernetes cluster using Docker as the driver:
    ```bash
    minikube start --driver=docker
    ```

### 3. **Create Deployment YAML**
- Created a `deployment.yaml` file to define the Node.js app as a Kubernetes deployment.
- The app is set to run with a single replica in the cluster.
  
    ```yaml
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: my-node-app
    spec:
      replicas: 1
      selector:
        matchLabels:
          app: my-node-app
      template:
        metadata:
          labels:
            app: my-node-app
        spec:
          containers:
            - name: my-node-app
              image: sppranam/my-node-app:latest
              ports:
                - containerPort: 3000
    ```

### 4. **Create Service YAML**
- Created a `service.yaml` file to expose the application via a NodePort service on port 3000.
  
    ```yaml
    apiVersion: v1
    kind: Service
    metadata:
      name: my-node-app-service
    spec:
      type: NodePort
      selector:
        app: my-node-app
      ports:
        - protocol: TCP
          port: 3000
          targetPort: 3000
          nodePort: 30036
    ```

### 5. **Deploy App to Kubernetes**
- Applied the `deployment.yaml` and `service.yaml` to the Kubernetes cluster using `kubectl` commands.
  
    ```bash
    kubectl apply -f deployment.yaml
    kubectl apply -f service.yaml
    ```

- Verified the deployment with:

    ```bash
    kubectl get pods
    kubectl get services
    ```

### 6. **Access the App**
- Opened the app using Minikube’s `service` command:

    ```bash
    minikube service my-node-app-service
    ```

- This opened the app in a browser via the URL `http://127.0.0.1:30036`.

### 7. **Scale the Deployment**
- Scaled the deployment to 3 replicas using:

    ```bash
    kubectl scale deployment my-node-app --replicas=3
    ```

- Verified the scaling with:

    ```bash
    kubectl get pods
    ```

### 8. **Check Logs**
- Checked the logs of the running pod with:

    ```bash
    kubectl logs <pod-name>
    ```

---

## Deliverables

- **Kubernetes Files**:
  - `deployment.yaml`
  - `service.yaml`

- **Screenshots**:
  - Pods status (`kubectl get pods`)
  - Services status (`kubectl get services`)
  - Running application in the browser
  - Pod logs

---

## Next Steps
After successfully completing this task, the next step is to dive deeper into Kubernetes features like:

- **Ingress Controllers**
- **ConfigMaps**
- **Secrets Management**
- **Helm Charts**

