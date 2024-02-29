---
title: Piiquante
publishDate: 2022-09-08 00:00:00
img: /assets/hot_takes.png
img_alt: Photos de plusieurs marques de sauce piquante
url: https://github.com/dphiane/OpenClassroom_p6_piiquante
description: |
  Création d’une API sécurisée pour une application d'évaluation.
tags:
  - API REST
  - MongoDB Express
---
Contexte du projet

Piiquante se dédie à la création de sauces épicées dont les recettes sont gardées secrètes. Pour tirer parti de son succès et générer davantage de buzz, l'entreprise souhaite créer une application web dans laquelle les utilisateurs peuvent ajouter leurs sauces préférées et liker ou disliker les sauces ajoutées par les autres.

Spécifications de l'API

    POST /api/auth/signup : Cette route permet de créer un nouvel utilisateur. Le corps de la requête doit inclure une adresse e-mail et un mot de passe. La réponse renvoie un message confirmant la création du compte.

    POST /api/auth/login : Utilisez cette route pour vous connecter à un compte existant. Vous devez fournir une adresse e-mail et un mot de passe dans le corps de la requête. La réponse inclut l'identifiant de l'utilisateur et un token d'authentification.

    GET /api/sauces : Cette route renvoie un tableau contenant toutes les sauces de la base de données.

    GET /api/sauces/:id : Utilisez cette route pour obtenir les détails d'une sauce spécifique en fournissant son identifiant unique.

    POST /api/sauces : Pour ajouter une nouvelle sauce, utilisez cette route avec le nom de la sauce et l'image correspondante dans le corps de la requête. La réponse confirme l'ajout de la sauce.

    PUT /api/sauces/:id : Cette route permet de mettre à jour les informations d'une sauce existante en fournissant son identifiant unique. Vous pouvez envoyer soit un objet JSON contenant les nouvelles informations de la sauce, soit une chaîne de caractères pour la sauce et une nouvelle image.

    DELETE /api/sauces/:id : Utilisez cette route pour supprimer une sauce de la base de données en fournissant son identifiant unique. La réponse confirme la suppression de la sauce.

    POST /api/sauces/:id/like : Cette route permet à un utilisateur de liker ou disliker une sauce spécifique en fournissant son identifiant et le statut de like (-1 pour dislike, 0 pour annuler, 1 pour like). La réponse confirme le changement de statut.

Les erreurs éventuelles doivent être renvoyées telles qu'elles sont produites, sans modification ni ajout. Si nécessaire, utilisez une nouvelle Error().
API Routes

Toutes les routes sauce pour les sauces doivent disposer d’une autorisation (le token est envoyé par le front-end avec l'en-tête d’autorisation : « Bearer <token> »). Avant que l'utilisateur puisse apporter des modifications à la route sauce, le code doit vérifier si l'userId actuel correspond à l'userId de la sauce. Si l'userId ne correspond pas, renvoyer « 403: unauthorized request. » Cela permet de s'assurer que seul le propriétaire de la sauce peut apporter des modifications à celle-ci.
Data Models
Sauce

    userId: String — l'identifiant MongoDB unique de l'utilisateur qui a créé la sauce
    name: String — nom de la sauce
    manufacturer: String — fabricant de la sauce
    description: String — description de la sauce
    mainPepper: String — le principal ingrédient épicé de la sauce
    imageUrl: String — l'URL de l'image de la sauce téléchargée par l'utilisateur
    heat: Number — nombre entre 1 et 10 décrivant la sauce
    likes: Number — nombre d'utilisateurs qui aiment (= likent) la sauce
    dislikes: Number — nombre d'utilisateurs qui n'aiment pas (= dislike) la sauce
    usersLiked: [ "String <userId>" ] — tableau des identifiants des utilisateurs qui ont aimé (= liked) la sauce
    usersDisliked: [ "String <userId>" ] — tableau des identifiants des utilisateurs qui n'ont pas aimé (= disliked) la sauce

Utilisateur

    email: String — adresse e-mail de l'utilisateur [unique]
    password: String — mot de passe de l'utilisateur haché

Exigences de sécurité

    Le mot de passe de l'utilisateur doit être haché.
    L'authentification doit être renforcée sur toutes les routes sauce requises.
    Les adresses électroniques dans la base de données sont uniques et un plugin Mongoose approprié est utilisé pour garantir leur unicité et signaler les erreurs.
    La sécurité de la base de données MongoDB (à partir d'un service tel que MongoDB Atlas) ne doit pas empêcher l'application de se lancer sur la machine d'un utilisateur.
    Un plugin Mongoose doit assurer la remontée des erreurs issues de la base de données.
    Les versions les plus récentes des logiciels sont utilisées avec des correctifs de sécurité actualisés.
    Le contenu du dossier images ne doit pas être téléchargé sur GitHub.

Référence

Ces spécifications définissent les exigences fonctionnelles et de sécurité pour le développement de l'API et de l'application web de gestion des sauces pour Piiquante