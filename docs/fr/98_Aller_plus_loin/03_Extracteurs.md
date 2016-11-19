Le rôle de l'extracteur est de convertir le flux en flux XML auquel le module appliquera (ou non) une XSLT.

Par  défaut deux extracteurs existent :
- XML
- CSV

L'extracteur XML est très basique, il lit le fichier XML au moyen de la bibliothèque SimpleXML :

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

L'extracteur CSV est plus complèxe, il transforme les colonnes du CSV en XML. Lle format de sortie resemble à cela :

```
<csv>
    <line>
        <A>contenu de la colonne A ligne A</A>
        <B>contenu de la colonne B ligne B</B>
        <C>contenu de la colonne C ligne C</C>
    </line>
    <line>
        <A>contenu de la colonne A ligne A</A>
        <B>contenu de la colonne B ligne B</B>
        <C>contenu de la colonne C ligne C</C>
    </line>
</csv>
```

L'extracteur doit être sélectionné lors de la création d'un nouveau modèle (onglet "modèle" du module, puis bouton "ajouter").

## Créer votre propre extracteur

Si votre flux est un peu complèxe, il peut être utile de créer votre propre extracteur.

Cela est particulièrement vrai, si vous avez besoin de faire appel à une API externe, si le format du flux est une format propriétaire ou plat, ou encore si votre flux fait référence à d'autres entitées PrestaShop sans utiliser un identifiant utilisable par le module.

La création d'un extracter consiste en la création d'une classe PHP. Attention, il faut respecter les convention de nommage.

La classe doit se nommer AI<votre exporter avec la première lettre en majuscule>Extractor. Exemple : AiCustomExtractor

Le fichier doit être placé dans le dossier modules/advancedimporter/classes/extractor

Le nom du fichier doit être le nom de votre exporteur en minuscule. Exemple : custom.php

La classe doit implémenter AIExtractorInterface et les méthodes **getName** et **extract** doivent être définies.

Voici un exemple d'extracteur qui augmente le prix de 20% :

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

Pour appliquer cet extractor, il faut créer un nouveau template est sélectionner l'extractor **Custom**.
Après cela il faudra importer votre flux en sélectiononnant le nouveau template.



