Gateway in GKE

Gateway API is an open source standard for service networking.

  Role-oriented
  Portable
  Expressive

Gateway API resources

The Gateway API is a role-oriented resource model, designed for the personas who interact with Kubernetes networking.

Gatewayclass:
 Defines a cluster-scoped resource that's a template for creating load balancers in cluster. 

Gateway:
 Defines where and how the load balancers listen for traffic.
 GKE creates load balancers that implement the configuration defined in the gateway resource.

HTTPRoute:
 Defines protocol-specific routes for routing requests from gateway to kubernetes services.

Policy:
 Defines a set of implementation-specific characteristics of a Gateway resource. You can attach a policy to a Gateway, a Route, or a Kubernetes Service.


GatewayClass

1. A GatewayClass is a resource that defines a template for HTTP(S) (level 7) load balancers in a Kubernetes cluster. 
2. GKE provides GatewayClasses as cluster-scoped resources. 
3. Cluster operators specify a GatewayClass when creating Gateways in their clusters.


GatewayClass name	Description
gke-l7-global-external-managed	Global external Application Load Balancer(s) built on the global external Application Load Balancer
gke-l7-regional-external-managed	Regional external Application Load Balancer(s) built on the regional external Application Load Balancer
gke-l7-rilb	Internal Application Load Balancer(s) built on the internal Application Load Balancer
gke-l7-gxlb	Global external Application Load Balancer(s) built on the classic Application Load Balancer
gke-l7-global-external-managed-mc	Multi-cluster Global external Application Load Balancer(s) built on the global external Application Load Balancer
gke-l7-regional-external-managed-mc	Multi-cluster Regional external Application Load Balancer(s) built on the global external Application Load Balancer
gke-l7-rilb-mc	Multi-cluster Internal Application Load Balancer(s) built on the internal Application Load Balancer
gke-l7-gxlb-mc	Multi-cluster Global external Application Load Balancer(s) built on the classic Application Load Balancer
gke-td	Multi-cluster Traffic Director service mesh
asm-l7-gxlb	Global external Application Load Balancer(s) built on Anthos Service Mesh


Gateway ownership and usage patterns

Gateway and Route resources provide flexibility in how they are owned and deployed with in an organization. 
 
  1. Self-managed gateway
  2. Plaform managed gateway per Namespace
  3. Shared gateway per cluster

GKE Gateway controller
The GKE Gateway controller is Google's implementation of the Gateway API for Cloud Load Balancing. Similar to the GKE Ingress controller, the Gateway controller watches a Kubernetes API for Gateway API resources and reconciles Cloud Load Balancing resources to implement the networking behavior specified by the Gateway resources.

There are two versions of the GKE Gateway controller:

Single-cluster: manages single-cluster Gateways for a single GKE cluster.
Multi-cluster: manages multi-cluster Gateways for one or more GKE clusters.