Les caractéristiques des produits se défnisent au moyen des nœuds « feature » et « featureValue ». Il est possible de créer les caractèristiques seules :

```
<advancedimporter">
    <feature>
        <name>material</name>
    </feaure>
</advancedimporter>
```

Par défaut, le nom de la caractéristique est utilisé comme référence fournisseur. Mais il est recommandé de définir la référence fournisseur sourtout si votre flux est multilangue:
```
<advancedimporter">
    <feature supplier-reference="material">
        <name>material</name>
    </feaure>
</advancedimporter>
```

Ensuite il est possible d'ajouter des valeurs à cette caractéristique. Cela est possible par imbrication :
```
<advancedimporter">
    <feature>
        <name>material</name>
        <featureValue>
            <value>coton</value>
        </featureValue>
        <featureValue>
            <value>wool</value>
        </featureValue>
    </feaure>
</advancedimporter>
```

Ou sans imbrication :
```
<advancedimporter">
    <feature>
        <name>material</name>
    </feaure>
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
