Nativement, le module attend des flux produits avec des déclinaisons groupées. Par exemple ce flux :

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<items>
    <item>
        <reference>demo-1</reference>
        <name>Name</name>
        <price>13</price>
        <combination>
            <reference-combination>demo-1</reference-combination>
            <color>red</color>
        <combination>
        <combination>
            <reference-combination>demo-2</reference-combination>
            <color>blue</color>
        <combination>
        <combination>
            <reference-combination>demo-3</reference-combination>
            <color>yellow</color>
        <combination>
    </item>
</items>
```

Ce format est en fait assez rare. On retrouve plus fréquemment deux autres formats :
* flux de déclinaisons
* flux de produits et sous-produits (dans ce cas, le sous-produit est la déclinaison)


## Flux de déclinaisons

Dans le cas d'un flux de déclinaisons, il est conseillé de grouper ces derniers par référence. Il est important de retrouver la référence du produit, ainsi que celle de la déclinaison :

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<items>
    <item>
        <reference>demo-1</reference>
        <reference-combination>demo-1</reference-combination>
        <name>Name</name>
        <price>13</price>
        <color>red</color>
    </item>
    <item>
        <reference>demo-1</reference>
        <reference-combination>demo-2</reference-combination>
        <name>Name</name>
        <price>13</price>
        <color>blue</color>
    </item>
    <item>
        <reference>demo-1</reference>
        <reference-combination>demo-3</reference-combination>
        <name>Name</name>
        <price>13</price>
        <color>yellow</color>
    </item>
</items>
```

Dans ce cas, la XSLT ressemblera à :

```
<?xml version="1.0" encoding="utf-8"?>
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
      <name>
        <xsl:value-of select="./name"/>
      </name>
      <price>
        <xsl:value-of select="./price"/>
      </price>
      <xsl:for-each select="key('groups', reference)">
        <combination external-reference="{./reference-combination}">
          <color>
            <xsl:value-of select="./color"/>
          </color>
        </combination>
      </xsl:for-each>
    </product>
  </xsl:template>
  <xsl:template match="item[not(generate-id()=generate-id(key('groups', reference)[1]))]"/>
</xsl:stylesheet>
```

Le résultat sera le suivant :

```
<?xml version="1.0" encoding="utf-8"?>
<products>
  <product external-reference="demo-1">
    <reference>demo-1</reference>
    <name>Name</name>
    <price>13</price>
    <combination external-reference="demo-1">
      <color>red</color>
    </combination>
    <combination external-reference="demo-2">
      <color>blue</color>
    </combination>
    <combination external-reference="demo-3">
      <color>yellow</color>
    </combination>
  </product>
</products>
```
