According to Wikipedia, XSLT (eXtensible Stylesheet Language Transformations), defined within the XSL recommendations of the W3C, is a functional language for transforming XML. It allows an XML document to be transformed into another format such as a PDF or even HTML to be displayed as a webpage.  

PrestaShop Advanced Importer used XSLTs to convert XMLs into the format’s native module. Whether or not you choose to use the model wizard, the model created will be an XSLT.  

For CSVs, the module first converts the CSV to basic XML to then be able to apply an XSLT. Whether or not the file is an XML to begin with, you can still benefit from the power offered by the XSLT transformation engine. 

The basic XML produced by converting a CSV looks as follows: 

```
<csv>
    <line>
        <A>content of column A row A</A>
        <B>content of column B row B</B>
        <C>content of column C row C</C>
    </line>
    <line>
        <A>content of column A row A</A>
        <B>content of column B row B</B>
        <C>content of column C row C</C>
    </line>
</csv>
```
