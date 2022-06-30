To add a product as an accessory for another product, use the “accessory” tag with the supplier reference for the product accessory: 
```
<advancedimporter>
    <product supplier-reference="accessory">
        <name>Mon accessory</name>
        <price>10</price>
    </product>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <accessory>accessory</accessory>
    </product>
</advancedimporter>
```

Missing accessories can be deleted by adding the “remove-missing-accessories” attribute: 
```
<advancedimporter>
    <product supplier-reference="accessoire2">
        <name>My second accessory</name>
        <price>10</price>
    </product>
    <product supplier-reference="test" remove-missing-accessories="yes">
        <name>test</name>
        <price>10</price>
        <accessory>accessory2</accessory>
    </product>
</advancedimporter>
```
