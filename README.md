## OpenVAS/Greenbone Docker Install
## Max Johnson

# Docker Install
```
sudo apt update
sudo apt install ca-certificates curl gnupg lsb-release
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
sudo usermod -aG docker maxjohnson
```

# Openvas Install
```
docker top openvas
sudo apt-get install docker.io
sudo service docker status
sudo docker run -d -p 443:443 --name openvas mikesplain/openvas
```
### Openvas running on my Ubuntu Machine
<img width="1680" alt="Screen Shot 2021-11-16 at 5 11 11 PM" src="https://user-images.githubusercontent.com/42543469/142081128-e82c1292-bd08-4767-afde-80c2780113b4.png">

### docker-compose.yml
```
version: '3.3'
services:
    openvas:
        ports:
            - '443:443'
        container_name: openvas
        image: mikesplain/openvas
```

# Links Used
https://github.com/mikesplain/openvas-docker
