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

En HTTP/1.1, le format RFC 1123 est privilégié, mais pour assurer la compatibilité, trois formats sont historiquement acceptés :

* **RFC 1123** (le standard recommandé) : `Sun, 06 Nov 1994 08:49:37 GMT`
* **RFC 850** (obsolète) : `Sunday, 06-Nov-94 08:49:37 GMT`
* **asctime** (format C de Unix) : `Sun Nov  6 08:49:37 1994`

---

# Les champs d'en-tête d'une requête (HTTP/1.1)

## Accept
Ce champ permet de spécifier quels formats de fichiers sont acceptables pour la réponse. Il est utile pour limiter les formats acceptés à un ensemble précis.
Si votre requête vise à recevoir une image, il y a peu d'intérêt à accepter du `text/html`.
```http
Accept: text/html, image/png
```
*Note : Si aucun en-tête `Accept` n'est présent, le serveur suppose que tout format est acceptable (`*/*`).*

## Accept-Charset
Ce champ permet de spécifier les tables de caractères (jeux d'encodage) acceptées pour la réponse.
Une table de caractères représente la façon dont les octets sont convertis en caractères lisibles par l'humain.
```http
Accept-Charset: iso-8859-5, utf-8
```
Si cet en-tête est absent, le serveur **PEUT** estimer que toutes les tables sont acceptées.

## Accept-Encoding
Ce champ permet de spécifier les types de compression acceptés pour la réponse (le transfert).
On parle d'encodage lorsque le contenu est transformé par un algorithme (ex: Gzip) pour réduire sa taille.
```http
Accept-Encoding: compress, gzip
```
Si cet en-tête est absent, le serveur considère qu'aucun encodage de compression n'est requis, bien qu'il puisse techniquement en proposer.

## Accept-Language
Ce champ permet de préciser les langages *naturels* (humains) acceptés pour la réponse.
L'ordre de préférence est désigné par le paramètre `q` (allant de 0 à 1). Sans `q`, la priorité se décide de gauche à droite.
```http
Accept-Language: da, en-gb;q=0.8, en;q=0.7
```
Si aucun en-tête n'est précisé, le serveur **DEVRAIT** considérer que tous les langages sont acceptables, mais servira généralement sa langue par défaut.

## Accept-Ranges
Ce champ de **réponse** permet au serveur d'indiquer qu'il supporte les requêtes partielles (demande d'un morceau de fichier en octets).
```http
Accept-Ranges: bytes
```
Si le serveur n'accepte pas ce mode, il peut spécifier `Accept-Ranges: none`. Cela indique au client qu'il ne peut pas demander seulement une partie du fichier (utile pour le "resume" de téléchargement).

---

# Manipulation du contenu

## Content-Type / Les tables de caractères (Charset)

Pour définir l'encodage utilisé dans le corps de la réponse afin que le client puisse l'afficher correctement :
```http
Content-Type: text/html; charset=utf-8
```
*Exemples courants : US-ASCII, ISO-8859-1 (Latin-1), UTF-8.*

## Content-Encoding (Compression)

Pour spécifier si le contenu a été compressé (pour voyager plus vite) et préciser l'algorithme utilisé :
```http
Content-Encoding: gzip
```
*Note : Le client annonce ce qu'il supporte via l'en-tête `Accept-Encoding`.*

---

# Formats des messages

## Structure générale
```text
<Méthode> <URL> <Version>
<En-têtes>
(Ligne vide)
<Corps du message (Optionnel)>
```

## Exemple de requête minimale
```http
POST /cgi/admin.php HTTP/1.1
Host: localhost
Content-Type: application/x-www-form-urlencoded
Content-Length: 13

user=admin&pw=123
```

## Exemple de réponse minimale
```http
HTTP/1.1 200 OK
Content-Length: 42
Content-Type: text/html

<html><body><h1>Hello World</h1></body></html>
```

---

## Les méthodes principales

* **GET** : Demande une ressource au serveur. Ne doit être utilisé que pour la récupération de données sans modifier l'état du serveur.
* **POST** : Envoie des données au serveur pour traitement (ex: formulaire). Peut modifier l'état du serveur ou créer une ressource.
* **DELETE** : Demande au serveur de supprimer la ressource indiquée.

---

## BONUS : Histoire du Web

Inventé par [**Tim Berners-Lee**](https://fr.wikipedia.org/wiki/Tim_Berners-Lee), le Web avait pour but de permettre aux chercheurs du monde entier de s'échanger des informations instantanément. Le **30 avril 1993**, le **CERN** a placé le logiciel du World Wide Web dans le domaine public.
[Voici un lien vers la toute première page web !](http://info.cern.ch/hypertext/WWW/TheProject.html)
