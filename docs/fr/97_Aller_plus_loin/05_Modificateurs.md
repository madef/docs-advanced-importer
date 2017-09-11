Les modificateurs permettent de modifier les valeurs d'un champ avec une méthode PHP. Il existe par défaut plusieurs modificateurs avec lequels ovus pourez entre-autre :
 * supprimer les espaces de début et fin de chaîne
 * augmenter le prix de N%
 * remplacer une paties d'une chaîne

## Fonction PHP

Vous pouvez exécuter n'importe quelle fonction PHP. Par exemple si vous souhaitez retirer les espace de fin et début de chaîne :

```
<advancedimporter>
    <product external-reference="demo-1">
        <name>Name</name>
        <description modifier="trim">Product description</description>
        <price>50</price>
    </product>
</advancedimporter>
```

Si vous souhaitez supprimer un autres caractères que les espaces :
```
<advancedimporter>
    <product external-reference="demo-1">
        <name>Name</name>
        <description modifier="trim(/)">Product description</description>
        <price>50</price>
    </product>
</advancedimporter>
```

## Méthode du module

### Opérations arithmetiques

```
<advancedimporter>
    <product external-reference="demo-1">
        <name>Name</name>
        <description>Product description</description>
        <price modifier="HelperNumber::calculate">2 * (50 + 5)</price>
    </product>
</advancedimporter>
```

Il existe d'autres modificateurs :
  * valeurs négative : neg
  * valeurs absolue : abs
  * reste de la division euclidienne : modulo

### Opération sur les chaînes

Ce modificateur replace le mot "love" par un "♥" :
```
<advancedimporter>
    <product external-reference="demo-1">
        <name>Name</name>
        <description modifier="HelperString::replace(love,♥)">Product description</description>
        <price>50</price>
    </product>
</advancedimporter>
```

## Mise en garde

Attention, les paramètres ne peuvent pas être entourés d'espaces. Cet exemple ne fonctionne pas :
```
<advancedimporter>
    <product external-reference="demo-1">
        <name>Name</name>
        <description modifier="HelperString::replace(love ,♥)">Product description</description>
        <price>50</price>
    </product>
</advancedimporter>
```

## Créer votre propre modificateur

Si vous souhaitez créer votre propre modificateur, vous devez créer une classe helper dans le dossier modules/advancedimporter/classes/helper.

Ne modifiez pas les helpers existant ! Les mises à jour du module écraseront vos modifications.

Le nom de la classe de l'helper doit être en camelcase et débuter par Helper. Le nom du fichier doit être le nom de la classe sans le helper initial. Il doit être en minuscules.
