La création de catégories se fait au moyen du nœud « category » ou depuis un produit avec le nœud « categorypath ».

Le categorypath permet de convertir un chemin (categorie > sous-catégorie > sous-sous-categorie). Il est plus simple d'utilisation mais moins personnalisable que category.

## Nœud « category »

Voici un exemple de catégories qui sera une fille de la catégorie « accueil » :
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>catégorie</name>
    </category>
</advancedimporter>
``` 

### Image

Pour télécharger une image depuis une URL et la rattacher à une catégorie, on utilise le nœud « image » :
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>catégorie</name>
        <image>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</image>
    </category>
</advancedimporter>
``` 

Il est aussi possible de récupérer l'image sur le disque local :
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>catégorie</name>
        <image>/modules/advancedimporter/img/media/01.jpg</image>
    </category>
</advancedimporter>
``` 



### Lien entre les catégories

Il est possible de lier des catégories entre-elles au moyen de l'imprication :
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>catégorie</name>
        <category supplier-reference="category2">
            <name>sous-catégorie</name>
        </category>
    </category>
</advancedimporter>
``` 

Il est possible de lier des catégories entre-elles sans imbrication :
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>catégorie</name>
    </category>
    <category supplier-reference="category2">
        <name>sous-catégorie</name>
        <id_parent supplier-reference="category">category1</id_parent>
    </category>
</advancedimporter>
```

### Lien entre catégories et produits

Pour lier une catégorie à un produit, on utilise l'imbrication :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category1">
            <name>catégorie</name>
        </category>
    </product>
</advancedimporter>
```

Attention, l'imbrication avec des sous-catégories est possible, mais le produit ne sera lié qu'à la première catégorie et non aux sous-catégories. Ainsi, dans cet exemple, le produit ne sera lié qu'à la catégorie :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category1">
            <name>catégorie</name>
            <category supplier-reference="category2">
                <name>sous-catégorie</name>
            </category>
        </category>
    </product>
</advancedimporter>
```

Pour lier un produit aux catégories et sous-catégories, on s'abstiendra de faire de l'imbrication de catégories :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category1">
            <name>catégorie</name>
        </category>
        <category supplier-reference="category2">
            <name>sous-catégorie</name>
            <id_parent supplier-reference="category">category1</id_parent>
        </category>
    </product>
</advancedimporter>
```

Si on souhaite lier le produit aux seules sous-catégories, alors on ne déclare par la catégorie dans le produit :
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>catégorie</name>
    </category>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category2">
            <name>sous-catégorie</name>
            <id_parent supplier-reference="category">category1</id_parent>
        </category>
    </product>
</advancedimporter>
```

Il est aussi possible de déclarer la sous-categorie à deux reprises :
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>catégorie</name>
        <category supplier-reference="category2">
            <name>sous-catégorie</name>
        </category>
    </category>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category2" />
    </product>
</advancedimporter>
```

## Nœud « categorypath »

Categorypath est plus simple d'utilisation, mais ne permet pas de nombreuse fonctionnalité. Par exemple, il ne sait pas gérer les langues ou les références fournisseurs et ne peux être utilisé que depuis un produit.

Il faut prenièrement déterminé quel est le séparateur utilisé. Ce dernier, permet des séparer les catégories des sous catégories. Par exemple dans « Femme, Robe, Été », le séparateur est « , ».

Ce dernier doit être bien choisis. En effet, si une catégorie se nomme « T-shirt, Haut », la virgule sera considérée comme un séparateur. Il n'est pas possible d'échaper les symboles identiques au séparateur.

```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <categorypath separator="&gt;"><![CDATA[ Femme > Robe > Été ]]></categorypath>
    </product>
</advancedimporter>
```

## Supprimer les liens entre produits et catégories non défini dans le flux

Le passage de ces deux flux successifs, vont faire que le produit sera rattaché à #category1 et #category2 :

```
<advancedimporter>
    <category supplier-reference="category1">
        <name>catégorie 1</name>
    </category>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category1" />
    </product>
</advancedimporter>
```

```
<advancedimporter>
    <category supplier-reference="category2">
        <name>catégorie 2</name>
    </category>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category2" />
    </product>
</advancedimporter>
```

Si vous ne souhaitez que garder les liens du dernier flux, utilisez l'attribut « remove-missing-categories » :
```
<advancedimporter>
    <category supplier-reference="category2">
        <name>catégorie 2</name>
    </category>
    <product supplier-reference="test" remove-missing-categories="yes">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category2" />
    </product>
</advancedimporter>
```
