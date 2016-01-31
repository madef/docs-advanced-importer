Link a product to an other as an accessory:

```
<objects>
	<object type="entityLink" external-reference="accessory_demo-1_demo-2">
		<table_name>accessory</table_name>
		<entity_left_name>id_product_1</entity_left_name>
		<entity_right_name>id_product_2</entity_right_name>
		<id_entity_left>1</id_entity_left>
		<id_entity_right>2</id_entity_right>
	<external_reference for="id_entity_left" type="product">demo-1</external_reference> <!-- External reference of the product -->
	<external_reference for="id_entity_right" type="tag">demo-2</external_reference> <!-- External reference of the accessory -->
	</object>
</objects>
```
