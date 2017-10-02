Attached documents can be created using the “attachment” tag:
```
<advancedimporter>
    <attachment supplier-reference="test">
        <name>Name of the document</name>
        <description>Description of the document</description>
        <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
    </attachment>
</advancedimporter>
```

The document can be attached to a product by nesting it in the product tag: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <attachment supplier-reference="test">
            <name>Name of the document</name>
            <description>Description of the document</description>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
        </attachment>
    </product>
</advancedimporter>
``` 
