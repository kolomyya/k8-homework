# k8-homework
I

1.)This cronjob will run one job every 1 minutes (using a cron format for scheduling) and display “Hello” and complete within 10 second
To launch this job you just need to run the following command

###kubectl apply -f cronjob.yaml

2.)To check that the cronjob was created just use 

###kubectl get cronjob

3.)So cronjob was named “homework” based on the metadata.name value. As a default function the job will run, so suspend value is False. There is currently no task running it (we didn’t plan it yet).If we check the status of our scheduled jobs after 1 minutes,  we’ll see that job completed within 10s.That will show the number of times the job has been restarted, full config of the job and the pod created.


###kubectl describe job or kubectl describe cronjob

II

1.) This doc is about cluster troubleshooting, below this link 

https://kubernetes.io/docs/tasks/debug-application-cluster/debug-cluster/

III

1.) Create a pod named myapp wit 4 containers, using nginx, redis, memchached, consul images.


IV

1.) Find the pod which is using the most CPU resources and pipe the name to report.txt file

###kubectl top pods > report.txt

V

1.) Create new pod, from redis image, running in web namespace and listening at port 9090. 


#####
As long as your containers are listening on the port, they’ll still be available for network access. This just provides some extra information to Kubernetes.

Kubernetes ServiceTypes allow you to specify what kind of service you want. The default is ClusterIP.

Type values and their behaviors are:

ClusterIP: Exposes the service on a cluster-internal IP. Choosing this value makes the service only reachable from within the cluster. This is the default ServiceType.


NodePort: Exposes the service on each Node’s IP at a static port (the NodePort). A ClusterIP service, to which the NodePort service will route, is automatically created. You’ll be able to contact the NodePort service, from outside the cluster.


LoadBalancer: Exposes the service externally using a cloud provider’s load balancer. NodePort and ClusterIP services, to which the external load balancer will route, are automatically created.


ExternalName: Maps the service to the contents of the externalName field, by returning a CNAME record with its value. No proxying of any kind is set up.
#####


VI

1.) Create a pod in test namespace and set resource limit 1G of memmory and 200m CPU. 

Specifically, for each resource, containers specify a request, which is the amount of that resource that the system will guarantee to the container, and a limit which is the maximum amount that the system will allow the container to use. The system computes pod level requests and limits by summing up per-resource requests and limits across all containers. When request == limit, the resources are guaranteed, and when request < limit, the pod is guaranteed the request but can opportunistically scavenge the difference between request and limit if they are not being used by other containers. This allows Kubernetes to oversubscribe nodes, which increases utilization, while at the same time maintaining resource guarantees for the containers that need guarantees.

When you specify a Pod, you can optionally specify how much CPU and memory (RAM) each Container needs. When Containers have resource requests specified, the scheduler can make better decisions about which nodes to place Pods on. And when Containers have their limits specified, contention for resources on a node can be handled in a specified manner. For more details about the difference between requests and limits
