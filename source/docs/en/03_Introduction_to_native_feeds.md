This chapter will focus on the format specific to the module. To integrate a feed from a supplier in another format, refer to the section [Importing a feed]](!en/Importing_a_feed).

## Structure

The root tag is always **advancedimporter**.

The second-level tag is the name of the entity PHP class: product, category, order, customer, etc.

Third-level tags are attributes. For example, we can create a product named **test** using this feed:
```
<advancedimporter>
    <product>
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

And also a category named **test**:
```
<advancedimporter>
    <category>
        <name>test</name>
    </category>
</advancedimporter>
```

Both can be created using the same feed:
```
<advancedimporter>
    <product>
        <name>test</name>
        <price>10</price>
    </product>
    <category>
        <name>test</name>
    </category>
</advancedimporter>
```

## Nesting
Entities are sometimes linked to each other. For example, to integrate a category and its sub-category: 

```
<advancedimporter>
    <category>
        <name>category</name>
        <category>
            <name>sub-category</name>
        </category>
    </category>
</advancedimporter>
```

Or products are linked to a sub-category:
```
<advancedimporter>
    <product>
        <name>test</name>
        <price>10</price>
        <category>
            <name>category</name>
            <category>
                <name>sub-category</name>
            </category>
        </category>
    </product>
</advancedimporter>
```

## Supplier references 

If you’ve already executed the feeds several times, you’ll have noticed that the entities have been duplicated. 

To avoid this, the entities need to be identified by their supplier reference:

### Statement
Here is an example of a product statement with a supplier reference: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Note that the supplier reference is specific to the entity type. You can thus use the “test” supplier reference for a product and a category:
```
<advancedimporter>
    <category supplier-reference="test">
        <name>test</name>
    </category>
</advancedimporter>
```

### Reusing

It can sometimes be helpful to be able to link products to each other to use the supplier reference. 
To do this, add the attribute “supplier-reference” with the entity type as a value: 
```
<advancedimporter>
    <category supplier-reference="category2">
        <name>test</name>
        <id_parent supplier-reference="category">category1</id_parent>
    </category>
</advancedimporter>
```

## Identifier

If you wish to modify existing entities, you can define an identifier different from that of the supplier reference (e.g.: reference, EAN code, etc.).
Here is an example of how to modify a product using its reference:
```
<advancedimporter>
    <product supplier-reference="reference-value" identifier="reference">
        <reference>reference-value</reference>
        <name>test</name>
    </product>
</advancedimporter>
```

If the supplier reference is optional, it is still recommended that this is defined to enable the module to register it. This will also make future modifications faster. 

If it’s a tag inside an entity, it can be used by defining the target entity type as follows:
```
<advancedimporter>
    <tag supplier-reference="test">
        <name>test</name>
        <id_lang identifier="iso_code" type="language">en</id_lang>
    </tag>
</advancedimporter>
```

## Deleting

Elements are deleted through the “delete” node:

```
<advancedimporter>
    <delete supplier-reference="test" type="product"/>
</advancedimporter>
```

## Disabling

Entities can be disabled in the same as they can be deleted: 

```
<advancedimporter>
    <disable supplier-reference="test" type="product"/>
</advancedimporter>
```

## Deleting missing entities

By default, the absence of an entity from a feed doesn’t necessarily mean it will be deleted. To delete it, add the “delete-missing” attribute to the root tag. This attribute must have the supplier name as a parameter. Only the entities imported with the module and with a supplier reference can be automatically deleted. 

First feed, creating “test 1” and “test 2”:
```
<advancedimporter delete-missing="supplier">
    <product supplier-reference="test1">
        <name>test 1</name>
        <price>10</price>
    </product>
    <product supplier-reference="test2">
        <name>test 2</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Second feed, deleting "test 2”:
```
<advancedimporter delete-missing="supplier">
    <product supplier-reference="test1">
        <name>test 1</name>
        <price>10</price>
    </product>
</advancedimporter>
```
Be careful when using delete-missing, as the integrated feed needs to be complete otherwise products will be definitively deleted.

## Disabling missing entities

The delete-missing attribute is quite a definitive command, so you may prefer to disable the missing entities instead. In this case, you simply need to use the “disable-missing” attribute. Be careful, as delete-missing and disable-missing are incompatible with each other.  
```
<advancedimporter disable-missing="supplier">
    <product supplier-reference="test1">
        <name>test 1</name>
        <price>10</price>
    </product>
    <product supplier-reference="test2">
        <name>test 2</name>
        <price>10</price>
    </product>
</advancedimporter>
```

Second feed, deleting “test 2”:
```
<advancedimporter disable-missing="supplier">
    <product supplier-reference="test1">
        <name>test 1</name>
        <price>10</price>
    </product>
</advancedimporter>
```
