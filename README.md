# Neo4j-Azure
## Create Virtual Machine on Azure
## Login VM
User the user of VM which is created by above step
```
ssh -i "WHOTest_key_azure.pem" neo4j@51.104.237.159
```
## install Java 17
```
sudo apt-get update
sudo apt install openjdk-17-jre-headless
```
Add the official OpenJDK package repository to apt:
```
sudo add-apt-repository -y ppa:openjdk-r/ppa
```
## Install Neo4j
```
sudo mkdir /var/data/neo4j_install
sudo scp -i WHOTest_key_azure.pem  ~/Downloads/neo4j-enterprise-5.0.0-drop06.0-unix.tar.gz neo4j@51.104.237.159:~/.
sudo cp neo4j-enterprise-5.0.0-drop06.0-unix.tar.gz /var/data/neo4j_install/.
sudo tar xvfz neo4j-enterprise-5.0.0-drop06.0-unix.tar.gz 
```
