Tags allow products to be classified in ways other than by using categories. Tags are added and modified using the “tag” tag: 
```
<advancedimporter>
    <tag supplier-reference="test">
        <name>test</name>
        <id_lang>1</id_lang>
    </tag>
</advancedimporter>
```

Using a numerical identifier for a language is not ideal, the language’s ISO code can be used directly:
```
<advancedimporter>
    <tag supplier-reference="test">
        <name>test</name>
        <id_lang identifier="iso_code" type="language">en</id_lang>
    </tag>
</advancedimporter>
```

Use nesting to attach a tag to a product: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <tag supplier-reference="test">
            <name>test</name>
            <id_lang identifier="iso_code" type="language">en</id_lang>
        </tag>
    </product>
</advancedimporter>
```

By default, old product tags will not be replaced. To do this, add the “remove-missing-tags” attribute:
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-tags="yes">
        <name>test</name>
        <price>10</price>
        <tag supplier-reference="test2">
            <name>test2</name>
            <id_lang identifier="iso_code" type="language">en</id_lang>
        </tag>
    </product>
</advancedimporter>
```
