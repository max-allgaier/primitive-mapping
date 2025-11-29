# primitive-mapping
A simple library that abstracts basic key value structures like JSON and YAML.

## Requirements
Java 8+

## Example Application
Take the following files below:

data.json
```json
{
  "name": "Max",
  "age": 100,
  "pocket": {
    "size": "xl",
    "color": "blue"
  }
}
```
data.yml
```yaml
name: Max
age: 100
pocket:
  size: xl
  color: blue # This is a comment
```
The files above are both the "same" but in different formats.
This library can represent the data without having a specific format.
For example, the code below also represents the data above.

```java
PrimitiveMap primitiveMap = PrimitiveMap.createSynchronized()
    .put("name", PrimitiveString.of("Max"))
    .put("age", PrimitiveNumber.ofInt(100))
    .put("pocket", PrimitiveMap.createSynchronized()
        .put("size", PrimitiveString.of("xl"))
        .putWithMetadata("color", PrimitiveString.of("blue"), new Comment("This is a comment"), new OtherMetadata())
    );
// Comment is a custom class, but it is deemed as metadata.
// OtherMetadata can also be a custom class and is used to display how to add additional metadata.
```
