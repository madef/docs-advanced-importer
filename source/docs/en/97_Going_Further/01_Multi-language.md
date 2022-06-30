To manage multiple languages, you need to define the ISO code for the language in the tag field.

Here is an example where the product is created in English and French:
```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name lang="en">Name</name>
        <name lang="fr">Nom</name>
        <price>0</price>
    </product>
</advancedimporter>
```

If later another feed no longer contains the “lang” tag, the field will be the same in all languages: 
```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```
