If you have flows form supplier, you may want to remove products when they disappears from the XML.

It's possible to remove missing products in flows since the version 1.22.0 of the module.

For that you need to add the attribute "autodelete" to your flows. This attribute must have the supplier name as value.

For example, this flow will create three product "Name 1", "Name 2" and "Name 3":
```
<?xml version="1.0" encoding="UTF-8"?>
<products autodelete="test">
	<product external-reference="demo-1">
		<name>Name 1</name>
		<description >Product description</description>
		<price>20</price>
	</product>
	<product external-reference="demo-2">
		<name>Name 2</name>
		<description >Product description</description>
		<price>20</price>
	</product>
	<product external-reference="demo-3">
		<name>Name 2</name>
		<description >Product description</description>
		<price>20</price>
	</product>
</products>
```

If one product is missing in the next import, it will be automatically removed:
```
<?xml version="1.0" encoding="UTF-8"?>
<products autodelete="test">
	<product external-reference="demo-1">
		<name>Name 1</name>
		<description >Product description</description>
		<price>20</price>
	</product>
	<product external-reference="demo-3">
		<name>Name 2</name>
		<description >Product description</description>
		<price>20</price>
	</product>
</products>
```

On the previous example the product "Name 2" will be removed.
