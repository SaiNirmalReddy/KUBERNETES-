# KUBERNETES-
This is a KUBERNETES discussion . 

KUBERNETES 

-> Kubernets is a container orchestration platform . 

-> Containers are ephemerial(short living) in nature it means containers can die and revive anytime .

 -> Everybody knows that people started moving to "microservices"

-> The Only pre-requesites to learn KUBERNETES is DOCKER . 

-> So, basically DOCKER is a CONTAINER PLATFORM because docker is making you to interact with the containers becuase it provides you complete container journey and complete container life cycle whether by using the Docker Engine or Docker CLI . 

-> So, Now What is Kubernets - > KUBERNETES is a Container Orchestration Platform .

 -> So before we start KUBERNETES, we will start with the problems of DOCKER .

     Problem 1 - Single Host Nature 

    Problem -2 - Auto Healing 

    Problem 3 - Auto Scaling 

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


-------------------------------------------------------------------------------------------------------------------------------------------------


 KUBERNETES ARCHITECTURE


![Kubernetes Architecture](./Kubimages/Screenshot%202024-02-13%20005655.png)


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


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Kubernetes Production Systems

 

-> Let's get to know how Devops Enginner manages the lifecycle like creation,upgradation,configuration,deletion of kubernetes clusters.

-> Most of the people practicing kubernetes on platforms like MINIKUBE,K3S,KIND,K3D,MICROK8S , these platforms are just for practice not for the real-time .


-> Let's know which tools are using in organization 


-> Let's learn about what are the distrubutions of kubernetes - They are some like Amazon-EKS, RedHat-Openshift, VMWare-Tanzoo,RancherLabs-Rancher , these tools are building User experience on kubernetes or any customer experience on Kubernetes .

-> Let's learn about Order of distrubutions of Kubernetes in Real-time .

 - Kubernetes, after that
 - Openshift      "
 - Rancher
 - Tanzoo
 - EKS
 - AKS
 - GKE
 - DKE  


 -> We use a tool called "KOPS" to install the "KUBERNETES" 


 -> Now, How Devops Engineers manages 100's of clusters on Production ? 

    -> We have Kops,Kubeadm,Kubequash 

          == We use a tool called "KOPS" to create,manage and delete the clusters in "KUBERNETES" .But Initially before 4 or 5 years we used to use "Kubeadm" in production but the difference with Kubeadm is you have to lot of manual activities like whenever you want to Upgrad, Configure - Kubeadm doesn't have that smooth approach of handling things whereas "KOPS" is basically Kubernetes Operations .

-> We have the Lifecycle of Kubernetes like Installing,Upgrading,Managing and Deleting Clusters and this lifecyle is managed by KOPS . 

-> 


# Kubernetes-Zero-to-Hero
Creating this repo with an intent to make Kubernetes easy for begineers. This is a work-in-progress repo.

## Kubernetes Installation Using KOPS on EC2

### Create an EC2 instance or use your personal laptop.

Dependencies required 

1. Python3
2. AWS CLI
3. kubectl

###  Install dependencies

```
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
```

```
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
```

```
sudo apt-get update
sudo apt-get install -y python3-pip apt-transport-https kubectl
```

```
pip3 install awscli --upgrade
```

```
export PATH="$PATH:/home/ubuntu/.local/bin/"
```

### Install KOPS (our hero for today)

```
curl -LO https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64

chmod +x kops-linux-amd64

sudo mv kops-linux-amd64 /usr/local/bin/kops
```

### Provide the below permissions to your IAM user. If you are using the admin user, the below permissions are available by default

1. AmazonEC2FullAccess
2. AmazonS3FullAccess
3. IAMFullAccess
4. AmazonVPCFullAccess

### Set up AWS CLI configuration on your EC2 Instance or Laptop.

Run `aws configure`

## Kubernetes Cluster Installation 

Please follow the steps carefully and read each command before executing.


->  Next, KOPS require as a pre-requisite isto we need to create S3 bucket because the reason is KOPS usually manages hundreds of kubernetes clusters and to manage these Kubernets clusters, it is very easy to store all of the configuration of your kubernetes clusters in S3 buckets . 

### Create S3 bucket for storing the KOPS objects.

```
aws s3api create-bucket --bucket kops-abhi-storage --region us-east-1
```

### Create the cluster 

```
kops create cluster --name=demok8scluster.k8s.local --state=s3://kops-abhi-storage --zones=us-east-1a --node-count=1 --node-size=t2.micro --master-size=t2.micro  --master-volume-size=8 --node-volume-size=8
```

-> One thing to remember here is we are using domain "k8s.local" but in real time we use "amazon.com", google.com and one additional step you shouls is you configure domain to "route53" . 

-> Use the command - aws route53 create-hosted-zone --name dev.example.com --caller-reference 1 

### Important: Edit the configuration as there are multiple resources created which won't fall into the free tier.

```
kops edit cluster myfirstcluster.k8s.local
```

Step 12: Build the cluster

```
kops update cluster demok8scluster.k8s.local --yes --state=s3://kops-abhi-storage
```

This will take a few minutes to create............

After a few mins, run the below command to verify the cluster installation.

```
kops validate cluster demok8scluster.k8s.local
````



Kubernetes Deployment

-> Kubernetes Deployment is nothing but the Pods .

-> Let's understand the difference between 


---------------------------------------------------------------
 
Container - So, we will create Container using Docker and to run this container , we provide specificaions to run the command-line by writing the commands like

docker -it 
docker -d
docker --network
docker -p -v   


---------------------------------------------------------------
  Pod - So, Now what Kubernetes say is let me bring the Enterprise model that is "instead of writing these things in a command line - you can create a YAML manifest and inside this YAML manifest , will write about container images, container nodes , ports, volumes and network . 

-> The only difference is a single or mutliple containers and why we create multiple containers is one is dependent to another C1<->C2 .

-> The advantage of using POD is both of the containers can use the same network , same storage and same local host .



 --------------------------------------------------------------



 
 Kubernetes Deployment - 
  

  Kubernetes have two behaviours in Deployment 


    1)Auto Healing 2)Auto Scaling 


    So these kind of things done in Deployment stage 

  -> So, If you created a deployment resource, it will again create a intermediate resource called Replica Set and then Replica Set will create something called as Pod .
---------------------------------------------------------------


So, What Kubernetes says is create a Pod using the Deployment resources and this Deployment resource will create Replica Set which is a Kubernetes controller and finally this will roll out the Pods . 

-> So , inside the "DEPLOYMENT YAML MANIFEST" , you increase the count of Replicas but in the Kubernetes there has to be something called "Kubernetes Controller" ensures that there are 2 Pods and even if users delete one of these Pods, then Kubernetes says like beacuse you have submitted YAML MANIFEST to me, I implement Auto Healing using the Replica Set Controller so that every detail and data will be with the Replicas Sets which is handled by Kubernetes Controller and this Controller ensures that the desired state is always present in the actual cluster . So there are "Default Controllers" and as well as you can create "Custom Controllers" 

-> So the End Process is You will Create a |Deployment|-> and this Deployment will roll out a |Replica Sets| -> and this will create the Number of Pods you mention in the "Deployment YAML" Manifest . 

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

   KUBERNETES DEPLOYMENT 


-> In Kuberenetes what we do is first we create a Deployement and that will create a replicaset and those Replica sets are controlled by control-managers in controllers and this replica set is basically responsible for Auto-healing feature in Kubernetes and

-> This Deployment - will create a Pod

-> So the Pod is basically a wrapper to the Container which handles the single or multiple containers and where as in Pod Kubelet is resposible for whether the container is running or not and Ku-proxy is responsible for IP - addresses and Networking in Kubernetes . 


-> Control Managers in the Master Node are responsible for contolling the actions of replica sets and this signal of actions is received to the API-SERVER and API-SERVER sends the signal to Control Managers to handle the actions . 



-> kubectl deployment.yml
------
-------
---------
----------

kubectl apply -f deployment.yml

->kubectl pod.yml

------
-------
---------
----------

kubectl apply -f pod.yml 

--> For example , if some user deletes the pod , then Kubernetes will take care of the actions like if the pod is deleted unfortunately by someone, then because of the deployment and there we have replica sets which are controlled by control managers will start creating again the same pod again and make sures it is in the running state . 


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 KUBERNETES SERVICES 


 
Kubernetes Services 


-> Service is very critical component of Kubernetes . 

|D| -> |RS| -> |P| 


-> Let's suppose say we have |1| |2| |3| pods and if every request is going to one single pod, it will goes down and number of replicas will depend up on no. of concurrent users trying to access your applications.
and Because of Auto Healing capability which is implemented by deployment in Kubernetes or replica set controller in Kubernetes . 


-> For example, Pod |1| has IP - 172.16.3.4 and Pod 2 has IP - 172.16.3.5 and Pod |3| has IP - 172.16.3.6 and for some reason Pod 1 went town but due to Auto Healing capability again the same Pod is created but with the "DIFFERENT IP ADDRESS" from |172.16.3.4| to 
|172.16.3.8| , so the use who is trying to access the but can't get the information of the POD 1, so Kubernetes comes up with the "SERVICE" and it will tell the Kube Proxy to send the requests accordingly and by which the problem is solved .

         172.16.3.4                user1
         172.16.3.5                user2
         172.16.3.6                user3
              |
              ^
         |Deployment|
              |
            |SVC|

   -> The advantage of SERVICE is 1) Load Balancing 2) Sevice Discovery 

 -> Let's know how the problem is solved and if the same case user1 sends the request to Pod 1 IP but for some reason it went down and another Pod is created but with Different IP , So the Kubernetes Service has new process called "Labels and Selectors" and by which for every Pod that is getting created, Devops Engineers will apply a Label and Label is common for all the Pods and why the Label will be same is Replica set will again create the Deployment with the same YAML file and So if the Services keeps the tracking of the Pods using Labels instead of IP adresses then the problem is solved . 

-> When you are creating the kuberenetes service resource in the YAML manifest, you can create it with three default types . 

1) Cluster IP 
2) Node Port 
3) Load balancer 

-> Cluster IP -  When we are creating the service using the Cluster IP mode, no body will access to the Cluster even if have access to VPC and even if we have EC2 Instance only if you can login to the Kubernetes Cluster and if they have access to the network in the kubernetes cluster, they only can access the application .

 -> Node Port - When we are creating the service using the Node-Port mode then it will allow your application inside your organization , so some user they might don't have asscess with Kubernetes Cluster but they just access with Worker Node IP adressses, only they can access your apllication if you create the service as type Node-Port mode . 


-> Load balancer - When we are creating the service using the Load-balancer type, then the service will expose the application the external world .

  Example -> Let's say you are deploying the application on the EKS Kubernetes Cluster then you will get a Elastic Load Balancer (ELB) IP address for your specific servive and who are trying to access they can access using the public IP Address and this IP Address is generated by the Cloud-Control Manager whenever we are using the cloud services . -> (AWS Implementation) . 


  
Load Balancer - Amazon .com 

Node Port - Organization or VPC 

Cluster IP - Devops Engineers



For example if we delete one pod , and due to concept of Auto-Healing in kubernetes , pod will again run with some different IP Address, then the user who ar trying to access the application faces the traffic loss, so kubernetes came up with the concept called kuberenets services which maintains the "labels and selectors" by which the user cannot confuse because of this concept


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-> KUBERNETES INGRESS AND INGRESS CONTROLLERS

Kubernetes Ingress and Ingress Controllers provide several advantages in real-time scenarios, making them crucial components for managing external access to applications deployed in Kubernetes clusters. Here are some key advantages:

Single Entry Point:

Advantage: Ingress acts as a single entry point for external traffic to access services within the Kubernetes cluster. This simplifies routing and load balancing, providing a centralized and consistent way to manage external access.

Path-Based Routing:

Advantage: Ingress allows path-based routing, enabling you to route traffic to different services based on URL paths. This is valuable for hosting multiple applications or microservices on a single domain.

SSL/TLS Termination:

Advantage: Ingress Controllers can handle SSL/TLS termination, offloading the responsibility of managing certificates from individual services. This simplifies certificate management and ensures secure communication between clients and services.

Load Balancing:

Advantage: Ingress Controllers often come with built-in load balancing capabilities. They distribute incoming traffic across multiple pods or nodes to optimize resource utilization and enhance application availability and reliability.

HTTP and HTTPS Support:

Advantage: Ingress supports both HTTP and HTTPS protocols, allowing you to secure communication with your applications. This is crucial for protecting sensitive data and complying with security best practices.

Web Application Firewall (WAF) Integration:

Advantage: Some Ingress Controllers support integration with Web Application Firewalls (WAFs). This enhances security by providing additional protection against common web application vulnerabilities and attacks.

Rewrite and Redirect Rules:

Advantage: Ingress enables you to define rewrite and redirect rules, allowing you to modify URL paths or redirect traffic to a different location. This is useful for creating user-friendly URLs and managing changes in application endpoints.

Dynamic Configuration Updates:

Advantage: Ingress Controllers often support dynamic configuration updates. This means you can modify routing rules, add or remove services, and make other adjustments without disrupting the overall application availability.

Customizable Error Pages:

Advantage: Ingress Controllers allow you to customize error pages for various HTTP status codes. This ensures a better user experience in case of errors and helps in providing meaningful information to users.

Integration with Kubernetes Ecosystem:

Advantage: Ingress is a native Kubernetes resource, tightly integrated with the Kubernetes ecosystem. This integration simplifies the management of external access within the Kubernetes environment, aligning with the declarative nature of Kubernetes configuration.

Scalability:

Advantage: Ingress Controllers can scale horizontally to handle increased traffic and provide high availability. This scalability ensures that the Ingress infrastructure can grow alongside the applications it serves.
In real-time scenarios, these advantages collectively contribute to efficient traffic management, improved security, and enhanced flexibility in deploying and managing applications within Kubernetes clusters.




































 


















 


























 




      




