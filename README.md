# HTTP-protocole

## Description
Ce résumé est à vocation d'usage personnel. Son but initial est simplement de m'aider à retenir les informations essentielles concernant le protocole HTTP.

## HTTP c'est quoi ?
Le protocole HTTP (Hypertext Transfer Protocol) est un protocole crée pour le [**World Wide Web**](#World-wide-web). Ce protocol se veut rapide et léger et necessite une relation client/server

## Format d'un url HTTP
```
http://<host>[":"port][path]

host : Un nom de domaine interet ou une address ip valide.
port : Port réseau, si il n'est pas spécifié alors ce sera 80
path : URI, si il n'est pas spécifié alors ce sera '/'
[] : Contenue optionel.
"" : Contenue literal.
```

## La gestion des dates
En http1.0 plusieurs format de date sont disponible. Je vous laisse donc en prendre connaissance si cette partie vous interesse.
Format :
```
- rfc1123-date
- rfc850-date
- asctime-date
```

## Format d'une requete HTTP
```
<Commande> <URL> <Version>
```
## BONUS

### World Wide Web
Inventé par [**Tim Berners-Lee**](https://fr.wikipedia.org/wiki/Tim_Berners-Lee), ce projet avait pour but de permettre au chercheurs du monde entier de s'échanger des informations instantanément.
Le **30 avril 1993** le **CERN** mis l'application W3 libre d'acces. Ce fus donc les debuts du web.
[Voici un lien pour la 1er page web !](http://info.cern.ch/hypertext/WWW/TheProject.html)
