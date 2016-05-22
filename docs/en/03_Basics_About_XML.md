The module integrates by default, six types of flow XML :
 * products
 * stock
 * attachment to categories
 * object
 * attachment
 * delete

If you have knowledge on PHP, it is possible to add others thanks to the creation of new importers.

The module can import almost any flow format without coding even one line. To do this, it is necessary to create a [XSLT](Customize/Support_Your_Own_XML_Format) format. 

## Flow product

The flow product is the flow the most complete. The major part of this document concerns this flow. Even though other flows are used for the stock management and the attachment to categories, it is possible to use directly the flow product without using this one. 

First, we will show you some basic examples. 

Do not forget that if you have not activated this module, import the flow by typing the url [http://localhost/prestashop/modules/advancedimporter/cron.php?debug](http://localhost/prestashop/modules/advancedimporter/cron.php?debug).

Please find an example of the development of the most basic product. Do not forget to change the language to the one used in your shop:
```
<products>
	<product external-reference="demo-1">
		<name>Name</name>
		<description>Product description</description>
		<price>20</price>
	</product>
</products>
```

If a product has already been created, consequently any flow using the same external reference, id, ean13 or reference will modify the product instead of creating a new one:

```
<products>
	<product>
		<id>12</id>
		<name>Name</name>
		<description>Product description</description>
		<price>19.99</price>
	</product>
	<product>
		<reference>demo_1</reference>
		<name>Name</name>
		<description>Product description</description>
	<price>19.99</price>
	</product>
	<product>
		<ean13>1111111111111</ean13>
		<name>Name</name>
		<description>Product description</description>
		<price>19.99</price>
	</product>
	<product external-reference="product-demo-1" >
		<name>Name</name>
	</product>
</products>
```

It is recommended to use the external reference to be identified by the exterior. 

It is possible to import pictures either via HTTP, or from the server:

```
<products>
	<product external-reference="product-demo-1" >
		<name>Name</name>
		<description>Product description</description>
		<images>
			<url>/modules/advancedimporter/img/media/01.jpg</url> <!-- from local storage -->
			<url>http://prestashopxmlimporter.madef.fr/img/demo.jpg</url> <!-- from a server -->
		</images>
	</product>
</products>
```

It is possible to define taxes, either by using the wording of the rule, or by using its id:

```
<products>
	<product external-reference="product-demo-1" >
		<name>Name</name>
		<description>Product description</description>
		<price>19.99</price>
		<tax>Tax rule name</tax>
	</product>
	<product external-reference="product-demo-2" >
		<name>Name</name>
		<description>Product description</description>
		<price>19.99</price>
		<id_tax_rules_group>1</id_tax_rules_group>
	</product>
</products>
```

**Beware: it is not possible to define directly the tax rate.**

The flow produced can modify the following attributes of a product: ([view full list](Other/Attributes_List)) :

Product:

* id_shop_default
* id_manufacturer
* id_supplier
* reference
* supplier_reference
* location
* width
* height
* depth
* weight
* quantity_discount
* ean13
* upc
* cache_is_pack
* cache_has_attachments
* is_virtual
* id_category_default
* id_tax_rules_group
* on_sale
* online_only
* ecotax
* minimal_quantity
* price
* wholesale_price
* unity
* unit_price_ratio
* additional_shipping_cost
* customizable
* text_fields
* uploadable_files
* active
* redirect_type
* id_product_redirected
* available_for_order
* available_date
* condition
* show_price
* indexed
* visibility
* cache_default_attribute
* advanced_stock_management
* date_add
* date_upd
* meta_description
* meta_keywords
* meta_title
* link_rewrite
* name
* description
* description_short
* available_now
* available_later

In all these examples, were defined an attribute "external-reference". This is not necessary but highly recommended, it enables to make a link between the external environment (the flow XML) and your shop.

## Flow object

The flow object allows the importation of any type of PrestaShop object. These enable the integration of several types of objects in one same file. 

Don’t forget that if you have not activated the module, in order to upload the flow you must type the url [http://localhost/prestashop/modules/advancedimporter/cron.php?debug](http://localhost/prestashop/modules/advancedimporter/cron.php?debug).

Importation of a product and a category:

```
<objects>
	<object type="category" external-reference="demo-1">
		<name>Category name</name>
		<link_rewrite>Name</link_rewrite>
	</object>
	<object type="product" external-reference="demo-1">
		<name>Product name</name>
		<link_rewrite>Name</link_rewrite>
	</object>
</objects>
```

You can find all the attributes which can be modified in the file [here](Other/Attributes_List).

## External Reference 

The external references enable to make a link between the flow (external environment) and your shop. The reference can be used in the flow object and product. It is used with the addition of an attribute **external-reference**. The references are unique for each type of entity. Consequently, it is possible to obtain a category and a product with the same external reference without any clashes (cf the precedent example). The ernernal reference is limited to 255 chars.

Example of the use of external references:

```
<objects>
	<object type="taxRulesGroup" external-reference="tax-1">
		<name>Tax rule goup name</name>
	</object>
</objects>
```

In addition to the fact of allowing the identification of each entity with the purpose of updating them, it is also possible to refer to them for some of their attributes. Imagine for instance, that you wish to import a product by specifying the tax via its external reference.

Definition of a tax via the external references:

```
<products>
	<product external-reference="demo-1">
		<name>Name</name>
		<description>Product description</description>
		<price>20</price>
		<external_reference for="id_tax_rules_group" type="taxRulesGroup">tax-1</external_reference>
	</product>
</products>
```

Another example, let’s imagine that you wish to create an attribute with values.

Creation of an attribute and values:

```
<objects>
	<object type="feature" external-reference="feature-test">
		<name>Test feature</name>
	</object>
	<object type="featureValue" external-reference="feature-value-test">
		<value>Test value</value>
		<external_reference for="id_feature" type="feature">feature-test</external_reference>
	</object>
</objects>
```

## Find entities

If you want to edit objects not created by flows you cannot use the external reference. If there is a way to identifier the entitie, you can use "findOne".

Here is an example of editing a customer:

```
<objects>
	<object type="Customer">
		<findOne
			for="id"
			type="Customer"
			identifier="id"
		>
			<email>test@domain.tld</email>
		</findOne>
		<firstname>Test</firstname>
		<lastname>Test</lastname>
	</object>
</objects>
```

## Notion of block

The flow product and object enables the modification or the creation of entities. In some cases, it can be useful to include the flows in the entities. To do this, the tag "block" is used to create for instance a product with a discount (specific price).

Example of a flow product with a 20% discount:

```
<products>
	<product external-reference="demo-1">
		<name>Name</name>
		<description>Product description</description>
		<price>19.99</price>
		<block>
			<objects>
				<object external-reference="specific-price-1" type="specificPrice">
					<id_product>{{id}}</id_product>
					<id_group>1</id_group>
					<price>0</price>
					<reduction>0.2</reduction>
					<reduction_type>percentage</reduction_type> <!-- or amount -->
					<from_quantity>1</from_quantity>
					<id_customer>0</id_customer>
					<id_shop>1</id_shop>
					<id_country>0</id_country>
					<id_currency>0</id_currency>
					<from>0000-00-00</from>
					<to>0000-00-00</to>
				</object>
			</objects>
		</block>
	</product>
</products>
```

In order to link the entity to the block, we can use the ID of the product that can be named {{id}}.

Blocks can nested. In this case, the {{id}} must be protected with sharps: #{#id}#}#.

## Flow delete

To remove entities, we use a flow of type "delete". It’s similar to the flow “object”. 

Example of removing a customer and a group ([delete-1.xml](http://prestashopxmlimporter.madef.fr/flows_en/delete-1.xml)) :

```
<delete>
    <object type="customer" external-reference="demo-1" />
    <object type="group" external-reference="demo-1" />
    <object type="customerGroup" external-reference="demo-1" />
</delete>
```
