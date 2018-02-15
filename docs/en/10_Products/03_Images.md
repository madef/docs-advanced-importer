To add an image to a product, use the “image” node:
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image</legend>
        </image>
    </product>
</advancedimporter>
```

The image can originate from a URL as in the previous example, or from the server itself: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <image>
            <url>/modules/advancedimporter/views/img/media/01.jpg</url>
            <legend>My image</legend>
        </image>
    </product>
</advancedimporter>
```

If you’ve tried both of the previous examples, you’ll have noticed that the product now has two images. If your feed lists all the product images, missing images can be deleted using the “remove-missing-images” attribute:
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-images="yes">
        <name>test</name>
        <price>10</price>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image</legend>
        </image>
    </product>
</advancedimporter>
```

If you wish to add several images, repeat the image tag, not the URL tag: 
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-images="yes">
        <name>test</name>
        <price>10</price>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image 1</legend>
        </image>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-2.jpg</url>
            <legend>My image 2</legend>
        </image>
    </product>
</advancedimporter>
```

Image order can also be defined using the “position” node: 
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-images="yes">
        <name>test</name>
        <price>10</price>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image 1</legend>
            <position>2</position>
        </image>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-2.jpg</url>
            <legend>My image 2</legend>
            <position>1</position>
        </image>
    </product>
</advancedimporter>
```

You can also define which image to use as the cover image:
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-images="yes">
        <name>test</name>
        <price>10</price>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image 1</legend>
            <cover>0</cover>
        </image>
        <image>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-2.jpg</url>
            <legend>My image 2</legend>
            <cover>1</cover>
        </image>
    </product>
</advancedimporter>
```

## Optimization

Downloading images can take time and is often the reason for slow imports. To avoid downloading images that are already present, it is recommended that the “mode” attribute is used with the “create” value. In addition, only images that do not yet exist (unknown URL) will be downloaded. 

```
<advancedimporter>
    <product supplier-reference="test" remove-missing-images="yes">
        <name>test</name>
        <price>10</price>
        <image mode="create">
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image 1</legend>
        </image>
        <image mode="create">
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-2.jpg</url>
            <legend>My image 2</legend>
        </image>
    </product>
</advancedimporter>
```

## Missing pictures

If an image is missing, the import process of the product is stopped. To avoid that, it's possible to add the attribute « ignore-not-found »:
```
<advancedimporter>
    <product supplier-reference="test" remove-missing-images="yes">
        <name>test</name>
        <price>10</price>
        <image ignore-not-found="yes">
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image 1</legend>
        </image>
    </product>
</advancedimporter>
```
