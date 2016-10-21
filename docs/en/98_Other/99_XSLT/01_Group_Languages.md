If your flow has one entry of product per language like this:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<items>
    <item>
        <lang>fr</lang>
        <reference>demo-1</reference>
        <name>Name FR</name>
        <price>13</price>
    </item>
    <item>
        <lang>en</lang>
        <reference>demo-1</reference>
        <name>Name FR</name>
        <price>13</price>
    </item>
    <item>
        <lang>fr</lang>
        <reference>demo-2</reference>
        <name>Name FR</name>
        <price>15</price>
    </item>
    <item>
        <lang>en</lang>
        <reference>demo-2</reference>
        <name>Name FR</name>
        <price>15</price>
    </item>
</items>
```

It's possible to group the entries of the same "reference" using XSLT:

```<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE xsl:stylesheet [
<!ENTITY nbsp " ">
<!ENTITY copy "©">
<!ENTITY reg "®">
<!ENTITY trade "™">
<!ENTITY mdash "—">
<!ENTITY ldquo "“">
<!ENTITY rdquo "”">
<!ENTITY pound "£">
<!ENTITY yen "¥">
<!ENTITY euro "€">
]>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output method="xml" encoding="utf-8" indent="yes"/>
  <xsl:variable name="cdataStart"><![CDATA[ <![CDATA ]]></xsl:variable>
  <xsl:variable name="cdataEnd"><![CDATA[ ]] ]]></xsl:variable>
  <xsl:key name="groups" match="item" use="reference"/>
  <xsl:template match="/items">
    <products>
      <xsl:apply-templates/>
    </products>
  </xsl:template>
  <xsl:template match="item[generate-id()=generate-id(key('groups', reference)[1])]">
    <product external-reference="{./reference}">
      <reference>
        <xsl:value-of select="./reference"/>
      </reference>
      <price>
        <xsl:value-of select="./price"/>
      </price>
      <xsl:for-each select="key('groups', reference)">
        <name lang="{./lang}">
          <xsl:value-of select="./name"/>
        </name>
      </xsl:for-each>
    </product>
  </xsl:template>
  <xsl:template match="item[not(generate-id()=generate-id(key('groups', reference)[1]))]"/>
</xsl:stylesheet>
```

The result will be this XML:

```
<?xml version="1.0" encoding="utf-8"?>
<products>
  <product external-reference="demo-1">
    <reference>demo-1</reference>
    <price>13</price>
    <name lang="fr">Name FR</name>
    <name lang="en">Name FR</name>
  </product>
  <product external-reference="demo-2">
    <reference>demo-2</reference>
    <price>15</price>
    <name lang="fr">Name FR</name>
    <name lang="en">Name FR</name>
  </product>
</products>
```
