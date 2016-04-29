Here is an example of the flow product with two images:

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

## Replace old images

The module don't delete the images of a product at each importation.

Each images is replaced by a new one with the same url. In other cases a new image will be created.

To replace all existing images you have to use the attribute "insertion" with the value "replace":
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

## Set legend

To add a legend, you have to use the attribute "legend":
```
<products>
	<product external-reference="product-demo-1" >
		<name>Name</name>
		<description>Description of the product</description>
		<images>
			<url legend="Image description">/modules/advancedimporter/img/media/01.jpg</url> <!-- from local storage -->
		</images>
	</product>
</products>
```

## Set position

By default the module calculate the position of the image. To define a custom position use the attribute "position":
```
<products>
	<product external-reference="product-demo-1" >
		<name>Name</name>
		<description>Description of the product</description>
		<images>
			<url position="1">http://prestashopxmlimporter.madef.fr/en/numbers/number-1.jpg</url>
			<url position="2">http://prestashopxmlimporter.madef.fr/en/numbers/number-2.jpg</url>
		</images>
	</product>
</products>
```

## Set cover

By default the module define the first image as the cover. It's possible to define a custom cover:
```
<products>
	<product external-reference="product-demo-1" >
		<name>Name</name>
		<description>Description of the product</description>
		<images>
			<url cover="0">http://prestashopxmlimporter.madef.fr/en/numbers/number-1.jpg</url>
			<url cover="1">http://prestashopxmlimporter.madef.fr/en/numbers/number-2.jpg</url>
		</images>
	</product>
</products>
```

## Define external reference

Like any other objects, images can be referenced with an external reference:
```
<products>
	<product external-reference="product-demo-1" >
		<name>Name</name>
		<description>Description of the product</description>
		<images>
			<url external-reference="demo-1">http://prestashopxmlimporter.madef.fr/en/numbers/number-1.jpg</url>
			<url external-reference="demo-2">http://prestashopxmlimporter.madef.fr/en/numbers/number-2.jpg</url>
		</images>
	</product>
</products>
```

## Optimize upload

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

You can also add the "update" attribute to a specific image:

```
<products>
	<product external-reference="product-demo-1" >
		<name>Name</name>
		<description>Description of the product</description>
		<images>
			<url update="0">/modules/advancedimporter/img/media/01.jpg</url> <!-- from local storage -->
			<url>http://prestashopxmlimporter.madef.fr/img/demo.jpg</url> <!-- from a server -->
		</images>
	</product>
</products>
```
