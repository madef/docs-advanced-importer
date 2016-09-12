## Taxes

By default the price of the products are tax exclude. It's poossible to define the price as tax inclide by using the tag price_type:

```
<products>
	<product external-reference="demo-1">
		<name>Name</name>
		<description>Product description</description>
		<categorypath separator="&gt;"><![CDATA[cat1 > cat2 > cat3]]></categorypath> <!-- Add product in category cat1 > cat2 > cat3 -->
		<price_type>ti</price_type> <!-- ti = tax include, te (default) = tax exclude -->
		<price>19.99</price>
	</product>
</products>
```

It's also possible to define customs fields as tax fields:

```
<products>
	<product external-reference="demo-1">
		<name>Name</name>
		<description>Product description</description>
		<<categorypath separator="&gt;"><![CDATA[cat1 > cat2 > cat3]]></categorypath> <!-- Add product in category cat1 > cat2 > cat3 -->
		<tax_fields>custom_tax</tax_fields>
		<price_type>ti</price_type> <!-- ti = tax include, te (default) = tax exclude -->
		<price>19.99</price>
	</product>
</products>
```

## Specific prices 

The specific prices can be created by using the flow object:

```
<objects>
	<object type="specificPrice" external-reference="demo-1">
		<external_reference for="id_product" type="product">demo-1</external_reference>
		<id_group>1</id_group>
		<price>-1</price>
		<reduction>0.2</reduction>
		<reduction_type>percentage</reduction_type> <!-- or amount -->
		<from_quantity>1</from_quantity>
		<id_customer>0</id_customer>
		<id_shop>0</id_shop>
		<id_country>0</id_country>
		<id_currency>0</id_currency>
		<from>0000-00-00</from>
		<to>0000-00-00</to>
	</object>
</objects>
```

Example of a flow product with a 20% discount:

```
<products>
	<product external-reference="demo-1">
		<name>Name</name>
		<description>Product description</description>
		<price>19.99</price>
		<block>
			<objects>
				<object type="specificPrice">
					<id_product>{{id}}</id_product>
					<id_group>1</id_group>
					<price>-1</price>
					<reduction>0.2</reduction>
					<reduction_type>percentage</reduction_type> <!-- or amount -->
					<from_quantity>1</from_quantity>
					<id_customer>0</id_customer>
					<id_shop>0</id_shop>
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
Example of a flow product with a $20 :

```
<products>
	<product external-reference="demo-1">
		<name>Name</name>
		<description>Product description</description>
		<price>19.99</price>
		<block>
			<objects>
				<object type="specificPrice">
					<id_product>{{id}}</id_product>
					<id_group>1</id_group>
					<price>-1</price>
					<reduction>20</reduction>
					<reduction_type>amount</reduction_type> <!-- or percentage -->
					<from_quantity>1</from_quantity>
					<id_customer>0</id_customer>
					<id_shop>0</id_shop>
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
