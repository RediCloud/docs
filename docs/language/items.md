---
sidebar_position: 8
---

# Items

```kotlin
object Navigator : ItemStack(
    {
        key = "lobby_navigator" // This is the database key of the message
        material = Material.COMPASS // Material of the item
        name = Component.text("Navigator").color(NamedTextColor.GOLD) // Name of the item (MiniMessage)
        lore = mutableListOf( // Lore of the item (MiniMessage)
            Component.text("Click to open the navigator").color(NamedTextColor.GRAY)
        )
    },
    clickHandler = { uuid ->// Handler to handle click events
        // open navigator
        true // cancel event
    },
    dropHandler = { uuid -> // Handler to handle drop events
        uuid.getPlayer()!!.playSound(Sound.sound(Key.key("music_disc.13"), Sound.Source.MUSIC, 1f, 1f)) //Do something
        true//cancel event
    },
    interactHandler = { uuid, interactType ->  // Handler to handle interact events
        true // cancel event
    }
)
```