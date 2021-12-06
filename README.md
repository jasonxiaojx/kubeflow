# KubeFlow Notes/Docs
  This includes some notes and information found during the deployment process of KubeFlow with AKS.

## Installation Documentation: [Link to Installation Docs](https://www.kubeflow.org/docs/distributions/azure/deploy/install-kubeflow/)
### Notes regarding installation

  1. Installing kfctl locally using darwin open source package: [Package Link](https://github.com/kubeflow/kfctl/releases/tag/v1.2.0)
  2. Start kubernetes cluster, get credentials first. 
  3. Follow the steps to eventually run kfctl in an empty directory. This will trigger a multiple minute installation process.
  4. After that, you will be able to see your kubernetes processes using the command: **kubectl get all -n kubeflow**
  5. Forward it to a local host port using: **kubectl port-forward** pod-name locahost-port:pod-port *(replace pod-name localhost-port and pod-port)*
  6. Now you can open http://localhost:localhost-port in your browser *(replace localhost-port)*
  7. It will lead to a KubeFlow dashboard, and if you see a namespace definition page instead of a dashboard it is because you didn't previously have a namespace. 
  8. You can create a KubeFlow Jupyter notebook, which is mounted on AKS by creating a notebook server.

## Provisioning GPU CPU and Memory:
1. If you request 10 core CPU, it will try to look for a 10 core CPU VM.
	1. In the scenario that you only had a node pool with 4-core CPUs. You would need to go into your portal -> node pools and create a new node pool with the specific cored CPUs.
2. Provisioning GPU:
	1. Need to enable GPU in node pools first for it to work.
		1. In preview. [Link to preview documentation](https://docs.microsoft.com/en-us/azure/aks/gpu-cluster#update-your-cluster-to-use-the-aks-gpu-image-preview)

## Other Notes:
1. CPU + Memory specs for Jupyter notebook refer to the request for a single pod in the cluster. Make sure you have a single node which can handle the full requirements
2. Recommend enabling auto-scaling for each node pool

