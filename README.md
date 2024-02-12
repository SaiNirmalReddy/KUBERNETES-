# KUBERNETES-
This is a KUBERNETES discussion . 



KUBERNETES 


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

 C1,C2,C3,C4, -- C100
 ________________________
   Docker

2)  Problem -2 - Auto Healing 

 -> Let's say somebody has killed one of your container so what happens is the apllication which is running inside the container is not accessible. So, unless the User or Devops Engineer starts or acts up on this particular container , It will not start again - and this behaviour is called Auto Healing .

-> So, Auto Healing is the definition for without any manual intervention the container has to start itself .

-> Let's say like Devops Engineer cannot handle like 10000's of containers like performing "docker ps" command and know which is in running state , so there has to be a mechanism that is Auto Healing.


3) 	  Problem 3 - Auto Scaling 

->
 |C1| - 4GB, 4CPU 
 _________________________
   Docker
____________________________
  
  EC2 Instance

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













 




      




