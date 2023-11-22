Admission controllers gaurd the door to your kubernetes cluster

An admission controller intercepts and processes requests to the kubernetes API prior to persistence of the object, but after the request id authenticated and authorized.

Admission controllers can answer existential questions in the life of a devops:
  1. Is the pod requesting too many resources ?
  2. Are the base images used to spawn the microservice pods secure ? 
  3. What is the priority of this deployment compared to the others ?
  4. Which privileges are currently granted to the service account linked to these pods/deployments ? Do they adhere to the principle of least privilege ?

Some controllers that are present in kubernetes:
1. LimitRanger:
    Manages resource limits and requests.

2. PersistentVolumeClaimResize:
	Implements additional validations for checking incoming PersistentVolumeClaim resize requests.


Webhooks: 

   1. Webhooks acts as an extension to kubernetes admission controllers.
   2. The kubernetes API server will call a registered webhook making it easy to integrate with any third party code. 
   3. 3 admission controllers lets you to expand API functionality. 

     1. ImagePolicyWebhook : to decide if any image should be admitted.
     2. MutatingAdmissionWebhook  : to modify a request.
     3. ValidatingAdmissionWebhook : to decide whether the request should be allowed to run.

