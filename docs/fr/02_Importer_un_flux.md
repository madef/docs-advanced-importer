Avant d'importer une flux pensez à correctement [configurer le module](!fr/installation).

Selon le format du flux à importer il peut y avoir des étapes supplémentaires. Par exemple si le flux est doccument Excel, il faudra d'abord le convertir en CSV.

| Format du flux   | XML natif | XML | CSV | Excel |
|------------------|-----------|-----|-----|-------|
| Convertir en CSV | Non       | Non | Non | Oui   |
| Créer un modèle  | Non       | Oui | Oui | Oui   |


La première étape est donc généralement de créer un modèle. Si votre flux est un CSV, ou un XML venant d'un prestataire alors la création d'un modèle est nécéssaire.

Le modèle permet de convertir XML ou CSV en XML comprehenttible par le module.





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
