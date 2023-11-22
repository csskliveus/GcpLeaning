https://cloud.google.com/kubernetes-engine/docs/concepts/service-load-balancer#neg_backends


1. When GKE subsetting is enabled for a cluster, GKE creates a unique GCE_VM_IP NEG in each zone for each internal LoadBalancer Service. 
2. Unlike instance groups, nodes can be members of more than one load-balanced GCE_VM_IP NEG. 
3. The externalTrafficPolicy of the Service and the number of nodes in the cluster determine which nodes are added as endpoints to the Service's GCE_VM_IP NEG(s).

![image](https://github.com/csskliveus/GcpLeaning/assets/53880733/234e50aa-681c-4ebb-b42e-0249c3b8a805)


externalTrafficPolicy is a standard service option. that defines how and whether traffic incoming to a GKE node is load balanced.

'Cluster' is the default policy
'Local' is often used to preserve the source IP of traffic coming into a cluster node.

Local effectively disables load balancing on the cluster node so that traffic that is received by a local pod sees the original source IP.


Cluster Policy:
  Traffic will be load balanced to any healthy GKE node in the cluster and then the kube-proxy will send it to a node with pod. 

Local Policy:
  Nodes that do not have one of the backend Pods appear as unhealthy to the TCP/UDP load balancer.
  Traffic will only be sent to one of the remaining healthy cluster nodes which has the pod.
  Traffic is not routed again by kube-proxy and instead will be sent directly to the local Pod with its IP header intact.
  
