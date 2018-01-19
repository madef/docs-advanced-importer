La création de client s'effectue au moyen de la balise customer. Voici un exemple de création de client :

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

Comme vous pouvez le voir le mot de passe doit être encodé selon la méthode de PrestaShop (Tools::encrypt).

Il est possible de donner les mot de passe en clair :
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
