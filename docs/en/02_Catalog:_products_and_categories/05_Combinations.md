A variant is an alternative version of the product with different attributes. This can be for instance products with different colours. 

A variant is composed of one or several attributes. Each attribute belongs to a group of attributes. A variant has at its maximum one attribute per group of attributes. 

## Creation of attributes and groups of attributes via the flow object

The creation of new attributes is made via the flow object.

Creation of attributes and values of attributes:

```
<objects>
	<object type="attributeGroup" external-reference="demo-recto-color">
		<is_color_group>1</is_color_group>
		<group_type>color</group_type>
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
			<url>/modules/advancedimporter/img/media/01.jpg</url> <!-- from local storage -->
		</images>
		<combinations external-reference="combination-1">
			<price>10.5</price>
			<unit_price_impact>0</unit_price_impact>
			<images>1</images>
			<attributes use-external-reference="1">demo-recto-color-blue</attributes>
		</combinations>
		<combinations external-reference="combination-2">
			<price>11.5</price>
			<unit_price_impact>0</unit_price_impact>
			<images>1</images>
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
			<url>/modules/advancedimporter/img/media/01.jpg</url> <!-- from local storage -->
		</images>
		<block>
			<objects>
				<object type="attributeGroup" external-reference="demo-recto-color">
					<is_color_group>1</is_color_group>
					<group_type>color</group_type>
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
				<object type="attribute" external-reference="demo-recto-color-red">
					<external_reference for="id_attribute_group" type="attributeGroup">demo-recto-color</external_reference>
					<color>#E84C3D</color>
					<name>Red</name>
					<block>
						<products>
							<product>
								<id>{{id}}</id>
								<combinations external-reference="combination-1">
									<price>10.5</price>
									<unit_price_impact>0</unit_price_impact>
									<images>1</images>
									<attributes use-external-reference="1">demo-recto-color-blue</attributes>
								</combinations>
								<combinations external-reference="combination-2">
									<price>11.5</price>
									<unit_price_impact>0</unit_price_impact>
									<images>1</images>
									<attributes use-external-reference="1">demo-recto-color-red</attributes>
								</combinations>
							</product>
						</products>
					</block>
				</object>
			</objects>
		</block>
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
