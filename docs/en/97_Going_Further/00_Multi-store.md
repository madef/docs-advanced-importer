To manage importing to multiple stores, the entity ID of the store needs to be defined in the root tag.

For example, if you want to import a product into only stores 2 and 3, you would proceed as follows: 
```
<advancedimporter>
    <product shop="2" supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
    <product shop="3" supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

If you want to use a different product name in each of your stores, you proceed as follows: 
```
<advancedimporter>
    <product shop="2" supplier-reference="demo-1">
        <name>Name 1</name>
        <price>0</price>
    </product>
    <product shop="3" supplier-reference="demo-1">
        <name>Name 2</name>
        <price>0</price>
    </product>
</advancedimporter>
```

Be careful, the default store for the product will always be the store defined in the feed. In our case this is Store 2. If we want to change this, the feed needs to read as follows: 
```
<advancedimporter>
    <product shop="3" supplier-reference="demo-1">
        <name>Name 2</name>
        <price>0</price>
    </product>
    <product shop="2" supplier-reference="demo-1">
        <name>Name 1</name>
        <price>0</price>
    </product>
</advancedimporter>
```

In all the previous examples, the product was not imported into Store 1. 

If you want to import a product into all your stores you do not need to define the store: 
```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

If you want to import a product into all stores but only customize one, you first need to create the product in all stores and then modify it in the desired store: 
```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
    <product shop="2" supplier-reference="demo-1">
        <name>Name 2</name>
        <price>0</price>
    </product>
</advancedimporter>
```

This will not work:
```
<advancedimporter>
    <product shop="2" supplier-reference="demo-1">
        <name>Name 2</name>
        <price>0</price>
    </product>
    <product supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
</advancedimporter>
```

Running a feed without defining the stores after importing the products into specific stores will have undesired effects. It is thus not recommended that the following two feeds are run in this order: 
```
<advancedimporter>
    <product supplier-reference="demo-1">
        <name>Name</name>
        <price>0</price>
    </product>
    <product shop="2" supplier-reference="demo-1">
        <name>Name 2</name>
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
