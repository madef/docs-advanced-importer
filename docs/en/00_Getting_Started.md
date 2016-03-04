## 1. Installation

To install the module, it is necessary to use the PrestaShop interface created for this purpose: In the back office under the tab "module", click on “Add a new module”.

A form appears:


![image alt text](image_0.png)

Choose the zip archive of the module then click on the button: "Change the module"

A message will inform you that the module is downloaded. 

To search the modules, search "importer" then click on the button “install”.

![image alt text](image_1.png)

In the menu, a new entry will appear: 

![image alt text](image_2.png)

The module is now installed. We just need to activate it now.

**The activation can only be done from your processing environment.**

If you have a preprocessing  environment, you can access from an external environment, contact us with the PrestaShop Addons form.

The module will works in a degraded mode from a local environment. This mode is sufficient to carry out tests but recurring tasks cannot be done. 

To activate the module go to "Configuration" in the menu. Fill in the field “Order Reference” with the order number and active the api “smart cron”.

![image alt text](image_3.png)

## 2. Import a flow

We will use the following flow:

```
<products>
    <product external-reference="demo-1">
        <name>Name</name>
        <description>Product description</description>
        <price>20</price>
    </product>
</products>
```

The importation from the back office will be done via the tab PrestaShop XML Importer > Upload

![image alt text](image_4.png)

Copy the flow on a file edited with an editor like notepad and upload it via the form.

![image alt text](image_5.png)

If you have not activated the module (in case you have done tests on a local machine for instance), it is necessary to simulate the normal operating mode.

To do this, type the url here under in your web browser: [http://localhost/prestashop/modules/advancedimporter/cron.php?debug](http://localhost/prestashop/modules/advancedimporter/cron.php?debug)

"localhost" and “prestashop” of the url are to be adapted to your configuration. [http://localhost/prestashop/](http://localhost/prestashop/) is the url of your shop’s home page. 

The flow now figures in the list under the tab PrestaShop XML Importer > Flow.

In PrestaShop XML Importer > Blocks, two new lines appear:

![image alt text](image_6.png)

The block #2 is now pending execution (result = 0). It will be executed automatically if you have activated the module. 

Otherwise, it will be necessary to execute it manually. To do so, choose (in the combobox on the right) the option "Execute the block" (icon play) :

![image alt text](image_7.png)

The product is now imported.