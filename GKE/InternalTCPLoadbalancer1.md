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

GKESubsetting:

1. GKE improves the scalability of internal load balancer services because it uses GCE_VM_IP network endpoint groups (NEGs) as backends instead of instance groups. 
2. When GKE subsetting is enabled, GKE creates one NEG per compute zone per internal loadbalancer service.
3. The member endpoints in the NEG are the IP addresses of nodes that have at least one of the Service's serving pods. 