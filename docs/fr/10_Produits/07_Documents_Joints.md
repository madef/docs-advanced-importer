La création de documents joints s'effectue à l'aide de la balise « attachment » :
```
<advancedimporter>
    <attachment supplier-reference="test">
        <name>Name of the document</name>
        <description>Description of the document</description>
        <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
    </attachment>
</advancedimporter>
```

Il est possible rattacher le document à un produit en l'imbricant dans la balise produit :
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
