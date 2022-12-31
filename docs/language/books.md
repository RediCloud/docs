---
sidebar_position: 5
---

# Books

```kotlin
fun openTestBook(player: IPlayer) {
    player.openBook {
        key = "test" // This is the key of the message
        title = Component.text("A test book") //Minimessage component
        author = Component.text("Suqatri") //Minimessage component
        pages = mutableListOf(
            Component.text("This is a test page"), //Page 1 content
            Component.text("This is another test page"), //Page 2 content
        )
    }
}
```