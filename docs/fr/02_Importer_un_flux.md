Avant d'importer une flux pensez à correctement [configurer le module](!fr/Installation).

Selon le format du flux à importer il peut y avoir des étapes supplémentaires. Par exemple si le flux est doccument Excel, il faudra d'abord le convertir en CSV.

| Format du flux   | XML natif | XML | CSV | Excel |
|------------------|-----------|-----|-----|-------|
| Convertir en CSV | Non       | Non | Non | Oui   |
| Créer un modèle  | Non       | Oui | Oui | Oui   |


La première étape est donc généralement de créer un modèle. Si votre flux est un CSV, ou un XML venant d'un prestataire alors la création d'un modèle est nécéssaire.

Le modèle permet de convertir XML ou CSV en XML compréhensible par le module.

S'il s'agit d'un flux produit alors il est possible d'utiliser l'assistant de création de modèle. Ce dernier permet de réaliser sans connaissance en XML et XSLT au moyen d'une interface des modèles.

### Créer un modèle avec l'assistant

Commencez par importer votre flux en choisissant «Téléchargement » du sous menu « PrestaShop XML Importer ». De préférence, choisissez un flux plus petit ne contenant que peu de données. Plus le fichier sera petit, plus l'assistant sera rapide.

Ensuite, il vous sera demandé de nommer le modèle. Si votre fichier est un XML, alors il vous sera demandé d'identifier la racine de chaque produit.

If you try to create a template for an XML, the assistant will ask you to define the xpath of the items. In other words, the path to the node of the products:

### Créer un modèle

### Créer une classe PHP de modèle

Si votre flux doit faire appel à une API externe, si le format du flux est une format propriétaire ou plat, ou encore si votre flux fait référence à d'autres entitées PrestaShop sans utiliser un identifiant utilisable par le module, alors l'écriture du d'une classe PHP sera nécessaire. Vous trouverez plus d'information dans [la page dédiée aux extracteurs](!fr/Avancé/Extracteurs).




The importation of flows can be done three different ways:

* Via the administration panel 
* Via FTP or SSH
* Via a planned task

In the different examples whatever the chosen method, we will use the following flow:

```
<products>
	<product external-reference="demo-1">
		<name>Name</name>
		<description >Product description</description>
		<price>20</price>
	</product>
</products>
```
