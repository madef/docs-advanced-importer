Pour plusieurs raison vous pouvez souhaiter ne pas modifier un produit si il existe déjà. Dans ce cas il faut place dans la balise racine de l'entité le champ mode. Ce dernier prend plus valeur :
- create : pour le création seulement
- update : pour la mise à jour seulement
- both : pour les création et modification

Ne pas modifier un produit existant :

```
<advancedimporter>
    <product mode="create" supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

Ne pas créer le produit si il n'existe pas :

```
<advancedimporter>
    <product mode="update" supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

Ces deux cas crée ou modifie le produit :

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

Si vous souhaitez ne pas modifier un champ lors de la mise à jour du produit, alors faut préciser le mode dans la balise du champ :

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

