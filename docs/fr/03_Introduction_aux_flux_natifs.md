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

## Suppression

## Suppression des manquants
