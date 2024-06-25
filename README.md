# ansible-package-installation-on-os
AWS EC2 instance, install Ansible on it, and write an Ansible playbook to update packages on both Ubuntu and another OS using apt and the appropriate package manager, respectively.

# Step 1: Create two AWS EC2 Instances**
----------> Target and Host <------------
a) Log in to AWS Management Console:
  Go to the AWS Management Console.


b)Navigate to EC2 Dashboard:
  In the Services menu, select EC2 under the Compute section.

c) Launch Instance:
  Click "Launch Instance".
  Choose an Amazon Machine Image (AMI). For this example, select "Ubuntu Server      20.04 LTS (HVM), SSD Volume Type".
  Choose an Instance Type. Select t2.micro which is free tier eligible.
  Review and Launch. Click "Launch".
  Select an existing key pair or create a new key pair to SSH into your instance.    Download the key pair file (.pem) if you create a new one.

# Step 2: Connect to Your EC2 Instance to local machine
  make passwordless authentication using ssh-keygen
  On host instance
    step-1 
      1)  ssh-keygen
      2)  use ls -a to see the .ssh key
      3)  select .pub key(copy the public key)
  On target instance
    step 1
      1)  ssh-keygen
      2)   use ls -a to see the .ssh key
      3)   select authorized_key
      4)  open the authorized_key in vim 
          vim authorized_key
      5)  paste the host public key into target authorized_key
     
# Run the command 
    ssh target_public_ip
    this command will make passwordless authentication

# Step 3: Install Ansible on Your EC2 Instance
  Update Package List:
  a)sudo apt update
  b)Install Ansible:
    sudo apt install ansible -y

# Step 4 Create the Inventory File
  vim inventory
  add the target ip address
    
# Step 5: Create the Ansible Playbook
  vim update_packages.yml

# Step 6: Run the Playbook
  ansible-playbook -i inventory update_packages.yml



