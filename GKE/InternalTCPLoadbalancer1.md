Load balancer service concepts

Check settings like the 
  1. externalTrafficPolicy 
  2. GKE subsetting 
for L4 internal load balancers determine how the load balancers are configured

Internal Load balancer

If your clients are located in the same VPC network or in a network connected to the cluster's (VPC network), then use an Internal LoadBalancer Service. Internal LoadBalancer Services are implemented by using internal passthrough Network Load Balancers. Clients located in the same VPC network or in a network connected to the cluster's VPC network can access the Service by using the load balancer's IP address.

To create an internal LoadBalancer Service, include one of the following annotations in the metadata.annotations[] of the Service manifest:

networking.gke.io/load-balancer-type: "Internal" (GKE 1.17 and later)
cloud.google.com/load-balancer-type: "Internal" (versions earlier than 1.17)

https://cloud.google.com/kubernetes-engine/docs/how-to/internal-load-balancing

**GKESubsetting:**

1. GKE improves the scalability of internal load balancer services because it uses GCE_VM_IP network endpoint groups (NEGs) as backends instead of instance groups. 
2. When GKE subsetting is enabled, GKE creates one NEG per compute zone per internal loadbalancer service.
3. The member endpoints in the NEG are the IP addresses of nodes that have at least one of the Service's serving pods.
4. GKE subsetting cannot be disabled once it has been enabled.
5. Internal load balancers with custom-mode subnets in addition to auto-mode subnets.

**Node Grouping**
https://cloud.google.com/kubernetes-engine/docs/concepts/service-load-balancer#endpoint-grouping

1. The Service manifest annotations and, for Internal LoadBalancer Service, the status of GKE subsetting determine the resulting Google Cloud load balancer and the type of backends. 
2. Backends for Google Cloud pass-through load balancers identify the network interface (NIC) of the GKE node, not a particular node or Pod IP address.
3. {++ The type of load balancer and backends determine how nodes are grouped into GCE_VM_IP NEGs, instance groups, or target pools. ++}

![image](https://github.com/csskliveus/GcpLeaning/assets/53880733/8ef63faa-aecc-434b-9fbe-a2cb19242773)
