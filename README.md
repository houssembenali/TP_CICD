# TP_CICD


# lien de l'image docker public
https://hub.docker.com/r/houssembenali/tp-cicd-ib

## DOCKER 

### TAG DU L'IMAGE

docker build . -t timgnh/tpcicd:v1

### POUSSER UNE IMAGE SUR UN REFERENCIEL

```
docker login --username username --password password
docker push timgnh/tpcicd:v1
```
docker login --username timgnh --password 123AZEqsd

### DROIT SU POUR UTILISATEUR DOCKER

- Créer le groupe docker s'il n'existe pas
    $ sudo groupadd docker
- Ajoutez votre utilisateur au groupe docker.
    $ sudo usermod -aG docker $USER
    $ sudo chmod 777 /var/run/docker.sock
- Exécutez la commande suivante ou Déconnectez-vous et reconnectez-vous et exécutez (cela ne fonctionne pas, vous devrez peut-être d'abord redémarrer votre machine)
    $ newgrp docker
- Vérifiez si docker peut être exécuté sans root
    $ docker run hello-world
- Redémarrez si l'erreur persiste
    $ reboot

## JENKINS

<p>Le serveur Jenkins est accèsible sur le port 8080</p>
<p>Exemple : http://192.168.1.120:8080/</p>

- Verification que Jenkins est bien démarrer

```
sudo service jenkins status
```

- Démarrer Jenkins manuellement

```
$ sudo /etc/init.d/jenkins restart
Usage: /etc/init.d/jenkins {start|stop|status|restart|force-reload}
```
### JENKINS FILE

Configurez les variables globales du jenkins file avant de l'executer 
```
    USER="UTILISATEUR"
    PASSWORD="MOT DE PASSE"
    TAG="timgnh/tp-cicd-ib"
    JENKINS_SERV="http://192.168.1.30:3000"
    SOURCE_GIT="https://github.com/houssembenali/TP_CICD.git"
```