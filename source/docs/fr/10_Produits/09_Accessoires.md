Pour ajouter un produit comme un accessoire d'un autre produit, on utilise la balise « accessory » avec la référence fournisseur du produit accessoire :
```
<advancedimporter>
    <product supplier-reference="accessoire">
        <name>Mon accessoire</name>
        <price>10</price>
    </product>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <accessory>accessoire</accessory>
    </product>
</advancedimporter>
```

Il est possible de supprimmer les accessoires manquants en rajoutant l'attribut « remove-missing-accessories » :
```
<advancedimporter>
    <product supplier-reference="accessoire2">
        <name>Mon second accessoire</name>
        <price>10</price>
    </product>
    <product supplier-reference="test" remove-missing-accessories="yes">
        <name>test</name>
        <price>10</price>
        <accessory>accessoire2</accessory>
    </product>
</advancedimporter>
```
