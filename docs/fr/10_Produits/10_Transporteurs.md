Il est possible de déterminer des méthode de livraisons spécifiques pour un produit. Pour cela on utilise la balise « carrier » avec comme valeur l'identifiant du transporteur :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <carrier>1</carrier>
    </product>
</advancedimporter>
```

Il est possible de supprimmer les transporteurs manquants en rajoutant l'attribut « remove-missing-carriers » :
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-carriers="yes">
        <name>test</name>
        <price>10</price>
        <carrier>2</carrier>
    </product>
</advancedimporter>
```

