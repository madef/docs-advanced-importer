Les tags permettent de classer les produits autrement qu'avec les catégories. L'ajout et modification de tags, s'effectuent au moyen de la balise tag :
```
<advancedimporter>
    <tag supplier-reference="test">
        <name>test</name>
        <id_lang>1</id_lang>
    </tag>
</advancedimporter>
```

L'utilisation de l'identifiant numérique de la langue n'est pas idéal, il est possible d'utiliser le code iso directement :
```
<advancedimporter>
    <tag supplier-reference="test">
        <name>test</name>
        <id_lang identifier="iso_code" type="language">en</id_lang>
    </tag>
</advancedimporter>
```

Pour associer un tag à un produit, on utilise l'imbrication :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <tag supplier-reference="test">
            <name>test</name>
            <id_lang identifier="iso_code" type="language">en</id_lang>
        </tag>
    </product>
</advancedimporter>
```

Par défaut les anciens tags du produit ne seront pas remplacés. Pour cela, il faut rajouter au produit l'attribut « remove-missing-tags » :
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-tags="yes">
        <name>test</name>
        <price>10</price>
        <tag supplier-reference="test2">
            <name>test2</name>
            <id_lang identifier="iso_code" type="language">en</id_lang>
        </tag>
    </product>
</advancedimporter>
```
