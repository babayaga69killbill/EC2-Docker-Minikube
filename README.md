# EC2-Docker-Minikube
installing minikube and docker on ec2
1. sign in to aws and then move to EC2
2. continue with launch instances
3. select your desired prefrences in storage,AMI
4. have a watch and launch
5. select key pair host through putty
![](https://github.com/babayaga69killbill/EC2-Docker-Minikube/blob/main/holocaust/Screenshot%202025-09-06%20203355.png)

# DOCKER.md
# docker-install


### Quick Install
```bash
curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash
```
---

install packages:
```bash
sudo apt update
sudo apt install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    jq
```

Add Docker’s official GPG key:
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

setup repository:
```bash
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Install Docker Engine:
```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

Add your user to the docker group:
```bash
sudo usermod -aG docker $USER
```

### Docker Compose

download the current stable release of Docker Compose:
```bash
COMPOSE_VERSION=$(curl -s "https://api.github.com/repos/docker/compose/tags" | jq -r '.[0].name')
sudo curl -L "https://github.com/docker/compose/releases/download/${COMPOSE_VERSION}/docker-compose-$(uname -s)-$(uname -m)" \
  -o /usr/local/bin/docker-compose
```

Apply executable permissions to the binary:
```bash
sudo chmod +x /usr/local/bin/docker-compose
```
# PULL IMAGES 
```bash
 docker pull hello-world
```
```bash
 docker pull nginx
```
```bash
docker pull ubuntu/apache2
```
# SEE IMGAGES/INSPECT
```bash
 docker images
```
```bash
 docker inspect
```
```bash
  docker ps
```
# PORT FORWADING 
```bash
docker run --name mynginxl -p 80:80 -d nginx
```
```bash
docker run --name myapache -p 80:80 -d ubuntu/apache2
```
# KILLING IMAGE
```bash
docker kill mynginxl
```
![](https://github.com/babayaga69killbill/EC2-Docker-Minikube/blob/main/holocaust/WhatsApp%20Image%202025-09-07%20at%2000.05.24_4768f18c.jpg)
# for installing minikube
```To install the latest minikube stable release on x86-64 Linux using binary download:

curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
2Start your cluster
From a terminal with administrator access (but not logged in as root), run:

minikube start
If minikube fails to start, see the drivers page for help setting up a compatible container or virtual-machine manager.

3Interact with your cluster
If you already have kubectl installed (see documentation), you can now use it to access your shiny new cluster:

kubectl get po -A
Alternatively, minikube can download the appropriate version of kubectl and you should be able to use it like this:

minikube kubectl -- get po -A```

