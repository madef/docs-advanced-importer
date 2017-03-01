The features of a product can be imported via the flow object or simply from the flow product. 

## Via the flow object

Creation of a feature and values:

```
<objects>
	<object type="feature" external-reference="feature-test">
		<name>My feature</name>
	</object>
	<object type="featureValue" external-reference="feature-value-test">
		<value>My value</value>
		<external_reference for="id_feature" type="feature">feature-test</external_reference>
	</object>
</objects>
```

## Via the flow product

There are two ways to create attributes from the flow product, either by using the tag "feature" or by using the blocks. The second method will not be detailed.

The tag "feature" can be used with values, external references or some ids. In the first case, if the features or the values don’t exist then they will be created.

Creation of features:

```
<products>
	<product external-reference="demo-1">
		<name>Name</name>
		<feature external-reference="feature-test" external-reference-value="feature-value-test" /> <!-- Add using external reference (cf "Flow object") -->
		<feature id="3" id-value="16" /> <!-- Add using ids -->
		<feature name="Prise casque" name-value="Jack stéréo"/> <!-- Add using names. If value do not exists, it will be create. -->
		<feature name="Test" name-value="Test Value" custom="1"/> <!-- Add using custom value (not recommended) -->
	</product>
</products>
```

The feature tag do not support multilanguage. To set multilangue you need to use a bloc with an objects flow :


```
<products>
	<product external-reference="demo-1">
		<name>Name</name>
        <block>
            <objects>
                <object type="feature" external-reference="feature-test">
                    <name lang="en">My feature</name>
                    <name lang="fr">Ma caractéristique</name>
                </object>
                <object type="featureValue" external-reference="feature-value-test">
                    <value lang="en">My value</value>
                    <value lang="fr">Ma valeur</value>
                    <external_reference for="id_feature" type="feature">feature-test</external_reference>
                </object>
            </objects>
            <products>
                <product external-reference="demo-1">
                    <feature external-reference="feature-test" external-reference-value="feature-value-test" />
                </product>
            </products>
        </block>
	</product>
</products>
```
