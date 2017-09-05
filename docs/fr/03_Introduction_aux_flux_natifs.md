Dans ce chapitre nous allons nous intéresser au format spécifique du module. Pour intégrer un flux fournisseur dans un autre format, référez-vous au chapitre [Importer un flux](!fr/Importer_un_flux).

## Structure

La balise racine est toujours **advancedimporter**

La balise de second niveau est le nom de la classe PHP de l'entité : product, category, order, customer, …

Enfin les balises de troisième niveau sont les attributs. Par exemple on créera un produit nommé **test** avec ce flux :

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

## Références fourniseurs

Si vous aviez exécuté les flux plusieurs fois alors vous avez dû remarquer que les entités ont été dupliquées.

Pour éviter cela, il faut identifier les entités au moyen de la référence fournisseur :

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

Par defaut, l'absence d'une entité du flux ne fera pas qu'il sera supprimé. Pour ce faire, il faut rajouter l'attribut « auto-delete » dans la balise racine. Cet attribut doit avoir comme paramettre le nom du fournisseur. Seules les entités importées avec le module et ayant une reférence fournisseur peuvent être supprimés automatiquement.

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
Attention, avec l'auto-delete le flux intégré doivent être complet sans quoi des produits seront effacés de façon définitive.
