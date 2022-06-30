A product brand or manufacturer is imported using the “manufacturer” node: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <manufacturer>
            <name>Manufacturer</name>
            <description>Manufacturer description</description>
        </manufacturer>
    </product>
</advancedimporter>
```
Please note that the can only have a single brand. If there are several manufacturers, only the last one will be used. 


Product suppliers are imported using the “supplier” node: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <supplier>
            <name>Supplier</name>
            <description>Supplier description</description>
        </supplier>
    </product>
</advancedimporter>
```

If the product has several suppliers, add them as in the following example: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <supplier>
            <name>Supplier 1</name>
        </supplier>
        <supplier>
            <name>Supplier 2</name>
        </supplier>
    </product>
</advancedimporter>
```

The product purchase price from the supplier and its reference can also be defined: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <supplier>
            <name>Supplier</name>
            <reference>product-supplier-reference</reference>
            <price>2.45</price>
        </supplier>
    </product>
</advancedimporter>
```
