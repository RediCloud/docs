---
sidebar_position: 7
---

# Placeholders

Each LanguageComponentProvider has a placeholder provider. This allows you to set different placeholders.

## Static placeholder

Static placeholders are values that don't change anymore. They are set when the placeholder is created and can no longer
be changed.

```kotlin
fun setCoins(player: IPlayer, target: IPlayer, coins: Int) {
    /*
    code to set coins
     */
    player.sendMessage {
        key = "coins_set"
        message = Component.text("Coins set to <coins>")
        placeholderProvider = { //Access the placeholder provider
            addStaticPlaceholder("coins", "$coins") //Add a static placeholder
        }
    }
}
```

## Dynamic placeholder

Dynamic placeholders are values that can change. They are set when the placeholder is created and can be changed later.

```kotlin
fun getCoins(player: IPlayer) {
    player.sendMessage {
        key = "coins_get"
        message = Component.text("You have <coins> coins!")
        placeholderProvider = { //Access the placeholder provider
            placeholders += Placeholder("coins", value = {
                ICoreAPI.INSTANCE.getPlayerManager().getPlayerByUUID(player.uuid)!!.coins.toString()
            })
        }
    }
}
```

## Placeholder collections

Placeholder collections are collections of placeholders. They are used to group placeholders together. This is useful if
you want to add multiple placeholders at once without having to add them every time again. 

For example, you create a placeholder collection for the player. This collection contains all placeholders that are
related to the player. You can then add this collection to the placeholder provider.

```kotlin
fun getCoins(player: IPlayer) {
    val playerPlaceholders = PlaceholderCollection("player").apply {
        add(Placeholder("name", { player.name }))
        add(Placeholder("uuid", { "${player.uuid}" }))
        add(Placeholder("coins", { "${player.coins}" }))
        add(
            Placeholder("language", {
                ICoreAPI.INSTANCE.getLanguageManager().getLanguage(player.languageId)?.name
                    ?: ICoreAPI.INSTANCE.getLanguageManager().getDefaultLanguage().name
            })
        )
    }
    player.sendMessage {
        key = "coins_get"
        message = Component.text("You have <coins> coins!")
        placeholderProvider = { //Access the placeholder provider
            placeholderCollections += playerPlaceholders
        }
    }
}
```

## Placeholder collection prefix

Placeholder collections can also have a prefix. This prefix is added to the placeholder name. This is useful if you have
multiple placeholder collections that have the same placeholder but for different objects (e.g. player and target).
You can set the prefix of one collection to "player" and the prefix of the other collection to "target". This way, the
placeholders have different names and can be used in the same message (e.g. "You have <player_coins> coins and <target_coins> coins").

```kotlin
fun setCoins(player: IPlayer, target: IPlayer, coins: Int) {
    val playerPlaceholders = PlaceholderCollection("player").apply {
        add(Placeholder("name", { player.name }))
        add(Placeholder("uuid", { "${player.uuid}" }))
        add(Placeholder("coins", { "${player.coins}" }))
        add(
            Placeholder("language", {
                ICoreAPI.INSTANCE.getLanguageManager().getLanguage(player.languageId)?.name
                    ?: ICoreAPI.INSTANCE.getLanguageManager().getDefaultLanguage().name
            })
        )
    }
    val targetPlaceholders = PlaceholderCollection("target").apply {
        add(Placeholder("name", { target.name }))
        add(Placeholder("uuid", { "${target.uuid}" }))
        add(Placeholder("coins", { "${target.coins}" }))
        add(
            Placeholder("language", {
                ICoreAPI.INSTANCE.getLanguageManager().getLanguage(target.languageId)?.name
                    ?: ICoreAPI.INSTANCE.getLanguageManager().getDefaultLanguage().name
            })
        )
    }

    player.sendMessage {
        key = "coins_set"
        message = Component.text("You set the coins of <target_name> to <coins>!")
        placeholderProvider = { //Access the placeholder provider
            placeholderCollections += playerPlaceholders
            placeholderCollections += targetPlaceholders
            addStaticPlaceholder("coins", "$coins")
        }
    }
    target.sendMessage {
        key = "coins_set_notify"
        message = Component.text("Your coins were set to <coins> by <player_name>!")
        placeholderProvider = { //Access the placeholder provider
            placeholderCollections += playerPlaceholders
            placeholderCollections += targetPlaceholders
            addStaticPlaceholder("coins", "$coins")
        }
    }
}
```