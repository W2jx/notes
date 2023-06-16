# Creat portal-cluster

## 1.Download and install docker

### Ubuntu

#### Set up the repository

1.Update the apt package index and install packages to allow apt to use a repository over HTTPS:

>sudo apt-get update

>sudo apt-get install ca-certificates curl gnupg

2.Add Docker’s official GPG key:

>sudo install -m 0755 -d /etc/apt/keyrings

>curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

>sudo chmod a+r /etc/apt/keyrings/docker.gpg

3.Use the following command to set up the repository:

>echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

#### Install Docker Engine

1.Update the apt package index:

>sudo apt-get update

2.Install Docker Engine, containerd, and Docker Compose.

>sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

3.Verify that the Docker Engine installation is successful by running the hello-world image.

>sudo docker run hello-world

4.Modify permissions

>sudo chmod 666 /var/run/docker.sock

5.Verify that the Docker Engine

>docker run hello-world

---

## 2.Build a database

execute under protal project path

>ant -f build-test-local.xml start-docker-database-mysql

---

## 3.Build cluster nodes

Sets currently installed bundle as a 2 node cluster. Configure more nodes with: `-Dnode.count=3`

>ant -f build-test-local.xml setup-portal-cluster

---

# Start the cluster

## 1.start elasticsearch

>cd bundles/elasticsearch-7.17.10/bin && ./elasticsearch

## 2.start portal

 start each node manually one at a time. Wait for first bundle to finish startup before starting the next one.

>cd bundles/tomcat-9.0.73/bin && ./catalina.sh run

>cd bundles-1/tomcat-9.0.73/bin && ./catalina.sh run



* tips

If the cluster is rebuilt, the database needs to be reset

>ant -f build-test-local.xml database-reset

