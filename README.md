# Spécification SCDL relatif aux données essentielles dans la commande publique française
### D'après l'arrêté du 14 avril 2017 et la spécification d'OpenDataFrance

*Ce dépôt contient un fichier schéma JSON de validation des données essentielles des marchés publics.*

L'arrêté du 14 avril 2017 relatif aux données essentielles dans la commande publique définit le cadre de l'ouverture des données des marchés publics. Ainsi, au 1er octobre 2018, les données de tous les marchés supérieurs à 25 000 euros devront être publiées en Open Data sur le profil d'acheteur.

## Le projet Qualidata

L'objet du projet [Qualidata](http://www.opendatafrance.net/outil-de-qualification-des-donnees-ouvertes-qualidata/) est de valider la qualité des données publiées ou en passe d'être publiées par les collectivités. 
Pour un certain nombre de sujets, ces données peuvent ou doivent obéir à des schémas : [Socle commun des données locales](http://opendatalocale.net/scdl/), élaboré par [OpenDataFrance](http://www.opendatafrance.net), ou normes juridiques édictées par l'État (comme pour les [subventions](https://www.legifrance.gouv.fr/eli/arrete/2017/11/17/PRMJ1713918A/jo/texte) ou les [marchés publics](https://www.legifrance.gouv.fr/eli/arrete/2017/11/17/PRMJ1713918A/jo/texte)).
Lorsque c'est le cas, on peut vérifier qu'un jeu de données (en CSV, par exemple) respecte effectivement ce schéma.
Pour ce faire, on s'appuie sur un paradigme, celui de [Frictionless Data](https://frictionlessdata.io/). Dans la variante à laquelle on a recours, les [Tabular Data Package](https://frictionlessdata.io/specs/tabular-data-package/), il s'agit fondamentalement d'un fichier CSV avec les données et d'un fichier JSON qui comprend les métadonnées (description du fichier et des champs). Ces métadonnées (en tout cas celles portant sur les champs) peuvent relever d'un [schéma formel](https://frictionlessdata.io/guides/table-schema/). Ce schéma peut alors être utilisé pour valider les données, par exemple via [goodtables](https://frictionlessdata.io/guides/validating-data/). Ce schéma s'exprime sous la forme d'un fichier en json et décrivant les contraintes s'appliquant aux champs.

## Le schéma JSON

Le schéma JSON fonctionne en utilisant la vérification proposée par [Goodtables pour Python](https://github.com/frictionlessdata/goodtables-py) sur des fichiers CSV. Les fichiers CSV doivent comporter 26 champs nommés et ordonnés ainsi :

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

L'arrêté précise que certains champs sont de type "objet" ou "liste d'objets". Ces types étant difficilement compatibles avec le format CSV, le schéma JSON présuppose des valeurs atomiques, avec une seule donnée par champ. Lorsque le marché public contient plusieurs acheteurs ou plusieurs titulaires la ligne entière est recopiée autant de fois qu'il y a d'acheteurs, et seules les données relatives aux différents acheteurs varient.

Lorsqu'il y a plusieurs acheteurs et plusieurs titulaires chaque combinaison de ligne est écrite dans le fichier CSV. Pour 3 acheteurs et 3 titulaires, les données essentielles du marché public tiendront donc sur 9 lignes. En cas de modification c'est le même principe qui prévaut, toutes les combinaisons possibles doivent être intégrées.

Afin de se conformer à ce format, les modifications suivantes ont été faites par rapport à la spécification d'OpenDataFrance 1.0.

- Le champ "ACHETEURS_LISTE", de type "liste dobjets", a été supprimé.
- Le champ "TITULAIRES_LISTE, de type "liste d'objets", a été supprimé.
- Le champ "MODIFICATIONS_LISTE", de type "liste d'objets" a été supprimé.

Une proposition de nouvelle spécification (1.1), qui tient compte de ces ajustements, a été ajouté dans le dossier "referentiels".

## Améliorations potentielles

- Continuer le travail sur les contrats de concession et les marchés de défense et de sécurité.
- Utiliser des "integer" au lieu des "strings" lorsqu'il s'agit de champs composés exclusivement de nombres entiers.
- Utiliser la propriété "Enum" pour contrôler les données devant se conformer à des listes fermées plutôt qu'une RegEx.
- Utiliser une méthode alternative à celle de la librairie Goodtables pour contrôler le code source du schéma JSON. Celle-ci ne renvoyant qu'une seule erreur "Can/t load descriptor" sans préciser le type d'erreur et la ligne de code ayant généré cette erreur.



## Contributeurs

Ce schéma a été conçu à l'aide des travaux de [Joël Gombin](https://github.com/joelgombin) [\(Datactivist\)](https://datactivist.coop), de [Charles Népote](https://github.com/charlesnepote) [\(Fing\)](http://fing.org), et de [Colin Maudry](https://github.com/ColinMaudry) [\(Etalab\)](https://github.com/etalab/format-commande-publique).


## Voir aussi

- [Le site Web thématique de la Direction des Affaires Juridiques du Ministère des Finances](https://www.economie.gouv.fr/daj/ouverture-des-donnees-commande-publique)
- [Arrêté du 14 avril 2017 relatif aux données essentielles dans la commande publique](https://www.legifrance.gouv.fr/affichTexte.do?cidTexte=JORFTEXT000034492587&dateTexte=&categorieLien=id)
- [Arrêté du 14 avril 2017 relatif aux fonctionnalités et exigences minimales des profils d'acheteurs](https://www.legifrance.gouv.fr/affichTexte.do;jsessionid=00B73A5DA9B3A710ABD6B312CD109476.tpdila16v_3?cidTexte=JORFTEXT000034492557&dateTexte=&oldAction=rechJO&categorieLien=id&idJO=JORFCONT000034491769)


## Notes de version

**1.0** (29 mars 2018)

- Première version. Ne renvoie pas d'erreurs en utilisant la fonction Validate de la librairie [Goodtables pour Python](https://github.com/frictionlessdata/goodtables-py) lorsqu'on l'applique sur le fichier csv d'exemple.