# Sommaire :
  - [Création des images] (#creation-des-images)


# 1. Création des images 

![1- build des images](https://github.com/lionel-kg/ynov-resource/assets/56402311/ff8ca3b1-baf1-4bc0-b55a-d3ecc3331095)

![2-toutes les images creer](https://github.com/lionel-kg/ynov-resource/assets/56402311/6c6294cc-7646-4fbd-8f16-fd56dc0bdbca)

Dans un premier temps nous avons créer les Dockerfile de chaques fonctionnalités et puis nous avons créer le fichier docker-compose-build.yaml à la racine du projet pour builder nos images.


# 2. Création du registre

![3- création registry](https://github.com/lionel-kg/ynov-resource/assets/56402311/6226a22b-6060-4dd0-a010-faae794da777)

Nous avons crée le container registry sur le port 5003:5000 ce qui nous permet de récupérer les registres en écoutant le port 5003.

![4-creation front registry et network registry](https://github.com/lionel-kg/ynov-resource/assets/56402311/28d1cff7-0378-4329-a62e-54ad0c85f259)

Nous avons crée un nouveau container afin d'afficher les registres avec une interface graphique sur un site sur le port 8086. Celui-ci utilise le registre nommé registry (sur l'image il se nomme registry-eval mais nous l'avons modifié) et est sur le même network que le registry. 
Nous avons exposé le port 8086 à l'aide du port forwarding. 

![5-push images sur le registre](https://github.com/lionel-kg/ynov-resource/assets/56402311/a3726022-84c8-44ca-8035-393462fca1d8)

![7-images redis et postgres](https://github.com/lionel-kg/ynov-resource/assets/56402311/d40d7ddb-9375-412c-85c8-686e7c013910)

Nous avons dû taguer chacune de nos images pour les push sur notre registre.

![image](https://github.com/lionel-kg/ynov-resource/assets/56402311/0c1dbaf0-5c7c-4dd2-b7b8-8bdc53cf16bc)

Comme vous pouvez le voir, les images apparaissent bien dans le registre.

# 3. Finalités

![final docker compose running](https://github.com/lionel-kg/ynov-resource/assets/56402311/c7eb1ded-4135-4975-a00f-4228c600b207)

Nous avons crée notre compose.yaml à la racine de notre projet qui nous a permit de créer tous les container à partir des images de notre registre privé

En lançant la commande docker-compose-up nous pouvons voir que tous nos container ont été crées efficacement. 

A la fin de toutes ces étapes vous devriez avoir les informations suivantes : 

![docker info](https://github.com/lionel-kg/ynov-resource/assets/56402311/0a676437-03f3-4ee1-8283-8f7e42b7fac6)

![forwarding port](https://github.com/lionel-kg/ynov-resource/assets/56402311/dda66658-27f6-49ea-bee1-5bedb4e279b7)

En accédant au localhost:5002 vous devriez avoir le vote chien / chat. 

![vote](https://github.com/lionel-kg/ynov-resource/assets/56402311/8b3a96f1-2061-4111-9d1d-dfb846285f34)

Finalement, en accédant au localhost:5001 vous devriez voir les résultats des votes. Cependant étant donné qu'il y a une erreur avec la connexion à la DB, nous n'avons pas les résultats en temps réel.

![image2](https://github.com/lionel-kg/ynov-resource/assets/56402311/184bc473-879e-4b99-a887-07f695292a2a)

