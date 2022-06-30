To create a tags, it's necessary to use an object flow:

```
<objects>
	<object type="tag" external-reference="demo-tag-1">
		<id_lang>1</id_lang>
		<name>test</name>
	</object>
</objects>
```


Create a produit, a tag and linked the tag to the product:

```
<products>
	<product external-reference="demo-1">
		<name lang="en">Name</name>
		<description lang="en">Description</description>
		<price>20</price>
		<block>
			<objects>
				<object type="tag" external-reference="demo-tag-1">
					<id_lang>1</id_lang>
					<name>test</name>
				</object>
				<object type="entityLink" external-reference="tag_demo-1">
					<table_name>product_tag</table_name>
					<entity_left_name>id_product</entity_left_name>
					<entity_right_name>id_tag</entity_right_name>
					<external_reference for="id_entity_left" type="product">demo-1</external_reference>
					<external_reference for="id_entity_right" type="tag">demo-tag-1</external_reference>
				</object>
			</objects>
		</block>
	</product>
</products>
```
