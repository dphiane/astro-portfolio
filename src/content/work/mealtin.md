---
title: Symfony Mealtin'Potes
publishDate: 2024-02-25 00:00:00
img: /assets/mealtin.png 
img_alt: Site de réservation Mealtin'Potes
description: |
  Web application gestion des réservation 
url: https://github.com/dphiane/symfony_mealtin
tags:
  - Symfony
  - Mailer
  - Asset Mapper
---

Suite à mon expérience en tant que gérant de mon établissement, j'ai souhaité répondre à mon problème de gestion des réservations et des appels téléphoniques qui monopolisaient du personnel.
Un système d'authentification a été mis en place pour lutter contre les "no-shows", qui sont les réservations non honorées.

#### Fonctionnalités implémentées : :
 -  Mise en place de l'inscription avec un authenticator personnalisé
 -  Login et logout avec AuthenticationUtils
 -  Réintialisation de mot de passe
 -  Page de profil, modification des informations.
 -  Formulaire de contacte
 -  Réservation d'un table via formulaire
 -  Obligation de s'incrire pour authentifier l'utilisateur
 -  Mise en place d'un calendrier avec la désactivation des jours de fermeture
 -  Désactivation des crénaux horaires si le service est plein
 -  Mail de confirmation de réservation et de modification
 -  Possibilité de modifier ou annuler les réservations.
 -  Dans un soucis de d'efficacité des test, l'utilisateurs peut réserver plusieurs fois le même jour.