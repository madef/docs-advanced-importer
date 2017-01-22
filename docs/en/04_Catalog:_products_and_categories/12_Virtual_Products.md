To create an vitual products, you have to set it's is_virtual and add a block "productdownload":

```
<?xml version="1.0" encoding="utf-8"?>
<products>
    <product external-reference="virtualproduct-1">
        <is_virtual>1</is_virtual>
        <name>test</name>
        <price>10</price>
        <block>
            <productdownloads>
                <productdownload external-reference="virtualproduct-1">
	              <external_reference for="id_product" type="product">virtualproduct-1</external_reference>
                <display_filename>Name of the file</display_filename>
                <nb_days_accessible>0</nb_days_accessible>
                <path>http://prestashopxmlimporter.madef.fr/app.png</path>
            </productdownload>
            </productdownloads>
        </block>
    </product>
</products>
```
