L'import de produits s'effectue au moyen de la balise « product ».

Voici un exemble de flux basique :
```
<advancedimporter">
    <product>
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Si vous souhaitez ne pas recréer un nouveau produit à chaque passage du flux, il est alors nécéssaire de rajouter la référence fournisseur :
```
<advancedimporter supplier-reference="test">
    <product>
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Voici un exemple plus complet avec les attributs les plus couramment utilisés :
```
<advancedimporter supplier-reference="test">
    <product>
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
