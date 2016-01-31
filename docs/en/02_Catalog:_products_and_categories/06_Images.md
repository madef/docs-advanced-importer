Here is an example of the flow product with two images :

```
<products>
	<product external-reference="product-demo-1" >
		<name>Name</name>
		<description>Description of the product</description>
		<images>
			<url>/modules/advancedimporter/img/media/01.jpg</url> <!-- from local storage -->
			<url>http://prestashopxmlimporter.madef.fr/img/demo.jpg</url> <!-- from a server -->
		</images>
	</product>
</products>
```

Download images can be slow. The images are downloaded even if they already exist. If you do not need this behavior, you must add the attribute "update":

```
<products>
	<product external-reference="product-demo-1" >
		<name>Name</name>
		<description>Description of the product</description>
		<images>
			<url>/modules/advancedimporter/img/media/01.jpg</url> <!-- from local storage -->
			<url>http://prestashopxmlimporter.madef.fr/img/demo.jpg</url> <!-- from a server -->
		</images>
	</product>
</products>
```

It's possible to download image for categories:

```
<objects>
	<object type="category" external-reference="demo-1">
		<name>Category name</name>
		<link_rewrite>Name</link_rewrite>
		<image>/modules/advancedimporter/img/media/01.jpg</image>
	</object>
</objects>
```
