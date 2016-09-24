Link a product to an other as an accessory:

```
<objects>
	<object type="entityLink" external-reference="accessory_demo-1_demo-2">
		<table_name>accessory</table_name>
		<entity_left_name>id_product_1</entity_left_name>
		<entity_right_name>id_product_2</entity_right_name>
		<id_entity_left>1</id_entity_left>
		<id_entity_right>2</id_entity_right>
	</object>
</objects>
```

Example with a products flow:
```
<products>
	<product external-refrence="demo-1">
		<name>Accessory</name>
		<description >Product description</description>
		<price>20</price>
	</product>
	<product external-refrence="demo-2">
		<name>Product</name>
		<description >Product description</description>
		<price>20</price>
		<block>
        	<objects>
				<object type="entityLink" external-reference="accessory_demo-2_demo-1">
			    	<table_name>accessory</table_name>
		    		<entity_left_name>id_product_1</entity_left_name>
	    			<entity_right_name>id_product_2</entity_right_name>
    				<external_reference for="id_entity_left" type="Product">demo-2</external_reference>
			    	<external_reference for="id_entity_right" type="Product">demo-1</external_reference>
				</object>
			</objects>
		</block>
	</product>
</products>
```
