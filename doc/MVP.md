## ArgoCD Setup and Demo Instructions

This readme provides instructions for setting up and demonstrating the automatic synchronization of a product's Git repository with ArgoCD. The Git repository for the product can be found at: [https://github.com/den-vasyliev/go-demo-app](https://github.com/den-vasyliev/go-demo-app).

### Prerequisites

Before proceeding with the setup, make sure you have the following:

1. A Kubernetes cluster up and running.
2. ArgoCD installed and accessible in your cluster.

### Setup Instructions

1. Create an application in ArgoCD to track the Git repository of the product:
   - Access the ArgoCD UI or use the ArgoCD CLI.
   - Create a new application.
   - Provide a name for the application.
   - Configure the Git repository URL to be tracked: [https://github.com/den-vasyliev/go-demo-app](https://github.com/den-vasyliev/go-demo-app).
   - Enable automatic synchronization to ensure changes are synced.

2. Once ArgoCD is successfully set up, a full cycle to demonstrate how ArgoCD automatically tracks and synchronizes changes from the Git repository to the Kubernetes cluster is initiated:


![Image](../.data/demo-3.gif)