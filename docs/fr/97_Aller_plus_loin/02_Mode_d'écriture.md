Pour diverses raisons, vous pouvez souhaiter de ne pas modifier un produit s'il existe déjà. Dans ce cas il faut placer dans la balise racine de l'entité le champ « mode ». Ce dernier peut prendre les valeurs suivantes :
- create : pour la création seulement
- update : pour la mise à jour seulement
- both : pour la création et la modification

Ne pas modifier un produit existant :
```
<advancedimporter>
    <product mode="create" supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

Ne pas créer le produit s'il n'existe pas :
```
<advancedimporter>
    <product mode="update" supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

Ces deux cas créent ou modifient le produit :
```
<advancedimporter>
    <product mode="both" supplier-reference="demo-1">
        <name>Name</name>
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

Si vous souhaitez ne pas modifier un champ lors de la mise à jour du produit, alors il faut préciser le mode dans la balise du champ :
```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name mode="create">Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

L'inverse est aussi possible :
```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name mode="update">Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

