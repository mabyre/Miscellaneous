#  Fusion Intranet / Fructidor

##  But

Fusionner les bases utilisées par les applications fructidor, intranet, photocompo en une base de données mysql.

##  Etat

Des scripts permettent de fusionner la base de données principale de fructidor (mysql) avec la base de donnée d'intranet (firebird) en une base de données mysql.

Ces scripts ont été modifiés pour tenir compte de l'encodage différent des 2 bases. La base de données utilisera utf8.

Rien n'est prévu pour la fusion de la base de données aspsecurity (firebird) dans cette nouvelle base de données.

Cette base de données permet la gestion des utilisateurs de l'application fructidor.

Le nombre important de procédures va poser problème lors de la fusion de cette base de données.

Les colonnes PROPERTYNAMES, PROPERTYVALUESSTRING, PROPERTYVALUESBINARY dans la table PROFILES devraient être remplacées par des tables.

Aucune modification de code n'a été effectuée.

##  Remarques

7 tables sont communes à Fructidor et Intranet

*  fadremail

*  factivite
*  fmarque
*  fproduit
*  fmoredata
*  fadr
*  fcontact




