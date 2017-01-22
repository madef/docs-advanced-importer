A variant is an alternative version of the product with different attributes. This can be for instance products with different colours. 

A variant is composed of one or several attributes. Each attribute belongs to a group of attributes. A variant has at its maximum one attribute per group of attributes. 

## Creation of attributes and groups of attributes via the flow object

The creation of new attributes is made via the flow object.

Creation of attributes and values of attributes:

```
<objects>
	<object type="attributeGroup" external-reference="demo-recto-color">
		<is_color_group>1</is_color_group>
		<group_type>color</group_type> <!-- Used for the layered navigation: select, radio or color -->
		<name>Color of the front</name>
		<public_name>Color of the front</public_name>
	</object>
	<object type="attribute" external-reference="demo-recto-color-gray">
		<external_reference for="id_attribute_group" type="attributeGroup">demo-recto-color</external_reference>
		<color>#AAB2BD</color>
		<name>Gray</name>
	</object>
	<object type="attribute" external-reference="demo-recto-color-blue">
		<external_reference for="id_attribute_group" type="attributeGroup">demo-recto-color</external_reference>
		<color>#5D9CEC</color>
		<name>Blue</name>
	</object>
	<object type="attribute" external-reference="demo-recto-color-rouge">
		<external_reference for="id_attribute_group" type="attributeGroup">demo-recto-color</external_reference>
		<color>#E84C3D</color>
		<name>Red</name>
	</object>
</objects>
```

## Creation of variants from the flow product 

Creation or modification of two variants:

```
<products>
	<product external-reference="product-demo-1" >
		<name>Name</name>
		<description>Product description</description>
		<price>19.99</price>
		<images>
			<url>http://prestashopxmlimporter.madef.fr/en/numbers/number-1.jpg</url>
		</images>
		<combinations external-reference="combination-1">
			<price>10.5</price>
			<unit_price_impact>0</unit_price_impact>
			<images>
			    <url>http://prestashopxmlimporter.madef.fr/en/numbers/number-1.jpg</url>
			</images>
			<attributes use-external-reference="1">demo-recto-color-blue</attributes>
		</combinations>
		<combinations external-reference="combination-2">
			<price>11.5</price>
			<unit_price_impact>0</unit_price_impact>
			    <url>http://prestashopxmlimporter.madef.fr/en/numbers/number-2.jpg</url>
			<attributes use-external-reference="1">demo-recto-color-red</attributes>
		</combinations>
	</product>
</products>
```

## Creation of attributes and of variants in the flow product 

In order to create the attributes and their values in the flow product, we use the [blocks](Basics_About_XML):

```
<products>
	<product external-reference="product-demo-1">
		<name>Name</name>
		<description>Product description</description>
		<price>19.99</price>
		<images>
		    <url>http://prestashopxmlimporter.madef.fr/en/numbers/number-1.jpg</url>
		</images>
		<block>
			<objects>
				<object type="attributeGroup" external-reference="demo-recto-color" update="0">
					<is_color_group>1</is_color_group>
					<group_type>color</group_type>
					<name>Color of the front</name>
					<public_name>Color of the front</public_name>
				</object>
				<object type="attribute" external-reference="demo-recto-color-gray" update="0">
					<external_reference for="id_attribute_group" type="attributeGroup">demo-recto-color</external_reference>
					<color>#AAB2BD</color>
					<name>Gray</name>
				</object>
				<object type="attribute" external-reference="demo-recto-color-blue" update="0">
					<external_reference for="id_attribute_group" type="attributeGroup">demo-recto-color</external_reference>
					<color>#5D9CEC</color>
					<name>Blue</name>
				</object>
				<object type="attribute" external-reference="demo-recto-color-red" update="0">
					<external_reference for="id_attribute_group" type="attributeGroup">demo-recto-color</external_reference>
					<color>#E84C3D</color>
					<name>Red</name>
				</object>
			</objects>
			<products>
				<product>
					<id>{{id}}</id>
					<combinations external-reference="combination-1">
						<price>10.5</price>
						<unit_price_impact>0</unit_price_impact>
						<images>
							<url>http://prestashopxmlimporter.madef.fr/en/numbers/number-1.jpg</url>
						</images>
						<attributes use-external-reference="1">demo-recto-color-blue</attributes>
					</combinations>
					<combinations external-reference="combination-2">
						<price>11.5</price>
						<unit_price_impact>0</unit_price_impact>
						<images>
			                <url>http://prestashopxmlimporter.madef.fr/en/numbers/number-2.jpg</url>
						</images>
						<attributes use-external-reference="1">demo-recto-color-red</attributes>
					</combinations>
				</product>
			</products>
		</block>
	</product>
</products>
```

## Don't remove combination not specified

By defaut the combination of the product not specified will be removed. You can avoid that by adding the attribute "autodelete-combinations" with the value "0":

```
<products>
	<product autodelete-combinations="0" external-reference="product-demo-1" >
		<name>Name</name>
		<description>Product description</description>
		<price>19.99</price>
		<images>
			<url>http://prestashopxmlimporter.madef.fr/en/numbers/number-1.jpg</url>
		</images>
		<combinations external-reference="combination-1">
			<price>10.5</price>
			<unit_price_impact>0</unit_price_impact>
			<images>
			    <url>http://prestashopxmlimporter.madef.fr/en/numbers/number-1.jpg</url>
			</images>
			<attributes use-external-reference="1">demo-recto-color-blue</attributes>
		</combinations>
		<combinations external-reference="combination-2">
			<price>11.5</price>
			<unit_price_impact>0</unit_price_impact>
			    <url>http://prestashopxmlimporter.madef.fr/en/numbers/number-2.jpg</url>
			<attributes use-external-reference="1">demo-recto-color-red</attributes>
		</combinations>
	</product>
</products>
```

## Define textures to attributes

PrestaShop allow to use textures (small images) instead of color for the color attributes.

Here is an example of a flow with a texture:
```
<objects>
	<object type="attribute" external-reference="demo-recto-color-rouge">
		<external_reference for="id_attribute_group" type="attributeGroup">demo-recto-color</external_reference>
		<color>#E84C3D</color>
		<texture>http://domain.com/texture.jpg</texture> <!-- a path or an url -->
		<name>Red</name>
	</object>
</objects>
```

To remove the texture, set an empty value:
```
<objects>
	<object type="attribute" external-reference="demo-recto-color-rouge">
		<external_reference for="id_attribute_group" type="attributeGroup">demo-recto-color</external_reference>
		<color>#E84C3D</color>
		<texture></texture>
		<name>Red</name>
	</object>
</objects>
```

## Define a combination as default combination:
```
<products>
	<product autodelete-combinations="0" external-reference="product-demo-1" >
		<name>Name</name>
		<description>Product description</description>
		<price>19.99</price>
		<images>
			<url>http://prestashopxmlimporter.madef.fr/en/numbers/number-1.jpg</url>
		</images>
		<combinations external-reference="combination-1">
			<price>10.5</price>
			<unit_price_impact>0</unit_price_impact>
			<images>
			    <url>http://prestashopxmlimporter.madef.fr/en/numbers/number-1.jpg</url>
			</images>
			<attributes use-external-reference="1">demo-recto-color-blue</attributes>
		</combinations>
		<combinations external-reference="combination-2">
			<default_on>1</default_on>
			<price>11.5</price>
			<unit_price_impact>0</unit_price_impact>
			    <url>http://prestashopxmlimporter.madef.fr/en/numbers/number-2.jpg</url>
			<attributes use-external-reference="1">demo-recto-color-red</attributes>
		</combinations>
	</product>
</products>
```
