Les déclinaisons permettent de définir les variations possibles d'un produit. Par exemple en listant des références de tailles et couleurs différentes. Ces déclinaisons ont leur propre stock et leur propre prix et propres images.

Ce flux permet de créer un produit avec deux tailles différentes.
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
                <attribute supplier-reference="size-l">
                    <name>L</name>
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
