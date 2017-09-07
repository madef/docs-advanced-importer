Les caractéristiques des produits se défnisent au moyen des nœuds « feature » et « featureValue ». Il est possible de créer les caractèristiques seules :

```
<advancedimporter>
    <feature>
        <name>material</name>
    </feature>
</advancedimporter>
```

Par défaut, le nom de la caractéristique est utilisé comme référence fournisseur. Mais il est recommandé de définir la référence fournisseur sourtout si votre flux est multilangue:
```
<advancedimporter>
    <feature supplier-reference="material">
        <name>material</name>
    </feature>
</advancedimporter>
```

Ensuite il est possible d'ajouter des valeurs à cette caractéristique. Cela est possible par imbrication :
```
<advancedimporter>
    <feature>
        <name>material</name>
        <featureValue>
            <value>coton</value>
        </featureValue>
        <featureValue>
            <value>wool</value>
        </featureValue>
    </feature>
</advancedimporter>
```

Ou sans imbrication :
```
<advancedimporter>
    <feature>
        <name>material</name>
    </feature>
    <featureValue>
        <id_feature supplier-reference="feature">material</id_feature>
        <value>coton</value>
    </featureValue>
    <featureValue>
        <id_feature supplier-reference="feature">material</id_feature>
        <value>wool</value>
    </featureValue>
</advancedimporter>
```

Enfin il est possible de rattacher des valeurs de caractéristiques à un produit :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <feature>
            <name>material</name>
            <featureValue>
                <value>coton</value>
            </featureValue>
        </feature>
    </product>
</advancedimporter>
```

Ou sans imbrication :
```
<advancedimporter>
    <feature>
        <name>material</name>
    </feature>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <featureValue>
            <id_feature supplier-reference="feature">material</id_feature>
            <value>wool</value>
        </featureValue>
    </product>
</advancedimporter>
```

Si on passe le flux suivant, on remarque aue le produit garde ses caratéristiques précédement ajoutées :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <feature>
            <name>material 2</name>
            <featureValue>
                <value>coton 2</value>
            </featureValue>
        </feature>
    </product>
</advancedimporter>
```

Pour ne garder que les nouvelles caractéristique, il faut rajouter le paramettre « remove-missing-features » :

```
<advancedimporter>
    <product supplier-reference="test" remove-missing-features="yes">
        <name>test</name>
        <price>10</price>
        <feature>
            <name>material 2</name>
            <featureValue>
                <value>coton 2</value>
            </featureValue>
        </feature>
    </product>
</advancedimporter>
```
