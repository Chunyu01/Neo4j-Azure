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
## Install Apoc
At neo4j@WHOTest:/var/data/neo4j_install/neo4j-enterprise-5.0.0-drop06.0/plugins: 
```
sudo curl -L -O https://github.com/neo4j-contrib/neo4j-apoc-procedures/releases/download/4.4.0.9/apoc-4.4.0.9-all.jar
```
## Install NeoSemantic
At neo4j@WHOTest:/var/data/neo4j_install/neo4j-enterprise-5.0.0-drop06.0/plugins: 
```
sudo curl -L -O https://github.com/neo4j-labs/neosemantics/releases/releases/download/4.4.0.2/neosemantics-4.4.0.2.jar
```
# Config Neo4j
```
sudo nano neo4j.conf
```
- Listen to all IP addresses:
  - Bolt connector "#dbms.connector.bolt.listen_address=:7687" -> dbms.connector.bolt.listen_address=0.0.0.0:7687
  - HTTP Connector "#dbms.connector.http.listen_address=:7474" -> dbms.connector.http.listen_address=0.0.0.0:7474
  - HTTPS Connector "#dbms.connector.http.listen_address=:7473" -> dbms.connector.https.listen_address=0.0.0.0:7473
