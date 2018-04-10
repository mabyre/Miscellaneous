# Dette technique

## Remplacer l'utilisation de string par des arrays.

Dans le code, on peut trouver des listes de valeurs qui sont concaténées en string pour plus tard être 'splittées' avant leur utilisation.

Example: 
Data.Providers.FOfferProvider GetAreaListId(int idOffer): création d'une chaine de caractères à partir d'une liste d'id en ajoutant des séparateurs (puis en supprimant le dernier séparateur).
AreaSearch.GetNameByIdList : récupère la chaine de caractères pour la splitter, pour obtenir des strings qui sont concaténés en ajoutant des séparateurs (puis en supprimant le dernier séparateur)

## Ajout de documentation

*  Dans les fichiers Web.config
*  Pour les fonctions
*  ...

## Offres principales

Il est possible de supprimer une offre principale, mais tous les changements nécessaires ne sont pas effectué en bd:

select distinct idOfferMain from FOffer where not idOfferMain in (select idOfferMain from FOffer where idOffer = idOfferMain);


ProcessOffer: cannot find main offer - idOfferMain=18634 > Pas d'offre en anglais dont l'idOffer = 18634.

Que faire quand on supprime une offre principale?
Que faire quand on supprime l'offre en anglais liée à une offre principale?

## 4 sites fructidor, en 4 langues !!!

Commencer par internationaliser le site d'une langue. 

Choisir fr et ajouter les fonctionnalité manquante de en.

! aux images

Ajout des fichiers pour les autres langues.

...

## Création d'un site 'mobile'

Le site fructidor n'est pas adapté aux mobiles.

Cela pourrait être un bon point de départ pour rajeunir le site Fructidor.

Le site 'mobile' serait créé directement avec:

 - l'internationalisation

 - bootstrap ou équivalent

 - api rest

 - angular, ... 

 - tests unitaires

 - ...

Cela permettra de garder le site Fructidor en place tout en testant une version plus moderne.


## Code mort

Trouver et supprimer

## Tests

Ajouter des tests automatiques

## Analyse du code avec Visual Studio

Renommer les méthodes en utilisant les recommandations

Voir les autres warnings 

## Mettre à jour les librairies

jquery 1.4.4

## Base de données

Manque des foreign keys

## Projet EOS

Le projet EOS est utilisé par fructidor, intranet (et iperion).

EOS devrait avoir son propre répertoire git et non se trouver dans celui de fructidor. 

(voir https://stackoverflow.com/questions/6680709/create-new-git-repo-from-already-existing-repos-subdirectory)

## Projet Intranet

Il est, en partie, en VBScript ASP. Il faut donc installer "Classic ASP" pour le faire fonctionner.

## Perte de connaissances
A l'heure actuelle personne ne sait comment fonctionne la partie du projet nommée : fructidor4.NET.Static elle comporte pourtant un script fructidor4.NET.Static\js\jclass.js dans lequel il y a une fonction mainTabManager qui est utilisée dans la page d'accueil du site !

Très peu ou pas de documentation sur la configuration des Server IIS qui sont pourtant au coeur des applications web.

## Gestion des images en configuration
Ce n'est pas bétonné

Je suppose que les images dans le répertoire fructidor4.NET.Image changent tout le temps du coup les précédents n'ont pas jugé bon de les mettre en gestion de Conf mais ... sans elles le site ne fonctionne pas ... 

## Test & Validation
Il n'y a aucun jeux de Tests, aucune donnée de validation. Le client n'en comprend même pas l'utilité.
Il faudrait des jeux de tests et un simili plan de validation.

Les données en PRODUCTION de ne cessent d'augmenter, il y a des répertoires avec des dizaines de milliers de fichiers.

## Utilisation de IIS Express en DEV 
C'est une fausse bonne idée ce "petit serveur internet" est là pour de petite applications simples sans gros besoin de configuration. Ce n'est pas le cas pour les applications Hélios qui ont besoin de multiples sites pour fonctionner. Conséquence en Debug avec la machine de Dev certaines actions sont impossibles !

## Conclusion
La dette technique n'a cessée d'augmenter depuis ... je me permet de dire qu'elle fut certainement réduite par la prise en main effectuée par IOCean et enfin la mise en place d'outils de production logiciel un tant soit peu professionnels sinon je ne serais jamais venu. Mais la dette technique à continuée d'augmenter par la suite car les moyens de développement en ressources humaines n'ont jamais été suffisant pour effectuer les chantiers qui auraient permis de réduire cette dette.

Voilà si vous avez lu jusque là c'est bien, c'est le strict minimum pour avoir une vision un peu globale de cet écosystème mais vous ne tarderez pas à comprendre également que si le nécessaire (à évaluer selon votre culture) n'est pas réalisé cette plateforme va exploser toute seule et ce jour là si vous êtes encore là, vous allez pleurer croyez-moi. Moi heureusement, je serais déjà loin ;)
