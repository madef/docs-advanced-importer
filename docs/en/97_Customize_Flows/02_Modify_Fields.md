In some cases the format of your data cannot match with format required by the module. In this case you can use "modifier"

With modifiers, you can for example:
 * remove spaces from the beginning and end of a string
 * increase the price of N%
 * replace some part of a string
 
## Examples

### Increase a price

To increase the price of 20% you will proceed like this:
```
<products>
    <product external-reference="demo-1">
        <name>Name</name>
        <description>Product description</description>
        <price modifier="Helper_Number::addPercentage(20)">50</price>
    </product>
</products>
```

Note: You can also calculate the percentage (N% of the prixe) with "percentage", or the complement of the percentage (100-N% of the price) with "percentageComplement".

You may also want to increase the price of 2$:
```
<products>
    <product external-reference="demo-1">
        <name>Name</name>
        <description>Product description</description>
        <price modifier="Helper_Number::add(2)">50</price>
    </product>
</products>
```

Note: You can also "sub", "multiply", or "divide".

### Arithmetic operations

The modifier allow to make more complex arithmetic operations:
```
<products>
    <product external-reference="demo-1">
        <name>Name</name>
        <description>Product description</description>
        <price modifier="Helper_Number::calculate">2 * (50 + 5)</price>
    </product>
</products>
```

There are other aritmetic operations like :
  * negative valies: neg
  * absolute values: abs
  * rest of divide operation: modulo

### Remove spaces from the beginning and end of a string

```
<products>
    <product external-reference="demo-1">
        <name>Name</name>
        <description modifier="trim">Product description</description>
        <price>50</price>
    </product>
</products>
```

It's also possible to remove other chars. For example slashes:

```
<products>
    <product external-reference="demo-1">
        <name>Name</name>
        <description modifier="trim(/)">Product description</description>
        <price>50</price>
    </product>
</products>
```
Note: trim is the native function of PHP. You can use all native PHP function.

### Replace strings

You can modify the string with regular expression.
For exemple you want to replace the words "love" by "♥" you will proceed like that:
```
<products>
    <product external-reference="demo-1">
        <name>Name</name>
        <description modifier="Helper_String::replace(love,♥)">Product description</description>
        <price>50</price>
    </product>
</products>
```

## Parameters

Be careful, the parameters cannot be surrounded by spaces. This example will not works:
```
<products>
    <product external-reference="demo-1">
        <name>Name</name>
        <description modifier="Helper_String::replace(love ,♥)">Product description</description>
        <price>50</price>
    </product>
</products>
```

## Create your own

In some cases the modifiers cannot fit your needs. In this case you will have to make your own helper class.

This helper class must be created in the directory modules/advancedimporter/classes/helper.

Do not modify existing helpers because your modifications will be erased when the module will be upgraded.

The helper class are PHP class with statics methods that follow the name convention: "Helper_<YourHelperNameInCamelCase>". The file name must be in lower case : <yourhelpernameinlowercase>.php.
