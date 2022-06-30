There are two types of stock management in PrestaShop. Classic stock management and advanced stock management. PrestaShop Advanced Importer can manage both types. 

## Classic stock 

To change product stock using its supplier reference, proceed as follows: 
```
<advancedimporter>
    <stock>
        <quantity>10</quantity>
        <product supplier-reference="product">test</product>
    </stock>
</advancedimporter>
```

To change the stock of a product using its EAN code, proceed as follows: 
```
<advancedimporter>
    <stock>
        <quantity>10</quantity>
        <product identifier="ean13">123456</product>
    </stock>
</advancedimporter>
```

This works the same way for the reference or the UPC code: 
```
<advancedimporter>
    <stock>
        <quantity>10</quantity>
        <product identifier="reference">reference</product>
    </stock>
    <stock>
        <quantity>10</quantity>
        <product identifier="upc">123456</product>
    </stock>
</advancedimporter>
```

If your feed includes a price differential and not absolute stock, this can be defined using the “mode” attribute: 
```
<advancedimporter>
    <stock mode="delta">
        <quantity>10</quantity>
        <product supplier-reference="product">test</product>
    </stock>
    <stock mode="delta">
        <quantity>-2</quantity>
        <product supplier-reference="product">test</product>
    </stock>
</advancedimporter>
```

If the stock is of a product variety (combination), you likewise need to define it in the same way as for the “combination” node. In this case, the “product” node is optional:  
```
<advancedimporter>
    <stock>
        <quantity>10</quantity>
        <combination supplier-reference="combination">test</combination>
    </stock>
</advancedimporter>
```
## Advanced stock

Warning: Advanced stock management is no longer available in PrestaShop 1.7, this part is untested and no support no guarantee will be provided in relation to stock management. 

Using advanced stock is similar to using classic stock. Three mandatory attributes need to be added: 
 - warehouse: warehouse identifier
 - usable: is the stock usable?
 - price: is the stock usable?

The following attributes are optional:
 - location: location in the warehouse
 - employee: employee identifier (default: 1)
 - currency: currency (default: base currency)
 - reason: identifies the reason for the stock movement (default: 1)

## Nesting in the product feed

If you import the product and stock, it will be faster and easier to nest the stock in the product. The “product” tag is no longer of any use in this case: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <stock>
            <quantity>10</quantity>
        </stock>
    </product>
</advancedimporter>
```
