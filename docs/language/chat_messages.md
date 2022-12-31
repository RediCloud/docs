---
sidebar_position: 2
---

# Chat Messages

```kotlin
fun sendTestMessage(player: IPlayer) {
    player.sendMessage {
        key = "test" // This is the database key of the message
        message = Component.text("Hello World!") //Minimessage component
    }
}
```