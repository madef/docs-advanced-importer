Dans ce chapitre nous allons nous intéresser au format spécifique du module. Pour intégrer un flux fournisseur dans un autre format, référez-vous au chapitre [Importer un flux](!fr/Importer_un_flux).

## Structure

La balise racine est toujours **advancedimporter**

La balise de second niveau est le nom de la classe PHP de l'entité : product, category, order, customer, …

Enfin les balises de troisième niveau sont les attributs. Par exemple nous créons un produit nommé **test** avec ce flux :
```
<advancedimporter>
    <product>
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Et de même pour une catégorie nommée **test** :
```
<advancedimporter>
    <category>
        <name>test</name>
    </category>
</advancedimporter>
```

Il est possible de créer les deux dans le même flux :
```
<advancedimporter>
    <product>
        <name>test</name>
        <price>10</price>
    </product>
    <category>
        <name>test</name>
    </category>
</advancedimporter>
```

## Imbrications
Les entités sont parfois liées entre elles. Par exemple pour intégrer une catégorie et sa sous-catégorie :

```
<advancedimporter>
    <category>
        <name>catégorie</name>
        <category>
            <name>sous-catégorie</name>
        </category>
    </category>
</advancedimporter>
```

Ou encore pour lier le produit à la sous-catégorie :
```
<advancedimporter>
    <product>
        <name>test</name>
        <price>10</price>
        <category>
            <name>catégorie</name>
            <category>
                <name>sous-catégorie</name>
            </category>
        </category>
    </product>
</advancedimporter>
```

## Références fournisseurs

Si vous avez exécuté les flux plusieurs fois alors vous avez dû remarquer que les entités ont été dupliquées.

Pour éviter cela, il faut identifier les entités au moyen de la référence fournisseur :

### Déclaration

Voici un exemple de déclaration d'un produit avec un référence fournisseur :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Notez que la référence fournisseur est spécifique au type de l'entité. Vous pouvez donc utiliser la référence fournisseur « test » pour un produit et une catégorie :
```
<advancedimporter>
    <category supplier-reference="test">
        <name>test</name>
    </category>
</advancedimporter>
```

### Réutilisation

Il est parfois utile pour pouvoir lier des produits entre-eux d'utiliser la référence fournisseur.
Pour cela, on rajoute l'attribut  « supplier-reference » avec comme valeur le type de l'entité :
```
<advancedimporter>
    <category supplier-reference="category2">
        <name>test</name>
        <id_parent supplier-reference="category">category1</id_parent>
    </category>
</advancedimporter>
```

## Identifieur

Si vous souhaitez modifier des entités déjà existantes, alors il est possible de définir un identifiant différent de la référence fournisseur (ex : reference, code ean, ...).
Voici un exemple de modification de produit à partir de sa référence :
```
<advancedimporter>
    <product supplier-reference="reference-value" identifier="reference">
        <reference>reference-value</reference>
        <name>test</name>
    </product>
</advancedimporter>
```

Si la référence fournisseur est optionnelle, il est quand même recommandé de la définir afin que le module l'enrenregistre. Cela permet ainsi d'améliorer la rapidité des futures modifications.

Si c'est une balise à l'intérieur d'une entité, elle s'utilisera en précisant le type de l'entité cible de la manière suivante :
```
<advancedimporter>
    <tag supplier-reference="test">
        <name>test</name>
        <id_lang identifier="iso_code" type="language">en</id_lang>
    </tag>
</advancedimporter>
```

## Suppression

La supressions des éléments se fait en ajoutant l'attribut « delete="1" » :

```
<advancedimporter>
    <product supplier-reference="test" delete="1">
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Les attributs sont alors optionels :

```
<advancedimporter>
    <product supplier-reference="test" delete="1" />
</advancedimporter>
```

## Suppression des manquants

Par defaut, l'absence d'une entité du flux ne fera pas qu'il sera supprimé. Pour ce faire, il faut rajouter l'attribut « auto-delete » dans la balise racine. Cet attribut doit avoir comme paramètre le nom du fournisseur. Seules les entités importées avec le module et ayant une reférence fournisseur peuvent être supprimées automatiquement.

Premier flux, création de « test 1 » et  « test 2 » :
```
<advancedimporter auto-delete="supplier">
    <product supplier-reference="test1">
        <name>test 1</name>
        <price>10</price>
    </product>
    <product supplier-reference="test2">
        <name>test 2</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Second flux, suppression de « test 2 » :
```
<advancedimporter auto-delete="supplier">
    <product supplier-reference="test1">
        <name>test 1</name>
        <price>10</price>
    </product>
</advancedimporter>
```
ttention, avec l'auto-delete le flux intégré doit être complet sans quoi des produits seront effacés de façon définitive.
