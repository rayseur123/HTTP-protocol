---

# HTTP-protocole

## Description
Ce résumé est à vocation d'usage personnel. Son but initial est de m'aider à retenir les informations essentielles concernant le protocole HTTP visant à la réalisation de mon projet **WebServ**. Ce n'est donc pas complet.

## HTTP, c'est quoi ?
Le protocole HTTP (**Hypertext Transfer Protocol**) est un protocole créé pour le [**World Wide Web**](https://www.google.com/search?q=%23world-wide-web). Ce protocole se veut rapide et léger ; il repose sur une architecture **client/serveur**.

## Format d'une URL HTTP
```text
http://<host>[":"port][path]

host : Un nom de domaine internet ou une adresse IP valide.
port : Port réseau. S'il n'est pas spécifié, la valeur par défaut est 80.
path : URI de la ressource. S'il n'est pas spécifié, la valeur par défaut est "/".
[]   : Contenu optionnel.
""   : Contenu littéral (doit apparaître tel quel).
```

## Les formats de temps et de date
Trois formats sont historiquement acceptés :
* **RFC 1123** (le standard recommandé) : `Sun, 06 Nov 1994 08:49:37 GMT`
* **RFC 850** (obsolète) : `Sunday, 06-Nov-94 08:49:37 GMT`
* **asctime** (format C de Unix) : `Sun Nov  6 08:49:37 1994`

---

# Les champs d'en-tête (HTTP/1.1 | 1.0)

## Host (OBLIGATOIRE en 1.1 | OPTIONNEL en 1.0)
Spécifie le domaine et le port du serveur. En HTTP/1.0, un serveur l'ignore généralement car il ne gère qu'un seul domaine par IP.
```http
Host: localhost:8080
```

## Accept
Spécifie quels formats de fichiers sont acceptables pour la réponse.
```http
Accept: text/html, image/png
```

## Accept-Charset
Spécifie les tables de caractères (jeux d'encodage) acceptées.
```http
Accept-Charset: iso-8859-5, utf-8
```

## Accept-Encoding
Spécifie les types de compression acceptés.
```http
Accept-Encoding: compress, gzip
```

## Accept-Language
Précise les langages naturels (humains) acceptés. Le paramètre `q` désigne l'ordre de préférence.
```http
Accept-Language: da, en-gb;q=0.8, en;q=0.7
```

## Allow (OBLIGATOIRE en 1.1 pour l'erreur 405 | INFORMATIF en 1.0)
Indique les méthodes possibles sur une URL précise.
```http
Allow: GET, POST
```

## Authorization
Gère l'authentification en spécifiant l'utilisateur et le mot de passe.
```http
Authorization: Basic YWRtaW46MTIzNA==
```

## Content-Encoding
Spécifie si le contenu a été compressé et précise l'algorithme utilisé.
```http
Content-Encoding: gzip
```

## Content-Type (OBLIGATOIRE si corps présent) / Charset (Parametre optionnel)
Définit l'encodage utilisé dans le corps de la réponse et le type de média.
```http
Content-Type: text/html; charset=utf-8
```

## Content-Language
Indique le public cible du contenu (ex: français, allemand).
```http
Content-Language: da
```

## Content-Length (OBLIGATOIRE si corps présent)
Précise la taille du contenu envoyé sous forme d'octets.
```http
Content-Length: 600
```

## Date (OBLIGATOIRE en réponse)
Précise la date et l'heure du message.
```http
Date: Tue, 15 Nov 1994 08:12:31 GMT
```

## Expires
Précise quand le contenu envoyé est obsolète.
```http
Expires: Thu, 01 Dec 1994 16:00:00 GMT
```

## From
Précise l'e-mail du client.
```http
From: webmaster@w3.org
```

## If-Modified-Since
Utilisé avec un GET pour conditionner l'envoi de données selon une date.
```http
If-Modified-Since: Sat, 29 Oct 1994 19:43:31 GMT
```

## Last-Modified
Spécifie la date de la dernière édition du contenu renvoyé.
```http
Last-Modified: Tue, 15 Nov 1994 12:45:26 GMT
```

## Location
Renvoie l'URL réelle (chemin absolu) lors d'une redirection (codes 3xx).
```http
Location: http://www.w3.org/hypertext/WWW/NewLocation.html
```

## Pragma
Utilisé pour indiquer le non-cache des données (compatibilité 1.0).
```http
Pragma: no-cache
```

## Referer
Précise l'URL de la page précédente.
```http
Referer: http://www.w3.org/hypertext/DataSources/Overview.html
```

## Retry-After
Indique le temps d'attente lors d'une indisponibilité (503).
```http
Retry-After: 900
```

## Server
Informations sur le logiciel du serveur.
```http
Server: MonWebServ/1.0
```

## User-Agent
Informations sur le logiciel client (navigateur).
```http
User-Agent: CERN-LineMode/2.15 libwww/2.17b3
```

## WWW-Authenticate (OBLIGATOIRE en réponse 401)
Indique au client qu'il doit fournir des identifiants.
```http
WWW-Authenticate: Basic realm="WallyWorld"
```

---

# Exemples de messages

## Requête la plus minimale (HTTP/1.0)
```http
GET / HTTP/1.0

```
*(Note : En HTTP/1.0, aucun en-tête n'est strictement obligatoire. La ligne vide après la première ligne suffit.)*

## Requête complète (HTTP/1.0)
```http
POST /submit-form HTTP/1.0
User-Agent: Mozilla/5.0
Accept: text/html, image/png
Content-Type: application/x-www-form-urlencoded
Content-Length: 17

user=paul&age=25
```

## Réponse complète (HTTP/1.0)
```http
HTTP/1.0 200 OK
Date: Tue, 21 Apr 2026 14:00:00 GMT
Server: MonWebServ/1.0
Content-Type: text/html; charset=utf-8
Content-Length: 44

<html><body><h1>Succes !</h1></body></html>
```

---

## Les méthodes principales
* **GET** : Demande une ressource. Utilisé uniquement pour la récupération.
* **POST** : Envoie des données pour traitement.
* **DELETE** : Demande la suppression d'une ressource.

## BONUS : Histoire du Web
Inventé par [**Tim Berners-Lee**](https://fr.wikipedia.org/wiki/Tim_Berners-Lee). Le **30 avril 1993**, le **CERN** a placé le logiciel du World Wide Web dans le domaine public.
[Lien vers la première page web !](http://info.cern.ch/hypertext/WWW/TheProject.html)
