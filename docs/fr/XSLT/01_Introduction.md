Selon wikipédia, XSLT (eXtensible Stylesheet Language Transformations), défini au sein de la recommandation XSL du W3C, est un langage de transformation XML de type fonctionnel. Il permet notamment de transformer un document XML dans un autre format, tel PDF ou encore HTML pour être affiché comme une page web.

PrestaShop Advanced Importer, utilise les XSLT pour convertir les XMLs dans le format natif du module. Que vous choisissiez de passer ou non par l'assistant de modèle, le modèle créé sera une XSLT.

Pour les CSVs, le module procède premièrement à un traformation du CSV en XML basique afin de pouvoir appliquer une XSLT par la suite. Ainsi que cela soit un XML ou non, il est possible de profiter de la puissance offerte par le moteur de transformation XSLT.

L'XML basique produit par la transformation des CSVs ressemble à cela :

```
<csv>
    <line>
        <A>contenu de la colonne A ligne A</A>
        <B>contenu de la colonne B ligne B</B>
        <C>contenu de la colonne C ligne C</C>
    </line>
    <line>
        <A>contenu de la colonne A ligne A</A>
        <B>contenu de la colonne B ligne B</B>
        <C>contenu de la colonne C ligne C</C>
    </line>
</csv>
```
