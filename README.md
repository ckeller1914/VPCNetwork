# VPCNetwork and Google Compute Engine

## Obejective 

Google Cloud Virtual Private Cloud (VPC) provides networking functionality to Compute Engine virtual machine (VM) instances, Kubernetes Engine containers, and App Engine flexible environment.

#### Task:
-Explore the default VPC network

-Create an auto mode network with firewall rules

-Create VM instances using Compute Engine

-Explore the connectivity for VM instances
## Task 1. Explore the default network 

### View the subnets 

The default network has a subnet in each Google Cloud region. 

1) In the Cloud Console, on the Navigation menu (Navigation menu icon), click VPC network > VPC networks. 

 ![Screenshot (142)](https://github.com/user-attachments/assets/707753ed-b6cb-4fdc-9368-e91bd95e87ef)


2) Click default. 

3) Click Subnets. 

![Screenshot (144)](https://github.com/user-attachments/assets/546df687-cfdc-4dbe-a2c7-727d06403331)

 

### View the routes 

4) In the left pane, click Routes. 

5) In Effective Routes click Network, and then select default. 

6) Click Region and select region Click View. 

 ![Screenshot (146)](https://github.com/user-attachments/assets/5823897e-4acc-4a6e-8f16-81ae89bf7111)


### View the Firewall rules 

In the left pane, click Firewall. 
Notice that there are 4 Ingress firewall rules for the default network: 

default-allow-icmp 

default-allow-rdp 

default-allow-ssh 

default-allow-internal 

 ![Screenshot (147)](https://github.com/user-attachments/assets/79b38022-9637-43b1-8179-51f29c0023fe)


 

### Delete the Firewall rules 

7) Select all of the default network firewall rules. 

8) Click Delete. 

9) Click Delete to confirm the deletion of the firewall rules. 

![Screenshot (148)](https://github.com/user-attachments/assets/90545599-3591-41d1-a103-4aa0d0852dbb)

![Screenshot (149)](https://github.com/user-attachments/assets/3c4498a3-689a-433f-b6d7-649bf25bcb23)


 

### Delete the default network 

10) In the Cloud Console, on the Navigation menu (Navigation menu icon), click VPC network > VPC networks. 

 ![Screenshot (150)](https://github.com/user-attachments/assets/3ff31edc-4996-407a-9520-6e5939f9e343)


11) Select the default network. 

12) Click Delete VPC network. 

13) Click Delete to confirm the deletion of the default network. 
Wait for the network to be deleted before continuing. 

 ![Screenshot (151)](https://github.com/user-attachments/assets/5b22d69e-d2d0-49fb-880a-a3e3a80cbe1f)


14) In the left pane, click Routes. 
Notice that there are no routes. 

15) In the left pane, click Firewall. 
Notice that there are no firewall rules. 

## Task 2. Create a VPC network and VM instances 

Create a VPC network so that you can create VM instances. 

### Create an auto mode VPC network with Firewall rules 

#### Replicate the default network by creating an auto mode network. 

16) On the Navigation menu (Navigation menu icon), click VPC network > VPC networks. 

17) Click Create VPC network. 

18) For Name, type mynetwork. 

19) For Subnet creation mode, click Automatic. 
Auto mode networks create subnets in each region automatically. 

20) For Firewall, select all available rules. 
These are the same standard firewall rules that the default network had. 

21) Click Create. 
When the new network is ready, notice that a subnet was created for each region. 

### Create a VM instance in Region 

#### Create a VM instance in the Region region. Selecting a region and zone determines the subnet and assigns the internal IP address from the subnet's IP address range. 

22) On the Navigation menu (Navigation menu icon), click Compute Engine > VM instances. 

23)  Create instance. 

24) Specify the following, and leave the remaining settings as their defaults: 

25) Click Create.

    ![Screenshot (157)](https://github.com/user-attachments/assets/6abed15b-8580-48df-832a-de41fc479177)


### Create a VM instance in Region 2 

#### Create a VM instance in the Region 2 region. 

26) Click Create instance. 

27) Specify the following, and leave the remaining settings as their defaults: 

28) Click Create. 

 ![Screenshot (158)](https://github.com/user-attachments/assets/a1bdff71-eea6-4dad-9b84-693ef9196f42)


 

## Task 3. Explore the connectivity for VM instances 

#### Explore the connectivity for the VM instances. 

#### Ping both the internal and external IP addresses of your VM instances using ICMP.

### Verify connectivity for the VM instances 

#### The firewall rules that you created with mynetwork allow ingress SSH and ICMP traffic from within mynetwork (internal IP) and outside that network (external IP). 

29) On the Navigation menu (Navigation menu icon), click Compute Engine > VM instances. 
Note the external and internal IP addresses for mynet-eu-vm. 

30) For mynet-us-vm, click SSH to launch a terminal and connect. 

 
![Screenshot (159)](https://github.com/user-attachments/assets/6b7dc657-60d6-451b-ad16-7ebbf8827561)

 

31) If an Authorize popup appears, click on Authorize 

 
![Screenshot (156)](https://github.com/user-attachments/assets/04ac4725-d42e-458a-bf50-5e52e65f0602)

 

To test connectivity to mynet-eu-vm's internal IP, run the following command, replacing mynet-eu-vm's internal IP: 

ping -c 3 10.138.0.2 

![Screenshot (161)](https://github.com/user-attachments/assets/21fefb01-2b91-4781-aa52-4ce4b74a2e11)

 
