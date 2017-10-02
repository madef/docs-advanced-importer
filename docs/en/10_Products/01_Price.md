 The price is defined using the “price” tag.
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

If no further detail is provided, the price will exclude tax. If the price includes taxes, you will need to define the tax regulation used (using its ID) and add the “tax” attribute with the “include” value. 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price tax="include">10</price>
        <id_tax_rules_group>1</id_tax_rules_group>
    </product>
</advancedimporter>
```

The purchase price can be defined:
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <wholesale_price>3.45</wholesale_price>
    </product>
</advancedimporter>
```

Like the price, the purchase price is considered to exclude tax. If it includes tax, you will need to add the “tax” attribute with the “include” value:
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

If you wish to display the product unit price (e.g. price per kg), you can define the unit price. Here is an example where a 10kg product is sold at 1 euro per kilogram:
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

Like the price, the unit price is considered to exclude tax. If it includes tax, you will need to add the “tax” attribute with the “include” value:
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
