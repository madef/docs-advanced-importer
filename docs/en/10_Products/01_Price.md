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

To integrate promotion, we need to proceed like this:
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
