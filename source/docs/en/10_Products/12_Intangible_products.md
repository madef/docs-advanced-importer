Intangible or virtual products allow non-physical products such as concert seats, music seats, or even vouchers to be purchased. 

The product is defined as a virtual product using the “is_virtual” node: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <is_virtual>1</is_virtual>
    </product>
</advancedimporter>
```

To add a file, use the “productDownload” entity: 
```
<advancedimporter>
    <product supplier-reference="test">
        <name>test</name>
        <price>10</price>
        <is_virtual>1</is_virtual>
        <productDownload>
            <display_filename>Name_of_file.pdf</display_filename>
            <url>http://v2.prestashopxmlimporter.madef.fr/fr/numbers/number-1.jpg</url>
        </productDownload>
    </product>
</advancedimporter>
```

In addition to these attributes, the following nodes may also be added:
 * nb_days_accessible: Number of days the file will be available for download. Set to 0 for unlimited. 
 * nb_downloadable: Number of possible downloads. Set to 0 for unlimited.
 * date_expiration: Expiration date of the file
