If the module does not work correctly, please check the following scenarios

**The cron seems to work correctly but no block is created**

Please check the version of your PHP. The module requires at least the version PHP 5.3. Of course, more recent versions can also be used.

**Blocks are created but never executed**

This issue occurs when the file "lock" cannot be deleted. to correct this, delete the file module/advancedimporter/lock/1.lock and keep sure that everyone can edit in the file module/advancedimporter/lock.

**Blocks regarding products are processed although not to a term **

This case can occur when the execution of the blocks ends unexpectedly or when the error cannot be interpreted by the module. In this case, go to the first example of the flow product ([product-1.xml](http://prestashopxmlimporter.madef.fr/flows_en/product-1.xml)). Please replace the language by the one used by default by your shop.

**Big block**

Blocks are stored in database. Sometime the data can be truncated. In the case you need to change the schema of the table ALTER ps_advancedimporter_block:

```
ALTER TABLE `ps_advancedimporter_block`
MODIFY COLUMN `block` LONGTEXT;
```
