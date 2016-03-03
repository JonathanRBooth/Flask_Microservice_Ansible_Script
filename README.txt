How to use this Ansible script: (from a fresh Ubuntu install)


1. Update & Upgrade apt:
   - $ sudo apt-get update
   - $ sudo apt-get upgrade

2. SCP transfer the ss_ansible folder to the /home/ubuntu/ directory 

3. - $ sudo apt-get install ansible
   - $ sudo apt-get install python-pip
   - $ sudo pip install boto
   - $ sudo apt-get install git
   
4. Download Ansible 2.0 (beta):
   - $ git clone git://github.com/ansible/ansible.git --recursive
   - $ cd ./ansible
   - $ source ./hacking/env-setup
   - $ git checkout 07b588f6c0065f5c91b95f96885b946852187197
   
5. Set the AWS keys as environment variables for the dynamic inventory script
   - $ export AWS_DEFAULT_REGION=eu-west-1
   - $ export AWS_SECRET_ACCESS_KEY= YOUR_AWS_SECRET_KEY
   - $ export AWS_ACCESS_KEY_ID= YOUR_AWS_ACCESS_KEY
   
6. Set permissions
   - $ sudo chmod u+x ~/ss_ansible/inventories/ec2.py
   - $ sudo chmod 400 ~/ss_ansible/files/authorized_keys

7. Edit ~/ss_ansible/vars/all.yml and insert your AWS credentials and AWS EC2 keypair name ( you must have previously generated one in the EC2 console)

8. Edit ~/ss_ansible/files/authorized_keys with the EC2 keypair .pem you just specified in /vars/all.yml

9. From the main ss_ansible directory run the playbook: 
   - $ cd ~/ss_ansible
   - $ ansible-playbook playbook.yml
  
 
The whole process will take ~5 minutes. At the end it will output the url of the new Elastic Load Balancer that has been created.
