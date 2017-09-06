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
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Si vos produit sont déjà existant et que vous ne souhaitez par le duppliquer, alors il faudra trouver un identifiant autre que l'attribut référence fournisseur.
Par exemple si votre flux contient le code ean du produit, il est possible de specifier dans le flux qu'il faut rechercher le produit ayant cette ean particulier grâce à l'attribut « identifier ». Dans tout les cas, il est recommandé de définir la référence fournisseur :
```
<advancedimporter>
    <product supplier-reference="test" identifier="ean13">
        <ean13>123456</ean13>
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Si le produit existe, sa référence fournisseur sera enregistrée. À la prochaine modification, cela le code ean ne sera plus utilisé pour identifié le produit. Si le produit n'éxiste pas, il sera créé.

Voici un exemple plus complet avec les attributs les plus couramment utilisés :
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
