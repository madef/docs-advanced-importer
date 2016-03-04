If you import an object or a product with an identifier field (ean, id, external reference, reference), and if the object or the product exists, it will be updated.

Since the version 1.22.0 of the module, it's possible to lock this mechanism to only allow the creation.

For example, this flow will create a product named "Name 1". The product will not updated because the second block has the attribute "update" set to "0".
```
<?xml version="1.0" encoding="UTF-8"?>
<products>
	<product external-reference="demo-1">
		<name>Name 1</name>
		<description >Product description</description>
		<price>20</price>
	</product>
	<product external-reference="demo-1" update="0">
		<name>Name 2</name>
		<description >Product description</description>
		<price>20</price>
	</product>
</products>
```
