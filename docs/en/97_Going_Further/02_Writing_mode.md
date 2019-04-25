For various reasons, you may wish to avoid modifying an existing product. In this case, you need to place the “mode” field into the entity’s root tag. This field may take the following values: 
- create: to only create
- update: to only update
- both: to create and modify 

To avoid modifying an existing product: 
```
<advancedimporter>
    <product mode="create" supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

To avoid creating the product if it doesn’t exist: 
```
<advancedimporter>
    <product mode="update" supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

These two examples create or modify the product: 
```
<advancedimporter>
    <product mode="both" supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

If you want to avoid modifying a field when updating a product, the mode needs to be defined in the field tag: 
```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name mode="create">Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

The opposite is also possible:
```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name mode="update">Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

You can also want to create/modify a child entity if the main entity is on creation or on updating.

In this example, the image is not added or update if product exists:

```
<advancedimporter>
    <product supplier-reference="demo-2">
        <name>Name</name>
        <price>10</price>
        <image mode="createparent">
            <url>http://prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image</legend>
        </image>
    </product>
</advancedimporter>
```

In this example, the image is added/updated only if the product exists :

```
<advancedimporter>
    <product supplier-reference="demo-3">
        <name>Name</name>
        <price>10</price>
        <image mode="updateparent">
            <url>http://prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
            <legend>My image</legend>
        </image>
    </product>
</advancedimporter>
```
