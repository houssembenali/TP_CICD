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
