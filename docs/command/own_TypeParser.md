---
sidebar_position: 5
---

# Custom TypeParser

If you want to create your own TypeParser, you can do so by implementing the `IStringTypeParser` interface.

```kotlin
class UUIDParser : IStringTypeParser<UUID> {
    override fun parse(value: String): UUID {
        return UUID.fromString(value)
    }

    override fun allowedTypes(): List<Class<out UUID>> {
        return listOf(UUID::class.java)
    }
}
```

## How to use

To use your custom TypeParser, you need to register it it the StringParser object.

```kotlin
StringParser.customTypeParsers.add(UUIDParser())
```
