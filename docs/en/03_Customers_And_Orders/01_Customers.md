Importing customers can be do with the flow object.

Example of creating a customer:

```
<objects>
	<object type="customer" external-reference="demo-1">
		<lastname>Lastname</lastname>
		<firstname>Firstname</firstname>
		<email>test@domain.tld</email>
		<passwd modifier="Tools::encrypt">myPassword</passwd>
	</object>
</objects>
```

An other example of creating a customer plus a group and adding customer to the group:

```
<objects>
	<object type="customer" external-reference="demo-1">
		<lastname>Lastname</lastname>
		<firstname>Firstname</firstname>
		<email>test@domain.tld</email>
		<passwd modifier="Tools::encrypt">myPassword</passwd>
		<block>
			<objects>
				<object type="group" external-reference="demo-1">
					<name lang="en">My Group</name>
					<price_display_method>1</price_display_method> <!-- Taxes incluse -->
					<block>
						<objects>
							<object type="customerGroup" external-reference="demo-1">
								<id_customer>{{id}}</id_customer>
								<id_group>\{\{id\}\}</id_group>
							</object>
						</objects>
					</block>
				</object>
			</objects>
		</block>
	</object>
</objects>
```
