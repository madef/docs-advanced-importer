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
Pour intégrer un prix barré, on procédera de la manière suivante :

```
<?xml version="1.0"?>
<advancedimporter>
    <product supplier-reference="demo">
        <name>Test Specific price</name>
        <price>100</price>
        <specificPrice supplier-reference="demo-price-customer-1">
            <id_product supplier-reference="product">demo</id_product>
            <id_group>0</id_group>
            <id_customer>1</id_customer>
            <price>-1</price>
            <reduction>0.2</reduction>
            <reduction_type>percentage</reduction_type> <!-- or amount -->
            <from_quantity>1</from_quantity>
            <id_customer>0</id_customer>
            <id_shop>0</id_shop>
            <id_country>0</id_country>
            <id_currency>0</id_currency>
            <from>0000-00-00</from>
            <to>0000-00-00</to>
        </specificPrice>
    </product>
</advancedimporter>
```
