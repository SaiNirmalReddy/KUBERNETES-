# KUBERNETES-
This is a KUBERNETES discussion . 



KUBERNETES 

![Kubernetes Architecture] (https://github.com/SaiNirmalReddy/KUBERNETES-/blob/main/Kubimages/Screenshot%202024-02-13%20005655.png)


-> Kubernets is a container orchestration platform . 

-> Containers are ephemerial(short living) in nature it means containers can die and revive anytime .

    Problem 1 - Single Host Nature 

    Problem -2 - Auto Healing 

    Problem 3 - Auto Scaling 

 -> Everybody knows that people started moving to "microservices"

-> The Only pre-requesites to learn KUBERNETS is DOCKER . 

-> So, basically DOCKER is a CONTAINER PLATFORM because docker is making you to interact with the containers becuase it provides you complete container journey and complete container life cycle whether by using the Docker Engine or Docker CLI . 

-> So, Now What is Kubernets - > KUBERNETES is a Container Orchestration Platform .

 -> So before we start KUBERNETES, we will start with the problems of DOCKER .

-> Containers are ephemerial(short living) in nature it means containers can die and revive anytime .

1) Problem 1 - Single Host Nature 

-> Let's say you or on a Host on top of which you installed Docker    and top which you have created 100 containers and one of this containers like C1 started taking lot of memory , so this C1 may impacts your C89 or C99 container because of not getting enough resources so it may die or not yet started - beacuse you have only Host i.e., Single Host Nature .

 C1,C2,C3,C4, -- C100 / Docker 

2)  Problem -2 - Auto Healing 

 -> Let's say somebody has killed one of your container so what happens is the apllication which is running inside the container is not accessible. So, unless the User or Devops Engineer starts or acts up on this particular container , It will not start again - and this behaviour is called Auto Healing .

-> So, Auto Healing is the definition for without any manual intervention the container has to start itself .

-> Let's say like Devops Engineer cannot handle like 10000's of containers like performing "docker ps" command and know which is in running state , so there has to be a mechanism that is Auto Healing.


3) 	  Problem 3 - Auto Scaling 

->
 |C1| - 4GB, 4CPU / Docker / EC2 Instance

-> Let's say you or on a Host on top of which you installed Docker    and top which you have installed Containers and C1 can maximum consume upto 4GB RAM and 4 CPU's becuase it is the maximum capacity of the Host . But for some reason, users have been increased from 10,000 to 1,oo,ooo . So to satisfy this increasing load or for the conainer or the application to act upon the increasing load , you need to have a specific feature called Auto Scaling .

 So, as soon as the load gets increases , there are two ways .

  1) To balance the load, Manually you increase the containers from 1 to 10 or you increase the similar containers like 10 C1 Containers .
  2) 2) or it has to happen automatically

   So, Now Docker doesn't support both the ways  


So, all these problems are solved by KUBERNETES .


 Problem 4 - 

-> As we know that Docker is a simple platform it means it doesn't support Enterprise level support .

 So, when we deal eith Enterprise applications, you have a lot of things to deal with

  1) Load balancer 2)Firewall 3)Auto Scale or it should support Scaling 4) Auto Healing or it should support Auto Healing 5) API Gateways so there are many starts which Docker doesn't support this Enterprise Level Support .



     How KUBERNETES is solving the problem ? 


 -> By default, kubernets is a cluster and cluster meant by Group of Nodes 


 -> Previously when we install Docker , we just install it on one personal laptop or one EC2 Instance and we can even instal kubernetes on one single host but In General or In Production time,  KUBERNETES is said to be a Master-Node Architecture .

-> The advantage of being installing kubernetes is for example if   | C1,-- C100 | - One C59 or C89 is going out of resources then kubernetes will put these faulty containers or faulty applications in a new different node because kubernetes have a clustered architecture . 

  So Single Host Nature problem is solved bu kubernetes .



-> Auto Scaling - Kubernetes has something called as Replication container or Replica Sets . 

 We know that Docker can't handle load which means the load is increasing from 10,000 to 1,00,000 . So, kubernetes is basically dependent on YAML files so everything in kubernetes is about YAML files so in Replica Set controller .YAML file . So, as a Devops Engineer we can go to one specific YAML file and YAML is bacisally a indentation format just like JSON format and simply you go to this YAML file and increase Replicas from 1 to 10 .

-> Kubernetes also supports HPA (Horizontal Pod Autoscaler) using this whenever there is a load, just keep increasing the container.

 For Example, when my container is receiving threshold of 80%  just spin-up one more container.

So, by using Replication Controller Yaml files and Horizontal Pod AutoScaler , problem of Auto scaling is solved in Kubernetes .


-> Auto Healing - Whenever there is damage , Kubernetes has to control and fix the damage .


  Example , Let's say for some reasons your container goes down,  Kubernetes will start a new container .

 Kubernetes ha something called as "API SERVER" so whenever the API SERVER understands that one container is going down , then it will create a new container using which the problem AUTO HEALING is solved . 


Now, Kubernetes is basically originated by Google and Google is using one specific tool called "BORG" and Kubernetes is one of the parts of "BORG" .


->  So, people at Google built a "Enterprise Level Container Orchestration Platform"

-> Kubernetes cannot handle Advanced Load balancing capabilities so to solves this we ask apllications like FI, NGINX to create a  kubernetes controller using which people can use "load balancer" even in kubernetes and this concept called as "Ingress Controllers"  .





 KUBERNETES ARCHITECTURE


 "C:\Users\saini\OneDrive\Pictures\Screenshots\Screenshot 2024-02-13 005655.png"


-> Kubernetes offers four fundamental advantages over Docker 

 1) Cluster 

 2) Auto Healing 

  3) Auto Scaling 

   4) Mutliple Enterprise Level Support - Like Kubernets offers you advanced load balancing, security related things, advance networking .


 Control Plane  |              Data Plane


API Server                      Kubelet
etcd                             Proxy
Scheduler                       Container Runtime
Controller Manager
Cloud Controller Manager

-> Let's learn about the Worker Node Componets in the architecture

-> Let's start with creation of Container in Docker 

-> Let's say there is a virtual machine , on top which you installed  DOCKER and you are running a container using a "docker run" command , Now Let's assume we are running a "JAVA APPLICATION" but we don't have a "Java Runtime Environment" then the JAVA apllication will not run . So, similarly in the same way docker will not tun if it doesn't have the "docker run time" component and we call this as "DockerShim" . 


-> Now, If we move to Kubernetes we have a Master and Worker Architecture . Now just a Example like there is a One Master and One Worker but In general we have Multiple Masters and Multiple Workers in Real -time . 


-> So, what happens in Kubernetes is the request is received and like when we deploy your "Pod" from Master Node through Control Plane in Worker Node and we have a component is kubernetes is called as "kubelet" and it is responsible for running your Pod and it always checks for whether the Pod is running or not and and for this needs to be have something like "container-runtime" and this implements container interface(containerd,dockershim,cri-o-).and if the pod is not in running state , then "Kubelet"  will inform the "api server" in the control plane to do someting or restart the container .

-> Next, the "Kube-Proxy" basically provides you Networking that means every Pod that you are creating and every container you are creating , it will alocate a IP address and it will be responsible even for the load balancing capabilities because we know that Kubernetes have something called as "Auto-Scaling" and when you scale your pod, instead of one replica if you have 2 replicas for your pod, then has to be a component which says send 50% to one and 50% to other that is done by kube-proxy . 

-> Kube-Proxy uses IP Tables for the Networking configuration .



-> Now, Let's learn about the Master Node Componets in the architecture .

-> To manage and decide the instructions, there must be a heart or kernel to the Kubernets in Master node that is "API SERVER" . API Server is a ccomponent that basically exposes your Kubernetes . 

-> Let's say the user is trying to create a Pod and access API Server and for example API SERVER decides "node1" is free but to schedule the component in "node1", we have component in Kubernetes is "Scheduler" . So Scheduler basically responsible for scheduling your pods or resources in kubernetes and it receives information from API Server .


-> After this, we are deploying a production level application on kubernetes cluster and we have the component basically acts as a back-up service handles the entire storage of cluster information is "etcd" and etcd is a key value store  So, the entire kubernetes cluster information is stored as objects (or) key-value pairs in etcd .


-> Controller Manager - Kubernetes have controllers like Replica sets that is basically a maintaing stage of kubernetes pod .

-> To auto-scale the components from one to two,three and so on there has to be a component if we need two or many pods at the time, replica sets are responsible anf to ensure the contollers are always running, controller manager is responsible for these things . 


-> Cloud Controller Manager (CCM) 


-> Let's say that Kubernetes can run on "EKS,AKS" cloud platforms . 

-> Let's say you are using Elastic Kubernetes Services and there is a user request to create a load balancer or storage , So User sends a request to create a storage or load balancer , the API should understand and create them and this mechanism has to be implemented on "Cloud Control Manager"  



-> In a nutshell, Control Plane is controlling the actions and Data Plane is executing the actions . 















 




      




