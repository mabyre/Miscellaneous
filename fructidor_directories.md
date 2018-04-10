

# Procédure d'export des annuaires.


Accéder au [poste de développement Delphi](https://gitlab.iocean.fr/HELIOS/Documentation/wikis/engineering_access)



**Avant chaque export, il faire mettre à jour la base de données e:\inetpub\databases\fadr.gbd**

*Sur le serveur de fructidor:*

*select idadr, idcustomerlevel from fadr*

*Export au format sql dans la table fadr.*

*Supprimer tous les ' dans le fichier sql.*

*Ajouter comme première ligne delete from fadr.*

Récupérer le fichier fadr.gdb sur le poste de dév delphi.

Faire une copie de l'ancienne base de données.

Lancer le script sql. (ne pas oublier de faire le commit s'il n'est pas automatique).





C:/programmesDelphi/photocompo/photocompo.exe



*  Définir un répertoire (le répertoire d'export)
   
   Spécifier où déposer tous les fichiers. Ce répertoire doit être accessible depuis les machines générant des fichiers d'export.

*  Collecter les informations nécessaires à la génération des annuaires

		1.  Date début => Date de validité des adresses : (exemple 01/01/15)

		2.  (Date fin ??) => Facultative / pas renseignée

		3.  Pour WESTERN EUROPE, obtenir ou valider les critères définis dans un fichier excel	

*  Mise à jour de la base de données intranet

	...
	
*  **Génération de l'annuaire PRE & POST HARVEST**

	Se rendre sur la page d'administration de fructidor.

	Sélectionner InDesign Exports

	***Questions:***

		1.  Doit-on exporter AFTL Transport et AFTL Autres Industries? => Oui

		2.  Doit-on exporter dans toutes les langues? => Oui. Pour AFWE, la génération sera en français pr la France, en allemand pr les allemands etc. (selon les pays, la langue est différente).

		3.  A quoi correspond la date? => Date de validité des adresses

	*Adapter en fonction des réponses:*

	Définir la date pour l'export AFTL

	Lancer l'export pour chacunes des langues.

	Définir la date pour l'export AFTL Autres Industries

	Lancer l'export pour chacunes des langues.

	Déplacer les fichiers générés dans le répertoire d'export

	
*  Se rendre sur la machine 'Delphi'

	Lancer l'application photocompo

	***Questions:***

		Dans le fichier excel et le ticket 32015: 

		  Dans photocompo, il y a des éléments à changer dans le code et à recompiler. 

		  Tout est indiqué dans le fichier Excel.

		Cette recompilation concerne-t-elle la génération des annuaires 'CENTRAL & EASTERN EUROPE', 'AFRICA & MIDDLE EAST', 'ASIA, PACIFIC & AMERICAS'


*  **Génération de l'annuaire CENTRAL & EASTERN EUROPE :**

	Spécifer les dates. (attention aux dates qui sont au format mm/jj/aaaa, avec le mois en premier.)

	Cliquer sur bouton AFCEE dans photocompo	

	Déplacer les fichiers générés dans le répertoire d'export


*  **Génération de l'annuaire AFRICA & MIDDLE EAST :** 

	Spécifer les dates. (attention aux dates qui sont au format mm/jj/aaaa, avec le mois en premier.)
	
	Dans le code Delphi, décommenter la requête AFAME (l.235) puis lancer l'application.

	Cliquer sur bouton AFAME dans photocompo	

	Déplacer les fichiers générés dans le répertoire d'export

	
*  **Génération de l'annuaire ASIA, PACIFIC & AMERICAS :** 

	Spécifer les dates. (attention aux dates qui sont au format mm/jj/aaaa, avec le mois en premier.)

	Cliquer sur bouton AFAPA dans photocompo	

	Déplacer les fichiers générés dans le répertoire d'export


*  **Génération de l'annuaire WESTERN EUROPE :**

	Spécifier les dates. (attention aux dates qui sont au format mm/jj/aaaa, avec le mois en premier.)

	Ouvrir le fichier excel spécifiant les critères de l'export

	***Questions:***
		Dans le fichier excel et le ticket 32015: 

		  Dans photocompo, il y a des éléments à changer dans le code et à recompiler. 

		  Tout est indiqué dans le fichier Excel.

		Quels sont ces éléments à changer?

	Pour chacune des lignes et après avoir changé le code et recompiler si nécessaire,

	Sélectionner les paramètres spécifiés dans la ligne excel et cliquer sur Bouton Transférer (à confirmer)
	
	Déplacer les fichiers générés dans le répertoire d'export


*  Vérifications des fichiers

	...
	
*  Compresser les fichiers d'export

...

*  Envoyer des fichiers d'export

...


# Informations techniques

## Annuaires:


AFWE (WESTERN EUROPE) : manuellement selon les critères dans un fichier excel (Voir ticket 32015. !Commentaires dans le fichier excel :recompilation??)

AFCEE (CENTRAL & EASTERN EUROPE) : bouton dans photocompo

AFAME (AFRICA & MIDDLE EAST) : bouton dans photocompo

AFAPA (ASIA, PACIFIC & AMERICAS) : bouton dans photocompo

AFTL ?? depuis fructidor (Administration > InDesign Exports > Export AFTLTransport)
AFPPH (PRE & POST HARVEST) depuis fructidor (Administration > InDesign Exports > Export AFTL Autres Industries)

## PhotoCompo

Le classement influence ProcessAf, ProcessAfDivers

Le pays influence ProcessAf, ProcessAfDivers

La date de début influence ProcessAf, ProcessAfTransport,ProcessAfAutres,ProcessAfDivers, ProcessAfMarques, ProcessAfDar

Les codes postaux influencent Export France, ProcessAf, ProcessAfDivers

La langues influence ProcessAf, ProcessAfTransport, ProcessAfDivers


**Bouton Transférer**

En fonction de la partie sélectionnée,

 génère un fichier

 	AfAlpha.txt (ProcessAf)

 	AfTransport.txt (ProcessAfTransport)

 	AfAutres.txt (ProcessAfAutres)

 	AfCentrales.txt (ProcessAfDivers(IdCentrales))

 	AfSupermarches.txt (ProcessAfDivers(IdSupermarches))

 	AfMarques.txt (ProcessAfMarques)

 	AfMagasinBio.txt (ProcessAfDivers(IdMagasinBio))

 	
**Export France**
 Génère des fichiers Af_France_XX.txt avec XX numéro de département. (ProcessAf)
 
**Export CHA Fr**
??

**Export Dates à retenir**
	Génère le fichier AfDar.txt (ProcessAfDar)
	
	
**Export AfaME, AfCEE, AfaPA**
	(le classement est modifié par les exports lors des exports)
	Génère des fichiers XX_YY.txt  avec XX le code d'annuaire et YY l'id du pays. (ProcessAf)
	afaME tout par ville tout en Anglais
	AfCEE tout par ville tout en Anglais
	AfaPA 
	

## Autres
* InDesign se trouve sur la machine Delphi

* la base de données utilisée par photocompo est accédée à l'adresse 62.244.100.9:Intranet

Il y a un serveur firebird sur le serveur de production. 

Un alias est définit pour Intranet = C:\inetpub\databases\INTRANET.GDB

photocompo se connecte à une autre base de données mais je n'ai pas trouvé son utilité 


Faut-il définir une procédure de mise à jour de la db intranet ou est-elle toujours à jour?


		


-------
# Ouvrir les sources Delphi

1.  Accéder au dossier : C:/programmesDelphi/photocompo/photocompo.exe
2.  Ouvrir le projet "photocompo.dproj"
3.  Une fois le projet ouvert, faire un CTRL+clic sur "Application"
Vous avez ouvert les sources du projet.


## Duplication de l'environnement pour le développement.
C:/programmesDelphi/photocompo-developpement

-------
# Temps de génération

Les durées sont estimatives car elles dépendent du volume de données traitées (en fonction des dates par exemple).

| Export | Durée |
| -------- | -------- |
| AFWE (AF Western Europe)|  |
| AFAPA (AF Asia, Pacific & Americas)|  |
| AFAME (AF Africa Middle East)| 11 min. (date 01/01/2016) |
| AFCEE (AF Central & Eastern Europe)|  |
| AFTL (AF Pre & Post Harvest / Transport-Logistics)|  |


-------
# Génération des annuaires finaux

* [ ]  Avant de générer les annuaires, il faut mettre à jour la base de données FADR à partir de la table de fructidor.**

> *** script à ajouter 

* [ ]  Vérification des annuaires générés 

Dans le fichier, pour les membres Gold, il doit y avoir le balise :
<ParaStyle:MEMBER2>@Gold_en.tif@
juste au dessus de la balise <ParaStyle:SOCIETE2>