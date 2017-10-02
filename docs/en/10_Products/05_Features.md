Product features are defined using the “feature” and “featureValue” nodes. Standalone features can be created:

```
<advancedimporter>
    <feature>
        <name>material</name>
    </feature>
</advancedimporter>
```

By default, the name of the feature is used as the supplier reference. But it is particularly recommended that you define the supplier reference if your feed is multilingual: 
```
<advancedimporter>
    <feature supplier-reference="material">
        <name>material</name>
    </feature>
</advancedimporter>
```

It is then possible to add values to this feature. This is done by nesting: 
```
<advancedimporter>
    <feature>
        <name>material</name>
        <featureValue>
            <value>cotton</value>
        </featureValue>
        <featureValue>
            <value>wool</value>
        </featureValue>
    </feature>
</advancedimporter>
```

Or without nesting:
```
<advancedimporter>
    <feature>
        <name>material</name>
    </feature>
    <featureValue>
        <id_feature supplier-reference="feature">material</id_feature>
        <value>cotton</value>
    </featureValue>
    <featureValue>
        <id_feature supplier-reference="feature">material</id_feature>
        <value>wool</value>
    </featureValue>
</advancedimporter>
```

It is also possible to attach feature values to a product:
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <feature>
            <name>material</name>
            <featureValue>
                <value>cotton</value>
            </featureValue>
        </feature>
    </product>
</advancedimporter>
```

Or without nesting:
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

If you run the following feed, you will notice that the product keeps the previously-added features:
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <feature>
            <name>material 2</name>
            <featureValue>
                <value>cotton 2</value>
            </featureValue>
        </feature>
    </product>
</advancedimporter>
```

To keep only the newly-added features, add the parameter “remove-missing-features”:

```
<advancedimporter>
    <product supplier-reference="test" remove-missing-features="yes">
        <name>test</name>
        <price>10</price>
        <feature>
            <name>material 2</name>
            <featureValue>
                <value>cotton 2</value>
            </featureValue>
        </feature>
    </product>
</advancedimporter>
```
