L'importation de la marque ou du fabriquant d'un produit se fait au moyen du nœud manufacturer :
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
Veuillez noter que le produit ne peut avoir qu'une seule marque. S'il y a plusieurs fabriquants, seul le dernier sera pris en compte.


L'importation des fournisseurs d'un produit se fait au moyen du nœud supplier :
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

Si le produit possède plusieurs fournisseurs, il faut les ajouter comme dans cet exemple :
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

Enfin, il est possible de définir le prix d'achat du produit chez le fournisseur ainsi que sa référence :
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
