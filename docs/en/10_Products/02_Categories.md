Categories are created using the “category” node or from a product using the “categorypath” node.

The categorypath node allows a path (category > sub-category > sub-sub-category) to be converted. It is simpler to use but less customizable than the category node. 

## “category” node

Here is an example of categories that will be the child of the “home” category:
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>category</name>
    </category>
</advancedimporter>
``` 

### Image

To download an image from a URL and attach it to a category, use the “image” node:
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>category</name>
        <image>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</image>
    </category>
</advancedimporter>
``` 

The image can also be retrieved locally:
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>category</name>
        <image>/modules/advancedimporter/views/img/media/01.jpg</image>
    </category>
</advancedimporter>
``` 



### Linking categories

Categories can be linked to each other through nesting: 
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>category</name>
        <category supplier-reference="category2">
            <name>sub-category</name>
        </category>
    </category>
</advancedimporter>
``` 

Categories can be linked to one another without using nesting:
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>category</name>
    </category>
    <category supplier-reference="category2">
        <name>sub-category</name>
        <id_parent supplier-reference="category">category1</id_parent>
    </category>
</advancedimporter>
```

### Linking categories and products

Nesting is used to link a category to a product:
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category1">
            <name>category</name>
        </category>
    </product>
</advancedimporter>
```

Be careful, nesting can be used for sub-categories, but the product will only be linked to the first category and not to the sub-categories. In this example, the product will only be linked to the category: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category1">
            <name>category</name>
            <category supplier-reference="category2">
                <name>sub-category</name>
            </category>
        </category>
    </product>
</advancedimporter>
```

To link a product to categories and sub-categories, avoiding category nesting:
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category1">
            <name>category</name>
        </category>
        <category supplier-reference="category2">
            <name>sub-category</name>
            <id_parent supplier-reference="category">category1</id_parent>
        </category>
    </product>
</advancedimporter>
```

If you want to link the product to single sub-categories, avoid stating the category in the product:
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>category</name>
    </category>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category2">
            <name>sub-category</name>
            <id_parent supplier-reference="category">category1</id_parent>
        </category>
    </product>
</advancedimporter>
```

The sub-category can also be stated twice:  
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>category</name>
        <category supplier-reference="category2">
            <name>sub-category</name>
        </category>
    </category>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category2" />
    </product>
</advancedimporter>
```

## “categorypath” node

Categorypath is simpler to use, but has less features. For example, it cannot be used to manage languages or supplier references, and can only be used from a product. 
First, you need to determine which separator has been used. This allows categories to be separated into sub-categories. For example, in “Women, Dresses, Summer” the separator is “,”.

This separator must be carefully chosen. For example, if there is a category named “T-Shirt, Long”, the comma will be processed as a separator. It is not possible to avoid symbols identical to the separator. 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <categorypath separator="&gt;"><![CDATA[ Women > Dresses > Summer ]]></categorypath>
    </product>
</advancedimporter>
```

## Deleting missing links between products and categories

Running these two feeds will attach the product to #category1 and #category2: 
```
<advancedimporter>
    <category supplier-reference="category1">
        <name>category 1</name>
    </category>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category1" />
    </product>
</advancedimporter>
```

```
<advancedimporter>
    <category supplier-reference="category2">
        <name>category 2</name>
    </category>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category2" />
    </product>
</advancedimporter>
```

If you only want to keep the links from the last feed, use the attribute “remove-missing-categories”: 
```
<advancedimporter>
    <category supplier-reference="category2">
        <name>category 2</name>
    </category>
    <product supplier-reference="test" remove-missing-categories="yes">
        <name>test</name>
        <price>10</price>
        <category supplier-reference="category2" />
    </product>
</advancedimporter>
```
