#  Livraisons de fructidor


## Attention

Pour la génération des dictionnaires:

*  Les répertoires des 4 sites Fructidor créés dans le répertoire wwwroot doivent se terminer par .en, .es, .fr ou .it.

*  Et le sous-répertoire dico doit être créé si nécessaire pour chacun des sites avec les permissions de modification pour IIs_IUSRS. 


## Livraison de Fructidor sur l'iis local (VirtualBox):

Arrêter les applications fructidor sur le serveur iis

cliquer sur le raccourci 'Developer Command Prompt for VS 2017'.

Modifier la branche du répertoire c:\Users\pnadal\Documents\Visual Studio 2017\Projects\Fructidor4 si nécessaire.

Se rendre dans le répertoire c:\Users\pnadal\Documents\Visual Studio 2017\Projects\Fructidor4

Executer build_fructidor.bat

Cela 

*  Génère l'application dans le répertoire c:\inetpub\wwwroot et déplace les anciennes versions dans des répertoires .old

*  Applique les migrations de la base de données mysql

*  Génère des fichiers .json qui permettent d'afficher des informations git et de migration de la base de données  sur la page **fructidor.fr/_admin/Details.aspx**


Démarrer les applications fructidor sur le serveur iis

L'application peut être testée sur le liens https://www.fructidor.fr, https://www.fructidor.com, ...



## Livraison de Fructidor sur le serveur de recette:



Arrêter le serveur iis

Changer la branche git du répertoire E:/fructidor4 si nécessaire.

Cliquer sur le raccourci 'E:\build_fructidor.bat'.

Cela 

*  Génère l'application dans le répertoire c:\inetpub\wwwroot et déplace les anciennes versions dans des répertoires .old

*  Applique les migrations de la base de données mysql

*  Génère des fichiers .json qui permettent d'afficher des informations git et de migration de la base de données sur la page **fructidor.fr/_admin/Details.aspx**

Démarrer le serveur iis

L'application peut être testée sur le liens https://helios-fr.iocean.fr/, https://helios-en.iocean.fr/, ... (username: helios password: Bananes).



## Livraison de Fructidor sur le serveur de production:

Sur la machine dans VirtualBox

cliquer sur le raccourci 'Developer Command Prompt for VS 2017'.

Modifier la branche du répertoire c:\Users\pnadal\Documents\Visual Studio 2017\Projects\Fructidor4 si nécessaire.

Se rendre dans le répertoire c:\Users\pnadal\Documents\Visual Studio 2017\Projects\Fructidor4

Executer build_fructidor__prod.bat

Cela 

*  Génère l'application dans le répertoire c:\inetpub\wwwroot

*  Génère des fichiers .json qui permettent d'obtenir des informations sur la page **fructidor.fr/_admin/Details.aspx**


Créer un zip avec les 4 répertoire fuctidor-pub.xx créés, les 2 répertoire fructidor4.NET.Static.new et fructidor4.NET.Common.new  et les 4 fichiers create-json-details.bat, install_fructidor_prod.bat, migrations.bat mysqlconfig.cnf du répertoire c:\inetpub\wwwroot.
Copier et décompresser le zip dans le répertoire c:\inetpub\wwwroot sur le serveur de production.


Arrêter le serveur iis


Cliquer sur le raccourci 'c:\inetpub\wwwroot\install_fructidor_prod.bat'.

Cela 

*  Déplace les anciennes versions dans des répertoires .old et les replace les nouvelles versions à leur place.

*  Applique les migrations de la base de données mysql

*  Génère un fichier .json qui permet d'afficher des informations de migrations sur la page fructidor.fr/_admin/Details.aspx

*  Copie des données des anciens répertoires vers les nouveaux.

*  Change les droits sur certains fichiers/répertoires

Démarrer le serveur iis

#  Livraisons de Gespros

## Génération de l'application web et des dll ServiceLibrary.

Sur la machine dans VirtualBox, démarrer Visual Studio 2017, sélectionner le project C:\Users\pnadal\Documents\Visual Studio 2017\Projects\GesprosFlexNet 

Cliquer sur Générer > Régénérer la solution. 

Commit et push des répertoires modifiés
 
## Génération de l'application Flex.

Ouvrir flash builder 4.5 sur la machine de dev Hélios.

A répéter pour les environnements cible dev, recette , prod

*  Click droit sur Gespros IOcean > Propriétés

*  Dans Compilateur Flex modifier les 'Arguments de compilateur supplémentaires' pour tenir compte de l'environnement cible.

*  Puis appliquer > Ok

*  Cliquer sur Projet > Générer le projet.

Commit et push le répertoire C:\Inetpub\WWWROOT\gesprosLite 

Rem: pour le développement générer un fichier gespros.swf permet de tester l'application sur http://localhost:82/gespros.html

## Livraison de Gespros sur les différents serveurs


Arrêter l'application gespros sur le serveur iis

Faire un git pull sur recette. Renommer le fichier gespros_recette.swf en gespros.swf.

(TODO: Déplacer les fichiers modifiés sur le serveur prod ou faire un git pull ou script. )

Démarrer l'application gespros sur le serveur iis

Rem : Vérifier l'accès en écriture du répertoire C:\Inetpub\WWWROOT\gesprosLite\log par IIS_IUSRS

Renommer Web.config__XX


#  Livraisons de Intranet

## Sur le poste de dev avec Visual Studio

Changer la branche des projets intranet, fructidor (EOS est utilisé par fructidor, intranet et ipérion mais n'a pas son répo git) et iperion si nécessaire.

Dans Visual Studio 

choisir la configuration de la solution (debug ou release)

Générer > Générer la solution.

Copier le répertoire intranet dans inetput/wwwroot (sur dev ou sur prod).



## Sur recette ou sur le poste dev d'Hélios

Changer la branche des projets intranet, fructidor (EOS est utilisé par fructidor, intranet et ipérion mais n'a pas son répo git) et iperion si nécessaire.

Lancer le script build-intranet.bat

Copier le répertoire intranet dans inetput/wwwroot

#### Lire la suite [Livraison_2 ](Livraison_2)