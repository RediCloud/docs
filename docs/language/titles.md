---
sidebar_position: 3
---

# Titles

```kotlin
fun sendTestTitle(player: IPlayer) {
    player.sendTitle {
        key = "test" // This is the key of the message
        title = Component.text("A test title") //Minimessage component
        subtitle = Component.text("A test subtitle") //Minimessage component
        fadeIn = 1.seconds.inWholeMilliseconds //time for the title to fade in
        stay = 2.seconds.inWholeMilliseconds //time for the title to stay
        fadeOut = 1.seconds.inWholeMilliseconds //time for the title to fade out
    }
}
```