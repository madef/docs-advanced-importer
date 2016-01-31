To create an attachement, it's necessary to use an "attachments" flow:

```
<attachments>
    <attachment external-reference="demo-1">
        <name>Name of the file</name>
        <path>Url of the file to download</path>
	<external_reference for="product" type="product">demo-1</external_reference>
	<external_reference for="product" type="product">demo-2</external_reference>
    </attachment>
</attachments>
```

