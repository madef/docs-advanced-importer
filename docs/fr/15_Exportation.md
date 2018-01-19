Le module permet l'export de toutes entités. Par exemple, il est possible d'exporter l'ensemble des produits du catalogue. En plus de cela, il permet d'exporter toutes entités liées aux produits (ex : categories, tags, déclinaisons, prix specifiques, ...).

Grâce à l'export de données, vous pouvez par exemple synchroniser le stock entre deux PrestaShop. Vous pouvez aussi envoyer vos commandes à une autre application.

## Stratégies d'export
Plusieurs stratégies d'exportation existent :
- complète : l'intégralité du catalogue ou des commandes
- partielle : l'ensemble des entités modifiées ou créées depuis le dernier export (cette option n'est pas encore possible)

Ces stratégies permettent d'exporter soit le catelogue complet, soit les différences de stocks, soit les nouvelles commandes ou encore les changement des statuts de commandes.

## Format des flux exportés

Les flux d'export sont au format XML comme décrit dans la docummentation (certaines spécifités existent mais le flux exporté peuvent être importé par le module).
Il est possible de personnaliser les flux grâce à des XSLT. Vous pouvez donc transformer les flux d'export XML en CSV ou en fichiers plat selon votre besoin.

## Référence fournisseur

Lorsque les entités ont une référence fournisseur, le module utilise ces dernières à la place des ids. Cela ne peut être fait que si les entités ont été importées par le module.

## Token

Les exports sont protégé par un token unique par fichier.


## Premier export

Pour créér un nouvel export rendez-vous dans le backoffice > Advanced Importer > Tâche récurrente.
Ici dans les option possible (en haut à droite) choisissez « Ajouter une exporteur ».
Remplissez les différentes options.

Une fois la tâche exécutée, rendez-vous dans les logs. Une message ressemblant à cela devrait être affiché :
  « Vous pouvez télécharger le flux à cette URL : http://myshop.com/advancedimporter/export/092ad23b72a1777f8b01/product.xml »


