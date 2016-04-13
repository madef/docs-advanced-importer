The importation of CSV flows is carried out the same way as the flow xml. The CSV flow needs to be converted to a XML flow to be uploaded. To do this, it is necessary to add a a template in the tab "Template CSV" of the addon.

Let’s take for instance the following flow:
```
Reference Externe,Reference,Nom,Description,Categorie parente,Sous catégorie,Prix,Stock,Ean13,Image
ref-1,ref-1,"Product 1","Description 1","Music player","Ipod",150, 12,8412457989784,http://prestashopxmlimporter.madef.fr/img/demo.jpg
ref-2,ref-2,"Product 2","Description 2","Music player","Accessories",20, 5,8412457989785,http://prestashopxmlimporter.madef.fr/img/demo.jpg
```


In  PrestaShop XML Importer > Template CSV, create a new template.

Fill out the "root tag" used ti build the XML. The root tag is "products" for products flows, "objects" for objects flow.

If you want to use the assistant, choose the type of the flow (products, object, ...). Otherwise, opt for the advanced mode.

Advanced mode allows more complex flows.

Here is a sample template:

```
<product external-reference="{{0}}">
    <reference><![CDATA[{{1}}]]></reference>
    <name lang="fr"><![CDATA[{{2}}]]></name>
    <description lang="fr"><![CDATA[{{3}}]]></description>
    <categorypath><![CDATA[{{4}}]]>&gt;<![CDATA[{{5}}]]></categorypath>
    <price>{{6}}</price>
    <block>
        <stocks>
            <stock>
                <product>{{id}}</product>
                <mode>set</mode>
                <quantity>{{7}}</quantity>
            </stock>
        </stocks>
    </block>
    <ean13>{{8}}</ean13>
    <images>
        <url>{{9}}</url>
    </images>
</product>
```
### Import combination

In order to import combination, you can use one line per combination.

Be careful, each line must includ the data of the product.

Here is an example of a CSV with multiple combination:
```
"ref product","ref combination","name"," color","size","price","quantity"," categories"," categories"," image1"," image 2"
"demo-1","demo-1-1","Product 1","blue","US","9.99",40,"Women > T-shirt","Outlet  > T-shirt","http://prestashopxmlimporter.madef.fr/app.png","http://prestashopxmlimporter.madef.fr/en/image_0.png"
"demo-1","demo-1-2","Product 1","red","US","10.99",40,"Women > T-shirt","Outlet  > T-shirt","http://prestashopxmlimporter.madef.fr/app.png","http://prestashopxmlimporter.madef.fr/en/image_0.png"
"demo-1","demo-1-3","Product 1","orange","US","11.99",40,"Women > T-shirt","Outlet  > T-shirt","http://prestashopxmlimporter.madef.fr/app.png","http://prestashopxmlimporter.madef.fr/en/image_0.png"
"demo-2","demo-2-1","Product 2","green",41,"9.99",40,"Women > T-shirt","Outlet  > T-shirt","http://prestashopxmlimporter.madef.fr/app.png","http://prestashopxmlimporter.madef.fr/en/image_0.png"
"demo-2","demo-2-2","Product 2","green",42,"9.99",40,"Women > T-shirt","Outlet  > T-shirt","http://prestashopxmlimporter.madef.fr/app.png","http://prestashopxmlimporter.madef.fr/en/image_0.png"
"demo-2","demo-2-3","Product 2","green",43,"9.99",40,"Women > T-shirt","Outlet  > T-shirt","http://prestashopxmlimporter.madef.fr/app.png","http://prestashopxmlimporter.madef.fr/en/image_0.png"
```

The template to convert the CSV in XML must look like this:

```
<product external-reference="{{0}}">
    <reference>{{0}}</reference>
    <name>{{2}}</name>
    <images>
        <csv_if_not_null column="9"><url>{{9}}</url></csv_if_not_null>
        <csv_if_not_null column="10"><url>{{10}}</url></csv_if_not_null>
    </images>
    <csv_if_not_null column="7"><categorypath separator="&gt;">{{7}}</categorypath></csv_if_not_null>
    <csv_if_not_null column="8"><categorypath separator="&gt;">{{8}}</categorypath></csv_if_not_null>
    <block>
        <objects>
            <object type="attributeGroup" external-reference="demo-color" update="0">
                <is_color_group>1</is_color_group>
                <group_type>color</group_type>
                <name>Color</name>
                <public_name>Color</public_name>
            </object>
            <object type="attribute" external-reference="demo-color-{{3}}" update="0">
                <external_reference for="id_attribute_group" type="attributeGroup">demo-color</external_reference>
                <name>{{3}}</name>
            </object>
            <object type="attributeGroup" external-reference="demo-size" update="0">
                <is_color_group>0</is_color_group>
                <group_type>select</group_type>
                <name>Size</name>
                <public_name>Size</public_name>
            </object>
            <object type="attribute" external-reference="demo-size-{{4}}" update="0">
                <external_reference for="id_attribute_group" type="attributeGroup">demo-size</external_reference>
                <name>{{4}}</name>
            </object>
        </objects>
        <products>
            <product external-reference="{{0}}">
                <combinations external-reference="{{1}}">
                    <price>{{5}}</price>
                    <unit_price_impact>0</unit_price_impact>
                    <images>1</images>
                    <attributes use-external-reference="1">demo-color-{{3}}</attributes>
                    <attributes use-external-reference="1">demo-size-{{4}}</attributes>
                </combinations>
            </product>
        </products>
        <stocks>
            <stock>
                <product use-external-reference="1">{{0}}</product>
                <combination use-external-reference="1">{{1}}</combination>
                <mode>set</mode>
                <quantity>{{6}}</quantity>
	    </stock>
        </stocks>
    </block>
</product>
```
