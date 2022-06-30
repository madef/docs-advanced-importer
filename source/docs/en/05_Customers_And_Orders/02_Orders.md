Importing orders can be do with the flow object.

Example of creating an order:

```
<objects>
	<object type="Customer">
		<findOne
			for="id"
			type="Customer"
			identifier="id"
		>
			<email>test@domain.tld</email>
		</findOne>
		<email>test@domain.tld</email>
		<passwd>*********</passwd> <!-- Il faut surcharge PrestaShop pour pouvoir créer des utilisateurs sans mot de passe -->
		<firstname>Test</firstname>
		<lastname>Test</lastname>
	</object>
	<object type="Product">
		<findOne
			for="id"
			type="Product"
			identifier="id"
		>
			<reference>test1</reference>
		</findOne>
		<name lang="fr">Test</name>
		<link_rewrite lang="fr">Test</link_rewrite>
		<price>12</price>
		<reference>test1</reference>
	</object>
	<object type="Address" external-reference="test@domain.tld-Test-Test-5 rue du puy-75001-Paris"><!-- Attention, les références externes sont lmimitées à 255 caractères -->
		<findOne
			for="id_customer"
			type="Customer"
			identifier="id"
		>
			<email>test@domain.tld</email>
		</findOne>
		<findOne
			for="id_country"
			type="Country"
			identifier="id"
		>
			<iso_code>fr</iso_code>
		</findOne>
		<firstname>Test</firstname>
		<lastname>Test</lastname>
		<address1>5 rue du puy</address1>
		<address2></address2>
		<postcode>75001</postcode>
		<city>Paris</city>
		<alias>5 rue du puy, 75001 Paris</alias>
	</object>
	<object type="Address" external-reference="test@domain.tld-Test un-Test-5 rue du puy-75001-Paris"><!-- Attention, les références externes sont lmimitées à 255 caractères -->
		<findOne
			for="id_customer"
			type="Customer"
			identifier="id"
		>
			<email>test@domain.tld</email>
		</findOne>
		<findOne
			for="id_country"
			type="Country"
			identifier="id"
		>
			<iso_code>fr</iso_code>
		</findOne>
		<firstname>Test un</firstname>
		<lastname>Test</lastname>
		<address1>5 rue du puy</address1>
		<address2></address2>
		<postcode>75001</postcode>
		<city>Paris</city>
		<alias>5 rue du puy, 75001 Paris</alias>
	</object>
	<object type="Order" external-reference="demo-3">
		<!--<id_address_delivery>1</id_address_delivery>
		<id_address_invoice>1</id_address_invoice>-->
		<external_reference for="id_address_delivery" type="Address">test@domain.tld-Test un-Test-5 rue du puy-75001-Paris</external_reference>
		<external_reference for="id_address_invoice" type="Address">test@domain.tld-Test-Test-5 rue du puy-75001-Paris</external_reference>
		<id_cart>1</id_cart>
		<id_currency>1</id_currency>
		<id_lang>1</id_lang>
		<findOne
			for="id_customer"
			type="Customer"
			identifier="id"
		>
			<email>test@domain.tld</email>
		</findOne>
		<id_carrier>1</id_carrier>
		<payment>1</payment>
		<module>cheque</module>
		<total_paid>2.5</total_paid>
		<total_paid_real>3.5</total_paid_real>
		<total_products>13.5</total_products>
		<total_products_wt>10.5</total_products_wt>
		<conversion_rate>1</conversion_rate>
		<id_shop>1</id_shop>
		<current_state>1</current_state>
	</object>
	<object type="OrderDetail" external-reference="demo-3-1">
		<external_reference for="id_order" type="Order">demo-3</external_reference>
		<findOne
			for="product_id"
			type="Product"
			identifier="id"
		>
			<reference>test1</reference>
		</findOne>
		<product_attribute_id>0</product_attribute_id>
		<id_shop>1</id_shop>
		<id_warehouse>0</id_warehouse>
		<product_price>10</product_price>
		<product_name>10</product_name>
		<product_quantity>10</product_quantity>
	</object>
	<object type="OrderHistory">
		<external_reference for="id_order" type="Order">demo-3</external_reference>
		<id_order_state>1</id_order_state>
	</object>
</objects>
```
