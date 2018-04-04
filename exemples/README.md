# Exemples de fichiers CSV portant sur les marchés publics
### D'après l'arrêté du 14 avril 2017 et la spécification d'OpenDataFrance

*Ce répertoire contient des fichiers exemples en format CSV afin de tester le schéma JSON.*

Le premier fichier, `exemple_marche_public.csv` ne retourne pas d'erreurs lorsqu'il est testé.
Le second fichier, `exemple_marche_public_avec_erreurs.csv` a été modifié afin de retourner différentes erreurs.

Ces fichiers ne comportent que des informations fictives et n'a qu'une valeur de test. Ils sont constitués de 5 lignes. La première est un header comportant les noms des différents champs.

```
MARCHE\_ID,  
ACHETEURS\_ID,  
ACHETEURS\_NOM,  
NATURE\_MARCHE,  
MARCHE\_OBJET,  
CPV\_CODE,  
PROCEDURE,  
LIEU\_EXEC\_CODE,  
LIEU\_EXEC\_TYPE,  
LIEU\_EXEC\_NOM,  
DUREE\_MOIS,  
NOTIFICATION\_DATE,  
PUBLICATION\_DATE,  
MONTANT,  
PRIX\_FORME,  
TITULAIRES\_ID,  
TITULAIRES\_ID\_TYPE,  
TITULAIRES\_DENOMINATION,  
MODIF\_OBJET,  
MODIF\_PUBLICATION\_DATE,  
MODIF\_DUREE\_MOIS,  
MODIF\_MARCHE\_MONTANT,  
MODIF\_TITULAIRES\_ID,  
MODIF\_TITULAIRES\_ID\_TYPE,  
MODIF\_TITULAIRES\_DENOMINATION,  
MODIF\_SIGNATURE\_DATE
```

Les 4 autres lignes décrivent un exemple fictif où un acheteur désigne dans un premier temps deux titulaires. Plus tard une modification du marché intervient et ces deux titulaires sont remplacés par un seul.
