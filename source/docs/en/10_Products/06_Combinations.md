Ranges allow you to define the possible product combinations, for example by listing different sizes and colors. These combinations have their own stock, prices, and images.

This feed creates a product with two different sizes: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <combination supplier-reference="test-size-s">
            <price>15</price>
            <attributeGroup supplier-reference="size">
                <is_color_group>0</is_color_group>
                <group_type>select</group_type>
                <position>10</position>
                <name>Size</name>
                <public_name>Size</public_name>
                <attribute supplier-reference="size-s">
                    <name>S</name>
                    <position>1</position>
                </attribute>
            </attributeGroup>
        </combination>
        <combination supplier-reference="test-size-m">
            <price>15</price>
            <attributeGroup supplier-reference="size">
                <is_color_group>0</is_color_group>
                <group_type>select</group_type>
                <position>10</position>
                <name>Size</name>
                <public_name>Size</public_name>
                <attribute supplier-reference="size-m">
                    <name>M</name>
                    <position>1</position>
                </attribute>
            </attributeGroup>
        </combination>
        <combination supplier-reference="test-size-l">
            <price>15</price>
            <attributeGroup supplier-reference="size">
                <is_color_group>0</is_color_group>
                <group_type>select</group_type>
                <position>10</position>
                <name>Size</name>
                <public_name>Size</public_name>
                <attribute supplier-reference="size-l">
                    <name>L</name>
                    <position>1</position>
                </attribute>
            </attributeGroup>
        </combination>
    </product>
</advancedimporter>
```

## Price

If the combination is created without being nested into the product, the “price” tag will indicate the impact on the product price. For example, if the product is at €10 and the combination is at €12, the then the price of the combination will be €22. If the combination is created without using nesting as in the previous example, the price will be the final price (€12).
The price attained is the price excluding tax. The price including tax can be given if nesting is used in a product:  
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price tax="include">10</price>
        <id_tax_rules_group>1</id_tax_rules_group>
        <combination supplier-reference="test-size-l">
            <price tax="include">15</price>
            <attributeGroup supplier-reference="size">
                <is_color_group>0</is_color_group>
                <group_type>select</group_type>
                <position>10</position>
                <name>Size</name>
                <public_name>Size</public_name>
                <attribute supplier-reference="size-l">
                    <name>L</name>
                    <position>1</position>
                </attribute>
            </attributeGroup>
        </combination>
    </product>
</advancedimporter>
```

## Images

To define combination images, use the same tag as for the product. The image will be added to the product and selected for the product combination: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <combination supplier-reference="test-size-l">
            <price>15</price>
            <image>
                <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
                <legend>My image</legend>
            </image>
            <attributeGroup supplier-reference="size">
                <is_color_group>0</is_color_group>
                <group_type>select</group_type>
                <position>10</position>
                <name>Size</name>
                <public_name>Size</public_name>
                <attribute supplier-reference="size-l">
                    <name>L</name>
                    <position>1</position>
                </attribute>
            </attributeGroup>
        </combination>
    </product>
</advancedimporter>
```

## Deleting missing combinations

By default, combinations missing from the feed are not deleted. To change this, you can use the delete-missing attribute, the use of which is described in the section [Introduction to native feeds](!en/Introduction_to_native_feeds). The “remove-missing-combinations” attribute can also be added in the product feed: 
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-combinations="yes">
        <name>test</name>
        <price>10</price>
        <combination supplier-reference="test-size-l">
            <price>15</price>
            <attributeGroup supplier-reference="size">
                <is_color_group>0</is_color_group>
                <group_type>select</group_type>
                <position>10</position>
                <name>Size</name>
                <public_name>Size</public_name>
                <attribute supplier-reference="size-l">
                    <name>L</name>
                    <position>1</position>
                </attribute>
            </attributeGroup>
        </combination>
    </product>
</advancedimporter>
```

## Additional information

If a combination is modified without attributes or with a missing attribute, the combination will lose all these attributes or the attribute which is missing. All the attributes for a combination therefore need to be clearly stated. 
