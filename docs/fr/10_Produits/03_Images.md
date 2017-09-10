Pour ajouter une image à un produit, on utilise le nœud « image » :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image</legend>
        </image>
    </product>
</advancedimporter>
```

L'image peut provenir d'une URL comme dans le précédent exemple, ou du serveur lui-même :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <image>
            <url>/modules/advancedimporter/views/img/media/01.jpg</url>
            <legend>My image</legend>
        </image>
    </product>
</advancedimporter>
```

Si vous avez essayé les deux exemples précédents, vous remarquerez que le produit a maintenant deux images. Si votre flux liste l'intégralité des images du produit, il est possible de supprimer les images manquantes avec l'attribut « remove-missing-images » :
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-images="yes">
        <name>test</name>
        <price>10</price>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image</legend>
        </image>
    </product>
</advancedimporter>
```

Si vous souhaitez ajouter plusieurs images il faut répéter la balise image et non la balise url :
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-images="yes">
        <name>test</name>
        <price>10</price>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image 1</legend>
        </image>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-2.jpg</url>
            <legend>My image 2</legend>
        </image>
    </product>
</advancedimporter>
```

Il est aussi possible de définir l'ordre des images avec la nœud « position » :
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-images="yes">
        <name>test</name>
        <price>10</price>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image 1</legend>
            <position>2</position>
        </image>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-2.jpg</url>
            <legend>My image 2</legend>
            <position>1</position>
        </image>
    </product>
</advancedimporter>
```

Enfin il est possible de définir quelle image utiliser comme couverture :
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-images="yes">
        <name>test</name>
        <price>10</price>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image 1</legend>
            <cover>0</cover>
        </image>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-2.jpg</url>
            <legend>My image 2</legend>
            <cover>1</cover>
        </image>
    </product>
</advancedimporter>
```

## Optimisation

Le téléchargement des images peut être long et est souvent la cause de lenteur d'importation. Afin d'éviter de télécharger des images déjà présentes, il est recommandé d'utiliser l'attribut « mode » avec pour valeur « create ». Ainsi, seules les images déjà non existantes (url inconnnue) seront téléchargées.

```
<advancedimporter>
    <product supplier-reference="test" remove-missing-images="yes">
        <name>test</name>
        <price>10</price>
        <image mode="create">
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image 1</legend>
        </image>
        <image mode="create">
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-2.jpg</url>
            <legend>My image 2</legend>
        </image>
    </product>
</advancedimporter>
```
