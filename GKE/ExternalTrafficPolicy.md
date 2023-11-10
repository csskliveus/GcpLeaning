https://cloud.google.com/kubernetes-engine/docs/concepts/service-load-balancer#neg_backends


1. When GKE subsetting is enabled for a cluster, GKE creates a unique GCE_VM_IP NEG in each zone for each internal LoadBalancer Service. 
2. Unlike instance groups, nodes can be members of more than one load-balanced GCE_VM_IP NEG. 
3. The externalTrafficPolicy of the Service and the number of nodes in the cluster determine which nodes are added as endpoints to the Service's GCE_VM_IP NEG(s).

![image](https://github.com/csskliveus/GcpLeaning/assets/53880733/234e50aa-681c-4ebb-b42e-0249c3b8a805)
