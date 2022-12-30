---
sidebar_position: 3
---

# Argument suggestion

With SuggestionsProvider you can suggest a list of arguments for a command.
The Dustrean api provides a few suggestions providers for you to use.

- PlayerCommandSuggestionProvider - Suggests all online players

## Command with argument suggestions

```kotlin
@CommandSubPath("add <target>")
fun add(player : Player,
	@CommandArgument("target", PlayerCommandSuggestionProvider::class) target : Player,
	@CommandArgument("amount") amount : Int){

	//your code
}
```
