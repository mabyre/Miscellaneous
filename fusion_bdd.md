# Applications concernées

**Fructidor**

 utilisant la base de données mysql fructidor et la base de données ASP.NET Security.

se connecte à la base de données intranet pour synchroniser les données.

(A vérifier: se connecte à intranet pour générer une partie des annuaires)

**Intranet**

 utilisant la base de données firebird intranet

 Attention
 + configuration dans global.asa
 + configuration dans web.config et eos.config

**Photocompo**

 utilisant la base de données firebird intranet (un serveur  'Firebird Sql Server' sur la prod permet l'accès à distance)

**Gespros**

 utilisant la base de données firebird intranet (voir Gespros\ServiceLibrary\dal\DataAccess.cs).
La partie en flex semble utiliser les services 'fluorinefx' pour accéder aux données.

# Données communes à Fructidor et Intranet et Synchronisation

Sur https://helios-fr.iocean.fr/_admin/Modules/Synchro/
 
 le bouton 'New DB : copy parameters' n'a pas d'utilité. (visible seulement en dev)
 le bouton 'New DB : copy companies' n'a plus d'utilité: Synchro - Intranet / Old Fructidor => New Fructidor (visible seulement en dev)

https://www.fructidor.fr/_admin/Modules/Synchro/Compare.aspx

les 7 tables fadremail, factivite, fmarque, fproduit, fmoredata, fadr, fconctact sont communes aux 2 applications
Parmi ces 7 tables certaines ont le même nom mais n'ont pas la même fonction.
Par exemple, fadremail de la bd intranet doit être renommée en iadremail.

Fcontact est synchronisée dans fructidor depuis intranet (92000 contacts dans Intranet, 1200 dans fructidor).
La synchro se fait dans Fructidor.Corer/Synchro/SynchroSte.cs > CopyContact.
Après la fusion regarder s'il est possible de fusionner les 2 tables (les ID des contacts sont différents entre les deux bases ITR et FRU)

# Etapes

[Modifier les applications pour qu'elles fonctionnent sur la recette.](https://gitlab.iocean.fr/HELIOS/Documentation/wikis/modifications_recette)

-> remplacement des url en dur par des paramètre.

Créer la nouvelle base de données (voir 
https://gitlab.iocean.fr/HELIOS/databases-fusion/blob/master/README.md)


Rem: Synchroniser les bases de données et vérifier s'il n'y a pas de perte de données. (voir les 7 tables fadremail, factivite, fmarque, fproduit, fmoredata, fadr, fconctact communes aux 2 applications)


**Attention** Modifier les scripts pour tenir compte des migrations de fructidor.

Tester au maximum les 4 sites fructidor en recette.

Modifier intranet pour l'accès à la nouvelle base.

Tester intranet en recette.

Modifier gespros pour l'accès à la nouvelle base.

Tester gespros en recette.

Migrer photocompo dans fructidor.

Tester photocompo.

