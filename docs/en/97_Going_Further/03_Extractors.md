The role of the extractor is to convert the feed into an XML feed to which the module may or may not apply an XSLT.

Two extractors exist by default:
- XML
- CSV

The XML extractor is very basic, it reads the XML file using the SimpleXML library:

```
class AIXmlExtractor implements AIExtractorInterface
{
    public static function getName()
    {
        return 'XML';
    }

    public function extract($file, $template)
    {
        return new SimpleXmlElement(file_get_contents($file));
    }
}

```

The CSV extractor is more complex, transforming CSV columns into XML. The output format looks as follows: 

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

The extractor must be selected when creating a new model (“model” tab in the module, then the “Add” button).

## Creating your own extractor

If your feed is a little complex, it may be more useful for you to create your own extractor. 

This is particularly true if you need to use an external API, if the feed format is a proprietary or flat format, or if your feed references other PrestaShop entities without using an identifier that can be used by the module.

An extractor is created by creating a PHP class. Take care to follow naming conventions. 

The class should be named  AI<your extractor with the first letter in upper case >Extractor. E.g.: AiCustomExtractor

The file must be located in the folder modules/advancedimporter/classes/extractor

The file name must be the name of your extractor in lower case. E.g.: custom.php

The class must implement AIExtractorInterface and the methods **getName** and **extract** must be defined.

Here is an example of an extractor that increases the price by 20%:

```
class AICustomExtractor implements AIExtractorInterface
{
    public static function getName()
    {
        return 'Custom';
    }

    public function extract($file, $template)
    {
        $xml = new SimpleXmlElement(file_get_contents($file));
        foreach ($xml->product as $product) {
            $product->price = ((float) $product->price) * 1.2;
        }
        return $xml;
    }
}

```

To apply this extractor, you will need to create a new model and select the **Custom** extractor.
After doing this you need to import your feed by selecting the new template. 




