Vous en conviendrez rapidement, [Livraisons](Livraisons) ne suffit pas ...

Essayons d'être clair, on utilise des "Profiles de publication" pour publier les "Applications Web" or on en a 4 à publier, il donc qu'elles atterrissent dans le bon répertoire après publication.

>
Donc fructidor-**dev**.fr c'est sur la plateforme de **RECETTE**
et fructidor-**pub**.fr c'est pour la plateforme de **PRODUCTION**

Ainsi les procédures :
* build_fructidor.bat
* build_fructidor_prod.bat
* build_fructidor_rec.bat

Ne peuvent pas être laissées comme cela, ni être utilisées tel quelles ...

Une première chose :

Il existait des "Evènements de build" en pré-build :

xcopy "$(ProjectDir)..\fructidor4.NET.Common\*.*" "c:\inetpub\wwwroot\fructidor4.NET.Common.new" /Y /I /E
xcopy "$(ProjectDir)..\fructidor4.NET.Static\*.*" "c:\inetpub\wwwroot\fructidor4.NET.Static.new" /Y /I /E

Provoque une copie à chaque fois que l'on Build or c'est quand on publie que l'on souhaite avoir les derniers fichiers NET.Common et NET.Static autrement il inutile de les copier sans arrêt.

# Livrer en RECETTE
Un Repository Git complet est installé sur la machine de RECETTE.

Donc on récupère la dernière version des sources de la **branche development**, en faisant un petit :

`
git checkout development
git pull
`

La procédure **build_fructidor_rec.bat** utilise le profile de Publish-Dev pour générer et déployer sur la RECETTE.

# Livrer en PRODUCTION
Il faut générer "builder" avec le profile "Publish-pub" depuis la machine de DEV pour créer les packages à déployer dans le répertoire c:\inetpub\wwwroot de la machine de DEV. Ces packages zippés seront ensuite copiés dans la répertoire c:\inetpub\wwwroot de la machine de PRODUCTION.

Le reste de la procédure est décrit dans Livraison ...

Depuis la machine DEV, on exécute la procédure **build_fructidor_prod.bat** dans la console : **VsDevCmd.bat** en mode administrateur pour configurer l'environnement nécessaire aux Build des projets.

1. Vérifier l'état du code source de la **branche master**, dans une console classique lancer un petit :
`
git checkout master
git pull
`
1. Générer les projets à l'aide de la procédure build_fructidor_prod.bat exécutée dans la console VsDevCmd.bat
1. Faire un gros Zip (packages à déployer) à l'aide de la procédure **make_zip_prod.bat**
1. Copier ce Zip dans "C:\inetpub\wwwroot\" de la machine de production, déziper
1. **Sauvegarder la base de données de PROD**
1. Exécuter alors la procédure de déploiement des packages **install_fructidor_prod.bat**

Vous remarquez que les répertoire livrés ont alors "l'extension" "-pub" (comme publication)

* [ ] Quand on regarde la procédure install_fructidor_prod il faut bien penser que les packages déployés sont nommés "-pud" et qu'ils vont écraser les packages installés. Donc on copie d'abord ce que l'on souhaite sauvegarder de la précédente version, dans les répertoires "-pub". 

# Environnement de PRE-PRODUCTION
La procédure install_fructidor_prod.bat peut être utilisée sur la machine de DEV pour installer le Soft de PROD sur la machine de DEV

# Prévoir un "retour en arrière"
Un fois la mise en PROD effectuée, si les tests en sont pas concluants, il faut pouvoir revenir en arrière, remettre en place l'ancienne version. C'est le but de la procédure **revert_fructidor_prod.bat**

Il faut donc :
* Sauver la BD de prod
* Sauver les packages
