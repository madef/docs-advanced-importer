Pour traiter plusieurs langue, il faut préciser dans la balise du champs le code iso de la langue.

Voici un exemple de création de produit en anglais et français :

```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name lang="en">Name</name>
        <name lang="fr">Nom</name>
        <price>0</price>
    </product>
</advancedimporter>
```

Si plus tard, un autre flux ne contient plus l'attribut "lang" alors le champ sera le même dans toutes les langues :

```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```
