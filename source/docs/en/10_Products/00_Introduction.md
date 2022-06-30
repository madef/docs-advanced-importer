Products are imported using the “product” tag.

Here is an example of a basic feed:
```
<advancedimporter>
    <product>
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

If you want to avoiding needing to create a new product feed every time, you will need to add the supplier reference: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

If your products already exist and you want to avoid duplicating them, you will need to use an identifier other than the supplier reference attribute. 
For example, if your feed contains the product EAN code, you can use the “identifier” attribute to specify in the feed that it needs to search for the product with this EAN code. In any case, it is highly recommended that you define the supplier reference:  
```
<advancedimporter>
    <product supplier-reference="test" identifier="ean13">
        <ean13>123456</ean13>
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

If the product exists, its supplier reference will be saved. Next time the product is modified, the EAN code will no longer be used to identify the product. If the product does not yet exist, it will be created.

Here is a more complete example with the most commonly used attributes:
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <description>test</description>
        <description_short>test</description_short>
        <reference>12345</reference>
        <ean13>12345</ean13>
        <height>34.5</height>
        <width>34.5</width>
        <depth>34.5</depth>
        <weight>4.350</weight>
        <ecotax>10</ecotax>
        <price>10</price>
        <wholesale_price>3.45</wholesale_price>
        <unity>kg</unity>
        <active>1</active>
    </product>
</advancedimporter>
```
