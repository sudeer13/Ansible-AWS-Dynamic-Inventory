# Setting Up Ansible AWS EC2 Dynamic Inventory

### Pre-requisites:
   1. Install and setup Ansible Server
   2. Install boto (version>=2.24.0)
   3. IAM Programmatic access user in AWS with EC2 access.
   4. Get the ec2.ini and ec2.py file.
       

### Setup 

To get help on dynamic inventory please follow  [Ansible Official Document](https://docs.ansible.com/ansible/latest/user_guide/intro_dynamic_inventory.html#inventory-script-example-aws-ec2)

1. Create IAM Programmatic access user with EC2 full access on AWS console 

   `IAM` --> `users` --> `Add user` 

1. Export IAM user credentials on Ansible server. 

   ```bash
   export AWS_ACCESS_KEY_ID='XXXXX'
   export AWS_SECRET_ACCESS_KEY='XXXXX'
   ```
1. To export keys permanently make sure that you have installed pip and boto and add credentials ~/.boto file

1. add executing permissions to ec2.py script
   ```sh
   chmod 755 ec2.py
   ```
1. test the script 
   ```
   ./ec2.py --list
   ```
1. List out servers which are running on ap-south-1a AZ
   ```
   ansible -i ec2.py  ap-south-1a --list-hosts
   ```
