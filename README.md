# Replica-set-in-Kubernetes-on-AWS-Ubuntu

PROJECT-II

*Replica-set-in-Kubernetes-on-AWS-Ubuntu*

 A Replication set is a object that enables you to easily create multiple pods then make sure that number of pods always exist

Technologies Used - Kubernetes, Docker, AWS-EC2, Git & Github


-------------------------------------------------------------------------------------------------------------------------------------------------------------


Step :-

1.Launch the EC2 Instance Ubuntu in AWS

2.Install the Docker in Ubuntu

3.Kubernetes - Install Kubectl and Minikube

4.Create the YAML file and write the code

5.Execute the YAML File


-------------------------------------------------------------------------------------------------------------------------------------------------------------



All Steps in details with Commands:-


-----------------------------------AWS EC2 Instance-----------------------------------


- Click on EC2 service 

- Click on the Launch Instance

- Choose AMI

      Ubuntu
      
- Choose an Instance Type
      
      t.2 medium  -- 2vCPU required
      
- Configure Instance Details

      Number of Instance = 1
      Network = Default
      Subnet = Default
      Auto-Assign Public IP = Use subnet setting (Enable)
      
- Add Storage

      Root - /dev/xvda  - Size-8GB  -- Default
      
- Add Tags 

      Name - Replicaset
      
- Configure the Security Group

      Select - Create a new security group 
      Security group name = sg-replicaset
      
      
      -Type-----Protocol-----Port-----Source-
      
      SSH -------TCP---------22-------Anywhere
      HTTP-------TCP---------80-------Anywhere
      HTTPS------TCP---------443------Anywhere
      
- Click on Review and Launch

- Access the Ubuntu via the putty 


-----------------------------------Ubuntu Instance-----------------------------------

- Command for root access

      $ sudo su
      
- Update

      [root@ip--] # apt-get update -y
      
- Install the Docker 

      [root@ip--] # apt install docker -y
      
- Kubernetes -
 
- Install Kubectl 

      [root@ip--] # curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && chmod +x ./kubectl && sudo mv ./kubectl /usr/local/bin/kubectl

- Install Minikube

      [root@ip--] # curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/

- Install conntrack

      [root@ip--] # apt install conntrack
      
- Start the minikube 

      [root@ip--] # minikube start --vm-driver=none
      
- Create the YAML file

      kind: ReplicaSet
      apiVersion: apps/v1
      metadata:
          name: myrs
      spec:
          replicas: 2
          selectors:
                matchExpressions:
                    - {key: myname. operator: In, values: [tech, technical, coder]}
                    - {key: env, operator: NotIn, values: [production]}
          template:
                metadata:
                    name: testpod1
                    labels:
                       myname: programmer
                spec:
                  containers:
                    - name: c00
                      image: ubuntu
                      command:["/bin/bash", "-c", "while true; do echo it is a program; sleep5 ; done'"] 
                      
- Execute the YAML file

       [root@ip--] # kubectl apply -f myrs.yml
       
- Check replica set - It will show how many pod run in the replica set

       [root@ip--] # kubectl get rs
       
- Check pods

       [root@ip--] # kubectl get pods
       
- Increase or Decrease pod mannually according to the requirent 

       [root@ip--] # kubectl scale --replicas=8 rs/myrs
       
- Check the pod again and it will show the 8 pods

       [root@ip--] # kubectl get pods
       
*Done*



# Kubernetes

Kubernetes is an open source container management tool which automates container scaling and load balancing

It schedule runs and manages isolated container which are running on virtual/physical/cloud machines

All top cloud providers support Kubernetes


# Docker
Docker is a tool designed to make it easier to create , deploy and run application by using containers. Containers allow a developer to pakage up an application with all of the parts it needs, such as libraries and other dependencies and deploy it as one pakage. By doing so, thanks to the container, the developer can rest assured that the application will run on any other Linux machine regardless of any customize settings that machine might have that could differ from the machine used for writing and testing the code


# AWS EC2 Instance - Ubuntu
An Amazon EC2 instance is a virtual server in Amazon's Elastic Compute Cloud (EC2) for running applications on the Amazon Web Services (AWS) infrastructure. AWS is a comprehensive, evolving cloud computing platform; EC2 is a service that enables business subscribers to run application programs in the computing environment. It can serve as a practically unlimited set of virtual machines (VMs).

Amazon provides various types of instances with different configurations of CPU, memory, storage and networking resources to suit user needs. Each type is available in various sizes to address specific workload requirements.
                     
  
