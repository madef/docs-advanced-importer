Les déclinaisons permettent de définir les variations possibles d'un produit, par exemple en listant des références de tailles et couleurs différentes. Ces déclinaisons ont leur propre stock et leur propre prix et leurs propres images.

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

## Prix

Si la déclinaison est créée sans être imbriquée dans le produit, alors la balise « price » indique l'impact sur le prix du produit. Par exemple si le produit est à 10€ et la déclinaison à 12€ alors le prix de la déclinaison sera de 22€. Si la déclinaison est créée avec une imbrication comme dans l'exemple précédent, alors le prix sera le prix final (donc 12).
Le prix attendu est hors taxe. Avec l'imbriquation dans un produit, il est possible de donner le prix taxé :
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

Pour définir les images des déclinaisons, on utilise la même balise que pour le produit. L'image sera ajoutée au produit et sélectionnée pour la déclinaison :
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

## Suppression des déclinaisons manquantes

Par défaut, les déclinaisons manquantes du flux ne seront pas supprimées. Pour changer cela, il est possible d'utiliser le delete-missing dont vous retrouverez le fonctionnement dans le chapitre [Introduction aux flux natifs](!fr/Introduction_aux_flux_natifs). Aussi il est possible dans le flux produit de rajouter l'attribut « remove-missing-combinations » :
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

## Informations diverses

Si une déclinaison (combination) est modifiée sans attribut ou avec un attribut manquant, alors la déclinaison perdra tous ces attributs ou celui qui est manquant. Il est donc nécéssaire de déclarer systématiquement tous les attrubuts d'une déclinaison.
