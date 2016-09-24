Speed of the imports can be improved by changing several parameters.

## The logs

Writing the logs in the database takes time. To improve the speed of these, it is recommended to disable all logs except those errors.
Disabling the logs is done in the "configuration" of the module.

## The cron

By default, the smart cron is enable. It is easy to use but not necessarily the most optimized.
To improve import speed it is recommended to use the UNIX cron. You will have also to configure your php.ini in cli mode to remove or increase the limits in memory and time.

Here is an example of crontab:
```
* * * * * cd /var/www/modules/advancedimporter && php plan.php >> /var/log/apache2/advancedimporter.cron.log 2>> /var/log/apache2/advancedimporter.cron.log
* * * * * cd /var/www/modules/advancedimporter && php cron.php 500 >> /var/log/apache2/advancedimporter.cron.log 2>> /var/log/apache2/advancedimporter.cron.log
```


## The images

Download images can be slow.
The images are downloaded even if they already exist. If you do not need this behavior, you must add the attribute "update":
```
<products>
	<product external-reference="product-demo-1" >
		<name lang="fr">Nom</name>
		<description lang="en">Description of the product</description>
		<images update="0">
			<url>/modules/advancedimporter/img/media/01.jpg</url> <!-- from local storage -->
			<url>http://prestashopxmlimporter.madef.fr/img/demo.jpg</url> <!-- from a server -->
		</images>
	</product>
</products>
```
