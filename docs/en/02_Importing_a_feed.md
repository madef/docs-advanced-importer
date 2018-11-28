Before importing a feed, remember to correctly [configure the module](!en/Installation).

Depending on the feed format to be imported, additional steps may be required. For example, if the feed is an Excel document, it will first need to be converted to CSV format.  

| Feed format   | Native XML | XML | CSV | Excel |
|------------------|-----------|-----|-----|-------|
| Convert to CSV | No       | No | No | Yes   |
| Create a model| No       | Yes | Yes | Yes   |


Generally, the first step is to create a model. If your feed is a CSV, or an XML from a service provider, you will need to create a model.

The model will allow an XML or CSV to be converted to an XML that can be processed by the module (the native format).

If the feed is a product feed, the model creation wizard can be used. This allows models to be created through a graphic interface with no knowledge of XML and XSLT required.

## Creating a model using the wizard

Click on the "template" entry in the module menu. Open the wizard interface by clicking on the "?" on top right.
The first step invites you to import the flow. If possible, choose a feed that contains as little data as possible. The smaller the file, the faster the wizard will run. 

It will then ask you to name the model. If your file is an XML, you will then be asked to identify the root of each product. 

Several further steps will then follow. Each step will ask you to define which node )for an XML) or which column (for a CSV) corresponds to the requested information:
- Product identifier
- Product name and description
- Price and taxes
- Categories
- Images
- Stock and status
- Specifications
- Supplier and manufacturer

## Creating a model

To create a model without using the wizard, access the “Model” tab and click the “Add” button. 

## Creating a PHP class for a model

If your feed refers to an external API, if the feed is in a flat or proprietary format, or if your feed refers to other PrestaShop entities without using identifiers that can be used by the module, you will need to define a PHP class. You can find more information on the [dedicated extractors page](!en/Going_Further/Extractors).

## Importing a feed manually

Start by clicking on the “Add” button in the “Feed” section of the “Advanced Importer” submenu. First, choose the feed to be imported. Then choose the model to apply. If the feed is in the native format, choose the “None” option. After this, access the “Feed” section in the “Advanced Importer” submenu to monitor the progress of the feed integration. 

## Importing a feed automatically

### Via FTP

To repeatedly download a feed from an FTP, visit the “Recurring tasks” section in the “Advanced Importer” submenu. 
Click on the “Add an FTP download” button. 
In the form that appears, begin by selecting the recurrence (cron time). Then, fill in the details required to connect to the FTP (user name, password, host, port) and the path to the file or folder. If the path is a folder, all the files in the folder will be downloaded. 

### Via HTTP


To repeatedly download a feed from a URL, visit the “Recurring tasks” section in the “Advanced Importer” submenu. 
Click on the “Add an HTTP download” button. 
In the form that appears, begin by choosing the recurrence (cron time). Then, enter the URL of the file and the desired name for the downloaded file. If the field is left blank, the file will not be renamed.
