There are two ways to modify the stocks. Either via the stock flow or the flow object. We will not detail the second method as it is more difficult and can only be used by the sellers which need very advanced functionalities (warehouse management for instance).

## Stock flow movement

It is possible to choose the stock movement of the stock definition

Stock Movement:

```
<stocks>
	<stock>
		<product use-external-reference="1">product-demo-1</product>
		<mode>delta</mode>
		<quantity>10</quantity>
	</stock>
</stocks>
```

The stock definition:

```
<stocks>
	<stock>
		<product use-external-reference="1">product-demo-1</product>
		<mode>set</mode>
		<quantity>10</quantity>
	</stock>
</stocks>
```

To modify the stock of a variant, use the tag combination.

Definition of the stock for the variant by using the external reference:

```
<stocks>
	<stock>
		<product use-external-reference="1">product-demo-1</product>
		<combination use-external-reference="1">combination-1</combination>
		<mode>set</mode>
		<quantity>10</quantity>
	</stock>
</stocks>
```

Beware : This flow will show as an error if the variant "combination-1" does not exist (cf 8.2).

## Stock movement in the flow product

It is possible to modify the stocks directly from the flow product by using the [blocks](Basics_About_XML).

## Advanced stocks

If you use avanced stock the previous example will not works. To de fine the stock you have to use a flow object:

```
<stocks>
    <stock>
        <reference>test01</reference>
        <warehouse>1</warehouse> <!-- required -->
        <price>10</price> <!-- required -->
        <quantity>10</quantity> <!-- required -->
        <usable>1</usable> <!-- optional, default value: 1 -->
        <location>Area 5</location> <!-- optional, default value: null -->
        <employee>1</empoyee> <!-- optional, default value: 1 -->
        <currency>1</currency> <!-- optional, default value: null -->
        <reason>1</reason> <!-- optional, default value: 1 -->
    </stock>
</stocks>
```
