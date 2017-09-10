Le prix se définit à l'aide de la balise « price ».
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Sans précision supplémentaire, le prix est hors taxe. Si le prix est ttc alors il est nécéssaire de définir la régle de taxe utilisée (via son id) et de rajouter l'attribut « tax » avec la valeur « include ».
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price tax="include">10</price>
        <id_tax_rules_group>1</id_tax_rules_group>
    </product>
</advancedimporter>
```

Il est possible de définir le prix d'achat :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <wholesale_price>3.45</wholesale_price>
    </product>
</advancedimporter>
```

De la même manière que pour le prix, ce prix est considéré hors taxe. S'il est avec taxe, il faudra rajouter l'attribut « tax » avec la valeur « include » :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price tax="include">10</price>
        <wholesale_price tax="include" >3.45</wholesale_price>
        <id_tax_rules_group>1</id_tax_rules_group>
    </product>
</advancedimporter>
```

Si vous souhaitez afficher le prix unitaire du produit (ex prix au kg), il est possible de définir le prix de l'unité. Voici un exemple avec un produit de 10kg dont le kg est vendu 1 euro :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <unitprice>1</unitprice>
        <unity>kg</unity>
    </product>
</advancedimporter>
```

De la même manière que pour le prix, le prix unitaire est considéré hors taxe. S'il est avec taxe, il faudra rajouter l'attribut « tax » avec la valeur « include » :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price tax="include">10</price>
        <unitprice tax="include">1</unitprice>
        <unity>kg</unity>
        <id_tax_rules_group>1</id_tax_rules_group>
    </product>
</advancedimporter>
```
