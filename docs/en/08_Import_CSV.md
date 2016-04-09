he importation of the flows CSV is carried out the same way as the flow xml. The CSV flow needs to be converted to a XML flow to be uploaded. To do this, it is necessary to add a a template in the tab "Template CSV" of the addon.

Let’s take for instance the following flow:

```
Reference Externe,Reference,Nom,Description,Categorie parente,Sous catégorie,Prix,Stock,Ean13,Image
ref-1,ref-1,"Product 1","Description 1","Music player","Ipod",150, 12,8412457989784,http://prestashopxmlimporter.madef.fr/img/demo.jpg
ref-2,ref-2,"Product 2","Description 2","Music player","Accessories",20, 5,8412457989785,http://prestashopxmlimporter.madef.fr/img/demo.jpg
```


In  PrestaShop XML Importer > Template CSV, create a new template.

Fill out the "root tag" used ti build the XML. The root tag is "products" for products flows, "objects" for objects flow.

If you want to use the assistant, choose the type of flow (products, subject, ...). Otherwise, opt for the advanced mode.

Le mode avancé permet de réaliser des flux plus complèxes.
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
