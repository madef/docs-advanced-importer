PrestaShop XML Importer is conciliable with the multishop.

For this, it is only necessary to specify the shop or the shops in the flows.

Addition of a product in the shops 1 and 3:

```
<products>
	<product external-reference="demo-3">
		<shop>1</shop>
		<shop>3</shop>
		<reference>ref01</reference>
		<name>Name</name>
		<description>Product description</description>
		<price>19.99</price>
	</product>
</products>
```

**Beware, if the external reference is not specified, the product will be created twice (once by shop).**

Addition of a product in the shops 1 and 2. then the modification of the title is needed in the shop 1:

```
<products>
	<product external-reference="demo-4">
		<shop>1</shop>
		<shop>2</shop>
		<name lang="en">Name</name>
		<description lang="en">Product description</description>
		<price>19.99</price>
	</product>
	<product external-reference="demo-4">
		<shop>2</shop>
		<reference>ref01</reference>
		<name lang="en">New name</name>
	</product>
</products>
```
