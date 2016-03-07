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

The module don't delete the images of a product at each importation. Each images is replaced by a new one with the same url. In other cases a new image will be created. To replace all existing images you have to use the attribute "insertion" with the value "replace":
```
<products>
	<product external-reference="product-demo-1" >
		<name>Name</name>
		<description>Description of the product</description>
		<images insertion="replace">
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
		<images update="0">
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
