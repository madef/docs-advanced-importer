Modifiers allow the values of a field to be modified using a PHP method. By default, there are several modifiers you can use to do the following and more:
 * Delete spaces at the beginning and end of strings
 * Increase the price by N%
 * Replace part of a string

## PHP function

You can execute any PHP function. For example, if you want to remove spaces at the beginning and end of strings. 

```
<advancedimporter>
    <product external-reference="demo-1">
        <name>Name</name>
        <description modifier="trim">Product description</description>
        <price>50</price>
    </product>
</advancedimporter>
```

If you want to delete characters other than spaces:
```
<advancedimporter>
    <product external-reference="demo-1">
        <name>Name</name>
        <description modifier="trim(/)">Product description</description>
        <price>50</price>
    </product>
</advancedimporter>
```

## Module method

### Mathematical operators

```
<advancedimporter>
    <product external-reference="demo-1">
        <name>Name</name>
        <description>Product description</description>
        <price modifier="HelperNumber::calculate">2 * (50 + 5)</price>
    </product>
</advancedimporter>
```

There are other modifiers:
  * negative value: neg
  * absolute value: abs
  * Euclidean division remainder: modulo

### Operating on strings

This modifier replaces the word "love" with "♥":
```
<advancedimporter>
    <product external-reference="demo-1">
        <name>Name</name>
        <description modifier="HelperString::replace(love,♥)">Product description</description>
        <price>50</price>
    </product>
</advancedimporter>
```

## Warning

Warning, parameters cannot be surrounded by spaces. The following example will not work:
```
<advancedimporter>
    <product external-reference="demo-1">
        <name>Name</name>
        <description modifier="HelperString::replace(love ,♥)">Product description</description>
        <price>50</price>
    </product>
</advancedimporter>
```

## Creating your own modifier

If you wish to create your own modifier, you will need to create a helper class in the folder modules/advancedimporter/classes/helper.

Do not modify the existing helpers: module updates will overwrite your modifications. 

The name of the helper class should be in camelcase and begin with Helper. The file name must be the name of the class without the Helper at the start. It must be in lower case. 
