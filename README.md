# HTTP-protocole

## Description

Ce résumé est à vocation d'usage personnel. Son but initial est de m'aider à retenir les informations essentielles concernant le protocole HTTP visant a la réalisation de mon projet WebServ. Ce n'est donc pas complet.

## HTTP, c'est quoi ?

Le protocole HTTP (**Hypertext Transfer Protocol**) est un protocole créé pour le [**World Wide Web**](https://www.google.com/search?q=%23world-wide-web). Ce protocole se veut rapide et léger ; il repose sur une architecture **client/serveur**.

## Format d'une URL HTTP

```
http://<host>[":"port][path]

host : Un nom de domaine internet ou une adresse IP valide.
port : Port réseau. S'il n'est pas spécifié, la valeur par défaut est 80.
path : URI de la ressource. S'il n'est pas spécifié, la valeur par défaut est "/".
[]   : Contenu optionnel.
""   : Contenu littéral (doit apparaître tel quel).
```

## Les formats de temps et de date

En HTTP/1.0, plusieurs formats de date sont acceptés pour assurer la compatibilité entre les systèmes.
Les trois formats officiels sont :

  - **RFC 1123** (le standard recommandé) : `Sun, 06 Nov 1994 08:49:37 GMT`
  - **RFC 850** (obsolète) : `Sunday, 06-Nov-94 08:49:37 GMT`
  - **asctime** (format C de Unix) : `Sun Nov  6 08:49:37 1994`

## Les tables de caractères (Charset)

Une table de caractères représente la façon dont les octets sont convertis en caractères lisibles pour l'humain.
Pour définir ce paramètre dans un en-tête `Content-Type`, on utilise :

```
Content-Type: text/html; charset=<table>
```

Il existe un grand nombre de tables différentes. Exemples courants : *US-ASCII, ISO-8859-1 (Latin-1), UTF-8*.

## Encodage du contenu (Compression)

Pour spécifier si un contenu a été modifié par un système de compression (pour voyager plus vite) et préciser lequel, on utilise l'en-tête `Content-Encoding` :

```
Content-Encoding: "x-gzip" | "x-compress" | transformation
```

*Note : Le client annonce ce qu'il supporte via l'en-tête `Accept-Encoding`.*

## Format d'une requête HTTP

Une requête simple (méthode de la ligne de commande) se structure ainsi :

```
<Méthode> <URL> <Version>
```

Exemple : `GET /index.html HTTP/1.0`

-----

## Les methodes
```
GET : Demande au server des données. Ne l'utiliser que pour la récuperation de données.
POST : Permet l'envoie de données au server permetant son changement d'état. Par exemple lors d'un envoie de formulaire.
DELETE : Demande au server de supprimer une ressource donnée. Une quete DELETE ne doit pas contenir de corp et permet *uniquement* de supprimer des données
```

## BONUS

### World Wide Web

Inventé par [**Tim Berners-Lee**](https://fr.wikipedia.org/wiki/Tim_Berners-Lee), ce projet avait pour but de permettre aux chercheurs du monde entier de s'échanger des informations instantanément.
Le **30 avril 1993**, le **CERN** a placé le logiciel du World Wide Web dans le domaine public. Ce fut le véritable début du Web tel qu'on le connaît.
[Voici un lien vers la toute première page web \!](http://info.cern.ch/hypertext/WWW/TheProject.html)
