Dans PrestaShop il existe deux type de stock. Le stock classique et le stock avancé. PrestaShop Advanced Importer sait gérer les deux cas.

## Stock classique

Pour changer le stock d'un produit à partir de sa référence fournisseur on procède de la manière suivante :
```
<advancedimporter>
    <stock>
        <quantity>10</quantity>
        <product supplier-reference="product">test</product>
    </stock>
</advancedimporter>
```

Pour changer le stock d'un produit à partir de son code ean on procède de la manière suivante :
```
<advancedimporter>
    <stock>
        <quantity>10</quantity>
        <product identifier="ean13">123456</product>
    </stock>
</advancedimporter>
```

Cela fonctionne de la même manière pour la référence ou le code upc :
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

Si votre flux comporte un différentiel de prix et non un stock absolu, il est possible de le préciser avec l'attribut « mode » :
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

Si le stock est celui d'une déclinaison, alors il faut la préciser de la même manière que pour le produit avec le nœud « combination ». Dans ce cas le nœud « product » est optionnel :
```
<advancedimporter>
    <stock>
        <quantity>10</quantity>
        <combination supplier-reference="combination">test</combination>
    </stock>
</advancedimporter>
```
## Stock avancé

Attention : la gestion avancée des stocks n'existant plus sur PrestaShop 1.7, cette partie n'est pas testée et aucune aide et garantie ne sera fourni sur la gestion des stocks.

L'utilisation du stock avancé est similaire au stock classique. Deux attributs obligatoires sont à rajouter :
 - warehouse : identifiant de l'entrepot
 - usable : est-ce du stock utilisable ?
 - price : est-ce du stock utilisable ?

Les attributs suivants sont optionnels :
 - location : place dans l'entrepot
 - employee : identifiant de l'employée (defaut : 1)
 - currency : monnaie (default : monnaie de base)
 - reason : identifiant de la raison du mouvement de stock (default : 1)

## Imbrication dans le flux produit

Si vous importez le produit et les stocks, il sera plus simple est rapide d'imbriquer le stock dans le produit. Dans ce cas, la balise « product » n'est plus utile :
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
