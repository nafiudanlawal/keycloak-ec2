
# Keycloak on single EC2 Instance

This project goes through the steps to install keycloak on a single AWS EC2 instance for use cases that require less than 10 transactions per second 

## Requirements
- AWS Account
- Domain name with hosted zone on Route53

## 1. AWS 
- EC2
  - create new instance (I used t3.micro instance)

- Security Group 
  - open port 80/443
  - attach to instance created

- Route53
  - create a new hosted zone with registered domain name.
  - Add an A record pointing to public IP of the instance (server).

## 2. Keycloak package requirements
Keycloak requires the following packages to work successfully for the use-case;
- java
- database access (postgres)
- nginx for port-forwarding

For the next part of the process we need to ssh into the EC instance. Let's go through how to install all these components below. 

## 3. Installing Packages 
  - Install Java
    - `sudo add ppa-openjdk repository`
    - `sudo add-apt-repository ppa:openjdk-r/ppa`
    - `sudo apt update`
    - `sudo apt install openjdk-21-jdk`

  - Install postgres and Create User
    - `sudo apt install postgresql`
    - `sudo -u postgres psql template1`
    - `ALTER USER postgres with encrypted password 'your_password';`
  - Downlaod Keycloak
    - `wget https://github.com/keycloak/keycloak/releases/download/26.1.2/keycloak-26.1.2.zip`
  - 

4. Download keycloak
`sudo certbot certonly --standalone -d yourdomain.com`

`bin/kc.sh bootstrap-admin user`

`bin/kcadm.sh config credentials --server http://localhost:8443 --realm master --user admin --password admin@123`

`bin/kcadm.sh create users -r master -s username=nafiu -s enabled=true`

`bin/kcadm.sh set-password -r master --username nafiu --new-password admin@123`

`bin/kcadm.sh add-roles -r master --uusername nafiu --rolename admin`


5. install nginx
	


