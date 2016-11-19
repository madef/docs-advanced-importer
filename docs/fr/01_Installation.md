## Installation

L'installation du module s'effectue de manière standard :
- via l'interface addons
- depuis le panel d'administration

L'installation par FTP est possible, mais n'est pas recommendée à cause de problème de droits qui peuvent se produire.

Nous ne détaillerons pas l'installation depuis addons.

Pour installer le module à partir de l'archive. Rendez-vous dans l'onglet « module » depuis le panel d'administration.

Cliquez sur le bouton « ajouter » (bouton « + »). Un formulaire devrait apparaitre :

![image alt text](media/image_0.png)

Choisissez l’archive zip du module puis cliquez sur le bouton « Charger le module ».

Un message vous informe que le module est téléchargé.

Dans la recherche des modules recherchez « importer » puis cliquez sur le bouton « installer ».

![image alt text](media/image_1.png)

Dans le menu une nouvelle entrée fait son apparition :

![image alt text](media/image_2.png)

Le module est maintenant installé. Il nous reste plus qu’à l’activer.

## Activer le Smart Cron

Le smart cron simule le cron unix, ce dernier permet d'exécuter des tâches toutes les minutes.

**L’activation ne peut être faite que depuis votre environnement de production.**

Si vous avez un environnement de préproduction accessible depuis l’extérieur contactez-nous via [le formulaire de PrestaShop Addons](https://addons.prestashop.com/fr/contactez-nous?id_product=7951).

Depuis un environnement local, le module fonctionnera en mode dégradé. Ce mode est suffisant pour faire des tests mais ne permet pas d’effectuer des tâches récurrentes.

Pour activer le module aller dans "Configuration" du menu plus haut. Renseigner le champ « Référence de commande » avec le numéro de votre commande et activez l’api « smart cron ».

![image alt text](media/image_3.png)

## Tester le bon fonctionnement du module

Téléchargez le flux [suivant](!flow/check-install.xml)

L’importation du backoffice se fait via l’onglet « PrestaShop XML Importer » > « Téléchargement »

![image alt text](media/image_4.png)

Téléchargez le flux via le formulaire :

![image alt text](media/image_5.png)

Après quelques minutes un nouveau produit devrait être présent.

Si vous n'avez pas activé le smartcron, alors il faudra entrer dans un nouvel onglet du navigateur l’url suivante : [http://localhost/prestashop/modules/advancedimporter/cron.php?debug](http://localhost/prestashop/modules/advancedimporter/cron.php?debug)

"localhost" et “prestashop” de l’url sont à adapter en fonction de votre configuration. [http://localhost/prestashop/](http://localhost/prestashop/) étant l’url de la page d’accueil de votre boutique.

Si le produit n'est pas créé, contatez [notre support](https://addons.prestashop.com/fr/contactez-nous?id_product=7951).
