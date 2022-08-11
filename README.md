# Replica-set-in-Kubernetes-on-AWS-Ubuntu

PROJECT-II

*Replica-set-in-Kubernetes-on-AWS-Ubuntu*

 

Technologies Used - Docker, AWS-EC2, Kubernetes, Git & Github


-------------------------------------------------------------------------------------------------------------------------------------------------------------


Step :-

1.Launch the EC2 Instance Ubuntu in AWS

2.Install the Docker in Ubuntu

3.Kubernetes - Install Kubectl and Minikube

4.Create the YAML file and write the code

5.Execute the File


-------------------------------------------------------------------------------------------------------------------------------------------------------------



All Steps in details with Commands:-


-----------------------------------AWS EC2 Instance-----------------------------------


- Click on EC2 service 

- Click on the Launch Instance

- Choose AMI

      Ubuntu
      
- Coose an Instance Type
      
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
