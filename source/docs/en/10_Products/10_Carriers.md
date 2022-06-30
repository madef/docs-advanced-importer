Specific delivery methods can be defined for a product. To do this, use the “carrier” tag using the carrier identifier as the value:
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <carrier>1</carrier>
    </product>
</advancedimporter>
```

Missing carriers can be deleted using the “remove-missing-carriers” attribute:
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-carriers="yes">
        <name>test</name>
        <price>10</price>
        <carrier>2</carrier>
    </product>
</advancedimporter>
```

