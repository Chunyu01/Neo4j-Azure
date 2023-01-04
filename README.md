# Neo4j-Azure
## Create Virtual Machine on Azure
<img width="536" alt="image" src="https://user-images.githubusercontent.com/4737766/210543679-88558f8f-8a14-4e31-bf51-7da4117056be.png">

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
sudo curl -L -O https://github.com/neo4j/apoc/releases/download/5.0.0/apoc-5.0.0-care.jar
```
## Install NeoSemantic
At neo4j@WHOTest:/var/data/neo4j_install/neo4j-enterprise-5.0.0-drop06.0/plugins: 
```
sudo curl -L -O https://github.com/neo4j-labs/neosemantics/releases/releases/download/4.4.0.2/neosemantics-4.4.0.2.jar
```
## Install GDS
```
sudo curl -L -O https://github.com/neo4j/graph-data-science/releases/download/2.2.2/neo4j-graph-data-science-2.2.2.jar
```
# Config Neo4j
```
sudo nano neo4j.conf
```
- Listen to all IP addresses:
  - Bolt connector "#dbms.connector.bolt.listen_address=:7687" -> dbms.connector.bolt.listen_address=0.0.0.0:7687
  - HTTP Connector "#dbms.connector.http.listen_address=:7474" -> dbms.connector.http.listen_address=0.0.0.0:7474
  - HTTPS Connector "#dbms.connector.http.listen_address=:7473" -> dbms.connector.https.listen_address=0.0.0.0:7473
- Config NeoSemantics
 add dbms.unmanaged_extension_classes=n10s.endpoint=/rdf
