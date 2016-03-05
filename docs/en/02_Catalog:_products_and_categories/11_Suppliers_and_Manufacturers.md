## Manufaturer

Here is an example of importing a product with a manufacturer:

```
<?xml version="1.0" encoding="UTF-8"?>
<products>
	<product external-reference="product-1">
		<name>Name</name>
		<description >Product description</description>
		<price>20</price>
		<block>
			<objects>
				<object update="0" type="Manufacturer" external-reference="manufacturer-1">
					<name>Manufacturer</name>
					<active>1</active>
				</object>
			</objects>
			<products>
				<product external-reference="product-1">
					<external_reference for="id_manufacturer" type="Manufacturer">manufacturer-1</external_reference>
				</product>
			</products>
		</block>
	</product>
</products>
```

## Supplier

Here is an example of importing a product with a supplier:

```
<?xml version="1.0" encoding="UTF-8"?>
<products>
	<product external-reference="product-1">
		<name>Name 2</name>
		<description >Product description</description>
		<price>20</price>
		<block>
			<objects>
				<object update="0" type="Supplier" external-reference="supplier-1">
					<name>Supplier</name>
					<active>1</active>
				</object>
				<object update="0" type="ProductSupplier" external-reference="product-1_supplier-1">
					<external_reference for="id_product" type="Product">product-1</external_reference>
					<id_product_attribute>0</id_product_attribute>
					<external_reference for="id_supplier" type="Supplier">supplier-1</external_reference>
				</object>
			</objects>
		</block>
	</product>
</products>
```
