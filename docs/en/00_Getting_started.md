Advanced XML & CSV Importer is an import module designed for large feeds. 
It can manage feeds of several hundred megabytes.

The module can import all PrestaShop entities (PHP classes from ObjectModel).

As the module name suggests, XML and CSV files can be imported, as well as flat files such as mqseries (currently in development).

Spreadsheet files (Excel, Libre Office, etc.) must be converted to CSV format before importing.

## Scheduled task

The primary role of the module is to schedule and execute tasks. For example, it can be scheduled to download an XML or CSV feed every night.  

The module imitates the functions of [Cron Unix](https://en.wikipedia.org/wiki/Cron).

## Basics for importing a feed

There are several steps to follow between downloading a feed before it is fully imported.

There are four main steps:
1. Downloading the feed file
2. Converting the feed file into a format that can be read by the module 
3. Reading the feed and saving it into multiple “**blocks**”
4. Converting the blocks into PrestaShop entities

The first two steps require some configuration. The final two are automated and require no configuration.

### Downloading the feed 

Downloading the feed is not covered in detail here, but you can find more information in the section [Importing a feed](!en/Importing_a_feed).

There are 3 ways to download a feed: 
- Manually, by using a dedicated form
- From a URL, using a scheduled task
- From an FTP server, using a scheduled task

### Converting feed files

By default, the module only processes XML files in a specific format. Throughout the documentation you will find only the native format described. Only the sections pertaining to converting XML or CSV present examples of non-native formats.

Files are converted as the feed is downloaded. This is done through a “**model**”. It allows CSV or XML files to be converted to the format required by the module using an **XSLT**. The model can be created using an assistant to avoid the need to write XSLT. This method is simpler, but doesn’t cover all the options possible with the module.  

## ETL

If you understand how ETL works, the module is strongly inspired by these processes. A model is in fact the “**extractor**”. Its purpose is to convert the feed into “**blocks**”. The **blocks** are **transformed** into a PrestaShop entity and **stored** in a database. 

## Documentation layout

Throughout this documentation it will be considered that you have created a model to convert your feeds to the native format. Only the [Importing a feed](!en/Importing_a_feed) section details how to import feeds in a non-native format. All of the feed examples are thus those supported by the module and require no special model. 

## Features:

The module can be used to:
- Create products in one specific store or several stores
- Save in multiple languages
- Import any type of PrestaShop entity (products, categories, clients, stock, images, orders, etc.)
- Create complex products (ranges, packs, etc.)
- Whether or not to update or partially update a product if it already exists
- Limit imports of updates
