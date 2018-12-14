# homework-eServices
homework de la 4ème séance des traveaux pratiques dans le cadre du cours eServices.
Il s'agit de la création et du déploiement d'un microservices sur plusieurs instances. 
Ce TP a été réalisé avec les outils suivants: 
* Spring Boot Version: 1.5.8
* Spring Cloud Version 1.2.4
* Java Version 1.8.0_121
* Maven Version 3.5.2
* IntelliJ IDEA Version Ultimate

## Architecture Proposée:

L'objectif de ce travail est de montrer comment créer plusieurs services indépendamment déployables qui communiquent entre eux, en utilisant les facilités offertes par Spring Cloud et Spring Boot. Spring Cloud fournit des outils pour les développeurs pour construire rapidement et facilement des patrons communs de systèmes répartis (tel que des services de configuration, de découverte ou de routage intelligent). Spring Boot permet de son côté de construire des applications Spring rapidement aussi rapidement que possible, en minimisant au maximum le temps de configuration, d'habitude pénible, des applications Spring.
Nous allons donc créer les microservices suivants:

Product Service : Service principal, qui offre une API REST pour lister une liste de produits.
Config Service : Service de configuration, dont le rôle est de centraliser les fichiers de configuration des différents microservices dans un endroit unique.
Proxy Service : Passerelle se chargeant du routage d'une requête vers l'une des instances d'un service, de manière à gérer automatiquement la distribution de charge.
Discovery Service: Service permettant l'enregistrement des instances de services en vue d'être découvertes par d'autres services.
L'architecture résultante aura l'allure suivante:

![alt text](https://insatunisia.github.io/TP-eServices/img/tp4/archi.png)

Le code source des 4 projets figure dans ce repo. 

## Dockeriseation des différents microservices:

Il s'agit de conteneuriser les services avec Docker. 
###### 1- Installation de Docker:
Instaler Docker depuis le site officiel: https://docs.docker.com/install/

###### 2- Ajouter la configuration suivante aux fichiers pom.xml de chaque projet :

Ce code permettera l'automatisation de la génération des docker image à partir de chaque Spring boot projet avec Maven et ceci grâce au pluggin io.fabric8 (docker-maven-plugin) .
