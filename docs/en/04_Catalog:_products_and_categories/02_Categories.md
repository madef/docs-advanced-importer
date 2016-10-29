There are different ways to create categories. Either via the flow object: The category in this case is not linked to another product (the flow association will be used to link it to a product.) Or, via the flow product: in this case, the category will be linked to the product. 

## Creation of categories via the flow object

Creation of a category:

```
<objects>
	<object type="category" external-reference="demo-1">
		<name>Name of the category</name>
		<link_rewrite>Name</link_rewrite>
		<id_parent>2</id_parent>
	</object>
	<object type="category" external-reference="demo-2">
		<name>Name of the category</name>
		<link_rewrite>Name</link_rewrite>
		<id_parent>2</id_parent>
	</object>
</objects>
```

Creation of a category with the parent file external reference demo-1:

```
<objects>
	<object type="category" external-reference="demo-3">
		<name>Name of the category</name>
		<link_rewrite>Name</link_rewrite>
		<external_reference for="id_parent" type="category">demo-1</external_reference>
	</object>
</objects>
```

## The attachment of products to categories

The flow association enables to link products (identified by their id, code ean13, reference or external reference) to categories named by their id or external reference.

The attachment of a product with the external reference demo-1 to the category demo-1 and demo-2:

```
<associations>
	<association external-reference="demo-1">
		<mode>replace</mode>
		<category use-external-reference="1">demo-1</category>
		<category use-external-reference="1">demo-2</category>
	</association>
</associations>
```

The attachment of a product with the external reference demo-1 to the category #1 and #2:

```
<associations>
	<association external-reference="demo-1">
		<mode>replace</mode>
		<category>1</category>
		<category>2</category>
	</association>
</associations>
```

The use of the ean13, reference and id:

```
<associations>
	<association productid="1">
		<mode>replace</mode>
		<category use-external-reference="1">demo-1</category>
		<category use-external-reference="1">demo-2</category>
	</association>
	<association ean13="ean-1">
		<mode>replace</mode>
		<category use-external-reference="1">demo-1</category>
		<category use-external-reference="1">demo-2</category>
	</association>
	<association reference="reference-1">
		<mode>replace</mode>
		<category use-external-reference="1">demo-1</category>
		<category use-external-reference="1">demo-2</category>
	</association>
</associations>
```

The mode enables to either replace all the categories of the product or to add one.

An example of the use of the "addition" mode:

```
<associations>
	<association external-reference="demo-1">
		<mode>add</mode>
		<category use-external-reference="1">demo-3</category>
	</association>
</associations>
```

## Creation of categories in the flow product

The flow product enables to create and attach categories directly. This is possible either by using the tab "categorypath" or by using the blocks.

The first solution is the most simple but also the most limited, as only the name of the category can be personified. If the category exists, then the product is simply attached to this same category. 

Using the categorypath:

```
<products>
	<product external-reference="demo-1" >
		<name>Name</name>
		<description>Product description</description>
		<categorypath separator="&gt;"><![CDATA[cat1 > cat2 > cat3]]></categorypath> <!-- Add product in category cat1 > cat2 > cat3 -->
		<price>19.99</price>
	</product>
</products>
```

With the use of blocks, it is necessary to create first a category and secondly to make the attachment. Beware, in this case the use of the external reference is mandatory. 

The use of blocks to associate a product to a category:

```
<products>
	<product external-reference="demo-1">
		<name>Name</name>
		<description>Product description</description>
		<price>19.99</price>
		<block>
			<objects>
				<object type="category" external-reference="demo-1">
					<name>Name</name>
					<link_rewrite>Name</link_rewrite>
					<id_parent>1</id_parent>
					<block>
						<associations>
							<association productid="{{id}}">
								<mode>add</mode>
								<category>#{#{id}#}#</category>
							</association>
						</associations>
					</block>
				</object>
			</objects>
		</block>
	</product>
</products>
```

## Add a group to a category

By default, categories are attached to the defaut group of PrestaShop. To add more group you need to insert an object CategoryGroup:

```<?xml version="1.0"?>
<objects>
  <object type="CategoryGroup">
	<id_category>191</id_category>
	<id_group>4</id_group>
  </object>
  <object type="CategoryGroup">
	<id_category>191</id_category>
	<id_group>4</id_group>
  </object>
</objects>
```

To detach group, you have to use the flow delete:

```
<delete>
    <object type="CategoryGroup" id="191-2" />
</delete>
```


## Attach category to a shop

```<?xml version="1.0"?>
<objects>
  <object type="CategoryShop">
	<id_category>191</id_category>
	<id_shop>1</id_shop>
  </object>
  <object type="CategoryShop">
	<id_category>191</id_category>
	<id_shop>2</id_shop>
	<position>78</position>
  </object>
</objects>
```
