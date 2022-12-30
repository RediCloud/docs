---
sidebar_position: 4
---

# Custom SuggestionProvider

If you want to create your own suggestion provider, you can do so by implementing the `CommandSuggestionProvider` interface.

```kotlin
class CustomCommandSuggestionProvider : CommandSuggestionProvider {

    override fun getSuggestions(sender: ICommandActor, fullCommand: String, lastArgument: String): List<String> {
        return listOf("suggestion1", "suggestion2")
    }
```

## How to use

To use your custom suggestion provider, you need to add it like the other to the `@CommandArgument` annotation.
