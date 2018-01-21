La création de clients s'effectue au moyen de la balise customer. Voici un exemple de création d'un compte client :

```
<?xml version="1.0" encoding="utf-8"?>
<advancedimporter>
  <customer supplier-reference="john@doe.com">
  <firstname>John</firstname>
  <lastname>Doe</lastname>
  <email>John@doe.com</email>
  <passwd>a625a8bccc7af3f39132f7567037d966</passwd>
  <id_default_group>1</id_default_group>
</customer>
</advancedimporter>
```

Le mot de passe doit être encodé selon la méthode de PrestaShop (Tools::encrypt).

Il est possible de soumettre le mot de passe en clair à l'aide d'un modifieur :
```
<?xml version="1.0" encoding="utf-8"?>
<advancedimporter>
  <customer supplier-reference="john@doe.com">
  <firstname>John</firstname>
  <lastname>Doe</lastname>
  <email>John@doe.com</email>
  <passwd modifier="Tools::encrypt">P@ssw0rd!</passwd>
  <id_default_group>1</id_default_group>
</customer>
</advancedimporter>
```
