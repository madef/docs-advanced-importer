Les produits dématérialisés ou produits virtuels permettent de vendre des produits non physiques comme des places de concert, de la musique ou encore des bons d'achat.

Le produit se défnit comme produit virtuel à l'aide du nœud « is_virtual » :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <is_virtual>1</is_virtual>
    </product>
</advancedimporter>
```

Pour rajouter un fichier, on utilise l'entité ProductDownload :
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <is_virtual>1</is_virtual>
        <productDownload>
            <display_filename>Nom_du_fichier.pdf</display_filename>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
        </productDownload>
    </product>
</advancedimporter>
```

En plus de ces attributs, il est possible de rajouter les nœuds suivants :
 * nb_days_accessible : Nombre de jours durant lesquels le fichier peut être récupéré. 0 pour aucune limite.
 * nb_downloadable : Nombre de téléchargement possible. 0 pour aucune limite.
 * date_expiration : Date d'expiration du fichier
