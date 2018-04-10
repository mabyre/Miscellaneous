# Objectifs
Faire la liste des outils utilisés dans le développement de la Plateforme. Faire vivre cette liste car elle n'est pas à jour.

# Outils tiers
Basé sur le document de référence : Helios -- 01 -- Generalites.doc - Chp 4. Référence des outils tiers intégrés dans les applications

## FCK Editor
### éditeur de texte wysiwyg pour HTML :
* régulièrement mis à jour dans les projets pour des questions de sécurité
* version actuelle utilisée : 3.61
* généralement située dans le dossier editor_361
* ne pas installer dans le dossier par défaut (en cas de faille de sécurité)

http://ckeditor.com/


## Jquery
### Framework Javascript
* versions actuellement utilisées (selon les projets) : 1.2.6 ou 1.4.4
* stable et donc rarement mis à jour dans les projets
* utilisation ponctuelle de composants tiers basés sur Jquery

http://jquery.com/


## Lucene
### indexation et recherches hypertext (en .NET)
utilisé en .NET

http://incubator.apache.org/lucene.net/


## Awstats
### pour statistiques de fréquentations basées sur les log de IIS 

http://awstats.sourceforge.net/

`Rem :` Ce n'est plus à jour quelqu'un à modifier le format des Logs qui est devenu incompatible d'avec Awstats.


### Log4Net
* utilisé dans le site Fructidor pour des statistiques sur les recherches
* utilisé en .NET

http://logging.apache.org/log4net/

### SasqChart
utilisé dans l’Intranet pour générer des graphiques statistiques
DLL en .NET

http://www.sasq.co.uk/Default.aspx

### Cairngorm MVC
Framework MVC pour ActionScript
utilisé en Flex pour Gespros
framework opensource d’Adobe

http://opensource.adobe.com/wiki/display/cairngorm/Cairngorm

### FluorineFX – interface AMF entre flash et .NET  pour les webservices
utilisé en .NET pour Gespros

http://www.fluorinefx.com/

### FlexLib – bibliothèque d’utilitaires Flex
utilisé en Flex pour Gespros

http://code.google.com/p/flexlib/

# Référence des API externes utilisées dans les applications

## Paypal
### Système de paiement en ligne
Paypal est utilisé pour les paiements dans les sites Web (abonnements ou membres référencés dans Fructidor).

## Google MAP
Utilisée sur le site Fructidor et l’Intranet pour localiser les entreprises.

# Autres Tools ésotériques

### IIS URL Rewrite Extensibility Samples
Je découvre ce soft comme tools installé sur la machine de DEV mais à quoi sert-il ? En téléchargeant RewriteExtensibility.msi depuis le site je peux réparer ce soft.

https://www.microsoft.com/en-us/download/details.aspx?id=43353

