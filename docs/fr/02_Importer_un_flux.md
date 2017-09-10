Avant d'importer un flux pensez à correctement [configurer le module](!fr/Installation).

Selon le format du flux à importer il peut y avoir des étapes supplémentaires. Par exemple si le flux est un document Excel, il faudra d'abord le convertir en CSV.

| Format du flux   | XML natif | XML | CSV | Excel |
|------------------|-----------|-----|-----|-------|
| Convertir en CSV | Non       | Non | Non | Oui   |
| Créer un modèle  | Non       | Oui | Oui | Oui   |


La première étape est donc généralement de créer un modèle. Si votre flux est un CSV, ou un XML venant d'un prestataire alors la création d'un modèle est nécéssaire.

Le modèle permet de convertir XML ou CSV en XML compréhensible par le module (appelé format natif).

S'il s'agit d'un flux produit alors il est possible d'utiliser l'assistant de création de modèle. Ce dernier permet de réaliser des modèles sans connaissance en XML et XSLT au moyen d'une interface graphique.

## Créer un modèle avec l'assistant

Commencez par importer votre flux en cliquant sur le bouton « Ajouter » depuis la section « Flux » du sous menu « PrestaShop XML Importer ». De préférence, choisissez un flux plus petit ne contenant que peu de données. Plus le fichier sera petit, plus l'assistant sera rapide.

Ensuite, il vous sera demandé de nommer le modèle. Si votre fichier est un XML, alors il vous sera demandé d'identifier la racine de chaque produit.

Plusieurs étapes se succèdent. Dans chacune, il vous sera demandé de définir quel nœud (pour un XML) ou quelle colonne (pour un CSV) correspond à l'infomation demandée :
- Identifiant du produit
- Nom et description du produit
- Prix et taxe
- Catégories
- Images
- Stock et statut
- Caractéristiques
- Fournisseur et fabriquant

## Créer un modèle

Pour créer un modèle sans assistant, il faut se rendre dans l'onglet « modèle » et cliquer sur le bouton ajouter.

## Créer une classe PHP de modèle

Si votre flux doit faire appel à une API externe, si le format du flux est dans un format propriétaire ou plat, ou encore si votre flux fait référence à d'autres entitées PrestaShop sans utiliser un identifiant utilisable par le module, alors l'écriture d'une classe PHP sera nécessaire. Vous trouverez plus d'informations dans [la page dédiée aux extracteurs](!fr/Aller_plus_loin/Extracteurs).

## Importer un flux manuellement

Commencez par cliquer sur le bouton « Ajouter » depuis la section « Flux » du sous menu « PrestaShop XML Importer ». Premièrement, choississez le flux à importer. Ensuite, choississez le modèle à appliquer. Si le flux est au format natif, choisissez l'option « aucun ». Après cela, rendez-vous dans la section « Flux » du sous menu « Advanced Importer » pour suivre l'avancement de l'intégration du flux.

## Importer un flux automatiquement

### Via FTP

Pour télécharger de manière récurrente un flux depuis un FTP, rendez-vous dans la section « Tâche récurrente » du sous menu « Advanced Importer ».
Cliquez sur le bouton « Ajouter un téléchargeur FTP ».
Dans le fornulaire qui apparait, commencez par choisir la récurrence (cron time). Ensuite, remplissez les informations nécéssaires à la connexion FTP (utilisateur, mot de passe, host, port) ainsi que le chemin vers le dossier ou fichier. Si le chemin est un dossier, tous les fichiers du dossier seront téléchargés.

### Via HTTP


Pour télécharger de manière récurrente un flux depuis une URL, rendez-vous dans la section « Tâche récurante » du sous menu « Advanced Importer ».
Cliquez sur le bouton « Ajouter un téléchargeur HTTP ».
Dans le fornulaire qui apparait, commencez par choisir la récurrence (cron time). Ensuite, remplissez l'url du fichier ainsi que le nom souhaité pour le fichier téléchargé. Si vous ne mettez rien, il ne sera pas renommé.
