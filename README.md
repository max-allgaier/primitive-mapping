# primitive-mapping
A simple library that abstracts basic key value structures like JSON and YAML.

## Requirements
Java 8+

## Example Application
Consider following data formats below (JSON and YAML) representing a person and the person's shirt:
```json
{
  "name": "Max",
  "age": 100,
  "shirt": {
    "size": "xl",
    "color": "blue"
  }
}
```
```yaml
name: Max
age: 100
shirt:
  size: xl
  color: blue # This is a comment
```
The JSON and YAML above are both equal in value but are in different formats.
This library can represent the data without having a specific format.
For example, the code below also represents the data above.
```java
PrimitiveMap primitiveMap = PrimitiveMap.createSynchronized()
    .put("name", PrimitiveString.of("Max"))
    .put("age", PrimitiveNumber.ofInt(100))
    .put("shirt", PrimitiveMap.createSynchronized()
        .put("size", PrimitiveString.of("xl"))
        .putWithMetadata("color", PrimitiveString.of("blue"), new Comment("This is a comment"), new OtherMetadata())
    );
// Comment is a custom class, but it is deemed as metadata.
// OtherMetadata can also be a custom class and is used to display how to add additional metadata.
```
The classes Comment and OtherMetadata are custom classes to show that anyone can create and assign metadata. 
