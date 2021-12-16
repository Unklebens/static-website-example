Fahim's Static Website Example
----------------------

To be used with AJC under Fraze's supervision

# BUILD STATUS

[![Build Status](http://18.207.3.70:8080/buildStatus/icon?job=TP9)](http://18.207.3.70:8080/job/TP9/)


# TP9



## Dockerfile
Cloner https://github.com/Unklebens/static-website-example.git

````
FROM nginx
COPY ./ /usr/share/nginx/html
````

Puis en shell
````
docker build -t fahimx/sitedirane:1.0 .
vi Dockerfile
docker build -t fahimx/sitedirane:1.0 .
docker run -d -p 80:80 fahimx/sitedirane:1.0
````
Test OK

commit
````
git add Dockerfile
git commit -m "+Dockerfile"
git push
````

## Instances EC2

Ubuntu server T2.micro avec userdata et ip publiques dans un SG avec 22 80 et 5000 et meme clé fahim-kp-ajc comme ca le secret Jenkis reste le meme
````
#!/bin/bash
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
usermod -aG docker ubuntu
````


>Fahim-ec2-dockerhost-prod http://3.92.2.219:5000

>Fahim-ec2-dockerhost-staging http://174.129.63.158:5000



Il faut bien entendu 

    1.le bon port dans le Docker run
    2.le ssh -o n'accepste que une commande , pas de &&
    3.nettoyer son env de staging et de prod pour un deploiement futur
    4.Personaliser son application
