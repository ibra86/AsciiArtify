Here's a README based on the provided instructions:

# ArgoCD Installation

This guide outlines the steps to install ArgoCD using the k3d Kubernetes distribution.

## Prerequisites

- Docker installed
- k3d installed

## Installation Steps

1. Check existing k3d clusters:
    ```bash
    k3d cluster list
    ```

2. Create a new k3d cluster named "argo":
    ```bash
    k3d cluster create argo
    ```

3. Alias `kubectl` as `k` (optional):
    ```bash
    alias k=kubectl
    ```

4. Verify cluster information:
    ```bash
    k cluster-info
    ```

5. Create a new namespace for ArgoCD:
    ```bash
    k create ns argocd
    ```

6. Apply the ArgoCD installation manifest:
    ```bash
    k apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
    ```

7. Check the status of deployed resources:
    ```bash
    k get all -n argocd
    ```

8. Check the status of ArgoCD pods:
    ```bash
    k get po -n argocd
    ```

9. Port forward ArgoCD server to local machine:
    ```bash
    kubectl port-forward svc/argocd-server -n argocd 8080:443 &
    ```

10. Access ArgoCD Web UI by opening this URL in your browser: `https://127.0.0.1:8080/`

11. Retrieve the initial admin password for ArgoCD:
    ```bash
    k -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
    ```

12. To stop the port forwarding, find the process ID and kill it:
    ```bash
    lsof -i :8080
    kill <process_id>
    ```



## Cleanup

To remove the k3d cluster and associated resources, you can use the following command:
```bash
k3d cluster delete argo
```

![Image](../.data/demo-2.gif)