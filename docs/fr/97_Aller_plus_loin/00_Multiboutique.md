Pour gérer l'enregistrement en multiboutique, il faut préciser dans le tag racine de l'entité l'id de la boutique.

Par exemple si vous souhaitez importer un produit dans le store 2 et 3 seulement, vous procéderez de la manière suivante :
```
<advancedimporter>
    <product shop="2" supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
    <product shop="3" supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

Si vous souhaitez avoir un nom de produit différent pour chacune des boutiques, vous procéderez de la manière suivante :
```
<advancedimporter>
    <product shop="2" supplier-reference="demo-1">
        <name>Name 1</name>
        <price>0</price>
    </product>
    <product shop="3" supplier-reference="demo-1">
        <name>Name 2</name>
        <price>0</price>
    </product>
</advancedimporter>
```

Attention, la boutique par défaut du produit sera toujours celle de la première boutique définie dans le flux. Dans notre cas c'est la boutique 2. Si on souhaite l'inverse, il faut que le flux ressemble à :
```
<advancedimporter>
    <product shop="3" supplier-reference="demo-1">
        <name>Name 2</name>
        <price>0</price>
    </product>
    <product shop="2" supplier-reference="demo-1">
        <name>Name 1</name>
        <price>0</price>
    </product>
</advancedimporter>
```

Dans tous les exemples précédents, le produit n'est pas importé dans la boutique 1.

Si vous souhaitez importer un produit dans toutes les boutiques alors il suffit de ne pas préciser la boutique :
```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

Si vous souhaitez importer un produit dans toutes les boutiques et le personnaliser pour une seule alors il faut créer d'abord le produit sur toutes les boutiques puis le modifier sur la boutique souhaitée :
```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
    <product shop="2" supplier-reference="demo-1">
        <name>Name 2</name>
        <price>0</price>
    </product>
</advancedimporter>
```

Ceci ne marchera pas :
```
<advancedimporter>
    <product shop="2" supplier-reference="demo-1">
        <name>Name 2</name>
        <price>0</price>
    </product>
    <product supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

Enfin passer un flux sans préciser les boutiques après avoir enregistré les produits dans des boutiques spécifiques aura un effet inattendu. Il n'est donc pas recomandé de passer les deux flux suivants dans cet ordre :
```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
    <product shop="2" supplier-reference="demo-1">
        <name>Name 2</name>
        <price>0</price>
    </product>
</advancedimporter>
```

```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```
