Dans ce chapitre nous allons nous intéresser au format spécifique du module. Pour intégrer un flux fournisseur dans un autre format, référez-vous au chapitre [Importer un flux](!fr/Importer_un_flux).

## Structure

La balise racine est toujours **advancedimporter**

La balise de second niveau est le nom de la classe PHP de l'entité : product, category, order, customer, …

Enfin les balises de troisième niveau sont les attributs. Par exemple on créra un produit nommé **test** avec ce flux :

```
<advancedimporter>
    <product>
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Et de même pour une catégorie nommé **test** :

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

Les entités sont parfois liée entre elles. Par exemple pour intégrer une catégorie et sa sous-catégorie :

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

Si vous aviez exécuté les flux plusieurs fois alors vous avez remarqué que les entités ont été dupliquées.

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

Par defaut, l'absence d'une entité du flux ne fera pas qu'il sera supprimé. Pour ce faire, il faut rajouter l'attribut « autodelete » dans la balise racine. Cette attribut doit avoir comme paramettre le nom du fournisseur. Seul les entités importées avec le module et une reférence externe pour être nettoyées automatiquement.

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

```
<advancedimporter auto-delete="supplier">
    <product supplier-reference="test1">
        <name>test 1</name>
        <price>10</price>
    </product>
</advancedimporter>
```
