---
sidebar_position: 6
---

# Tab List

```kotlin
fun sendTestTabList(player: IPlayer) {
    player.sendTabList {
        key = "test" // This is the key of the message
        header = Component.text("A test header") //Minimessage component
        footer = Component.text("A test footer") //Minimessage component
    }
}
```