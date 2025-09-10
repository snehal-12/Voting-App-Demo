Demonstrate pods,services and deployments creation for a voting app. 
The images for the application are pulled from dockersamples/examplevotingapp.

[Used Minikube, Docker Desktop, Visual studio code].

Minikube - single node cluster on local machine. Both the control plane and worker components run on same VM or container on local machine.
Hence,the 'NodePort' is exposed on the Minikube VM's network, not on your host machine's network.

To access the service from your host machine, you need a way to tunnel traffic from your host to the Minikube VM. The 'minikube service 'service-name' --url' command handles this for you by automatically creating a tunnel and providing the correct URL.

NodePort Service: A NodePort service in Kubernetes exposes a service on a static port on each node's IP address. In a multi-node cluster, this works because all nodes are on the same network. However, in Minikube's isolated environment, the "node" is the VM or container itself, so its IP address is not directly accessible from your host.

The minikube service Command: This command automates the process of creating a secure network tunnel from your host machine to the Minikube VM. It forwards traffic from a local port on your host to the specified node port on the Minikube VM, giving you a convenient URL to access your service. It's essentially a temporary port-forwarding mechanism tailored for Minikube's specific architecture.
