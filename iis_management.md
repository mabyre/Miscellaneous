Il faut bien prendre quelques notes sur les configurations d'IIS (Internet Information Services) car ce n'est pas si simple ...

Note en forme de ... transmission écrite

FDU : Les logs étaient au format IIS mais quelqu'un à changé le format des Logs sur IIS ...

# En Local

![2018-02-05_13h27_25](/uploads/c76d163a6d631ab9374374c9b0808205/2018-02-05_13h27_25.png)

J'ai réparé le fonctionnement du site en DEV (localhost) en configurant le site "fructidor.static" correctement et puis une proc.bat à supprimer le répertoire sur lequel il pointait j'ai compris alors pourquoi il ne fonctionnait plus en DEV

Et puis j'ai testé les nouvelles procédures de livraison en PROD et j'ai donc créé un site web pour tester cette installation :

![2018-03-09_16h07_36](/uploads/e46a0556b1d7a6db2aa6f9cd081e0d0a/2018-03-09_16h07_36.png)

# En RECETTE

![2018-02-05_14h57_51](/uploads/88953b8aeca392d699c07e9bc231fada/2018-02-05_14h57_51.png)

Deux sites arrêtés ouranos, visionsandtrends

# En PRODUCTION

![2018-01-18_17h15_22](/uploads/af4d75dfda1198b9bf0cfb615d029388/2018-01-18_17h15_22.png)

# IIS Journalisation

Je découvre en PROD 5 Go de journalisation dans le répertoire :

C:\inetpub\logs\LogFiles

![2018-03-20_17h28_06](/uploads/3605dd627c6782de88bcde16d4317d4b/2018-03-20_17h28_06.png)

Et la configuration de la journalisation

![2018-03-20_17h08_10](/uploads/df15a5bc764003e206dfd6f99a751646/2018-03-20_17h08_10.png)

Et un soft pour lire les Logs :

https://gallery.technet.microsoft.com/Log-Parser-Studio-cd458765





