Le prix se définit à partir de la balise « price ».
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Sans précision supplémentaire, le prix est le prix hors taxe. Si le prix est le prix ttc alors il est nécéssaire de définir le régle de taxe utilisée (via son id) et de rajouter l'attribut « tax » avec la valeur « include ».
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

De la même manière que pour le prix, ce prix est concidéré hors tax. S'il est avec taxe, il faudra rajouter l'attribut « tax » avec la valeur « include » :
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

Si le produit peut être frationné, vous pouvez définir le prix de l'unité. Le prix total correspont au prix avec toutes les unités :
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

De la même manière que pour pour le prix, le prix unitaire est concidéré hors tax. S'il est avec taxe, il faudra rajouter l'attribut « tax » avec la valeur « include » :
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
