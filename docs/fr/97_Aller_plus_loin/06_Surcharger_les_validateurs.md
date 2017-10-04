Par défaut, les entités sont validées par les validateurs des PrestaShop. Par exemple, le nom des produits ne doit pas comporter les caractères suivants : <, >, ;, =, #, {, et }.

Il est possible de changer le validateur d'un champ d'une entité avec l'attribut « validator ». Voici un exemple où le validateur est remplacé par isString :
```
<advancedimporter>
  <product suppier-reference="demo">
    <name validator="isString">Test &gt;</name>
  </product>
</advancedimporter>
```


Il est aussi possible de supprimer complètement le validateur en ne mettant pas de valeur à l'attribut « validator » :
```
<advancedimporter>
  <product suppier-reference="demo">
    <name validator="">Test &gt;</name>
  </product>
</advancedimporter>
```

Si la validation ne passe pas à cause de la longueur de la chaîne, il est possible de la tronquer au moyen d'un modificateur. Le validateur n'est pas responsable de cette erreur :
```
<advancedimporter>
  <product suppier-reference="demo">
    <name modifier="HelperString::truncate(32)">Really long name test test test test test test test test test test test</name>
  </product>
</advancedimporter>
```

Attention, si un champ est présent plusieurs fois (comme c'est le cas pour les champs multilangues), il n'est possible que de définir un seul nouveau validatateur pour tous ces champs. Les exemples suivants ont le même résultat :
```
<advancedimporter>
  <product suppier-reference="demo">
    <name validator="isString" lang="en">Test &gt;</name>
    <name validator="isString" lang="fr">Test &gt;</name>
  </product>
</advancedimporter>
```

```
<advancedimporter>
  <product suppier-reference="demo">
    <name validator="isString" lang="en">Test &gt;</name>
    <name lang="fr">Test &gt;</name>
  </product>
</advancedimporter>
```

```
<advancedimporter>
  <product suppier-reference="demo">
    <name lang="en">Test &gt;</name>
    <name validator="isString" lang="fr">Test &gt;</name>
  </product>
</advancedimporter>
```

Enfin, définir des validateurs différents pour un même champ aura un comportement inattendu :

```
<advancedimporter>
  <product suppier-reference="demo">
    <name validator="isName" lang="en">Test &gt;</name>
    <name validator="isString" lang="fr">Test &gt;</name>
  </product>
</advancedimporter>
```

Par contre, il est possible de définir des validateurs différents pour deux entités différentes :
```
<advancedimporter>
  <product suppier-reference="demo">
    <name validator="isString">Test &gt;</name>
  </product>
  <product suppier-reference="demo-2">
    <name validator="isName">Test &gt;</name>
  </product>
</advancedimporter>
```

