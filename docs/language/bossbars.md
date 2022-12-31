---
sidebar_position: 3
---

# Boss Bars

```kotlin
fun sendTestBossBar(player: IPlayer) {
    player.sendBossBar {
        key = "test" // This is the key of the message
        name = Component.text("A test boss bar") //Minimessage component
        progress = 0.5f // 0.0f to 1.0f
        color = BossBar.Color.GREEN // BossBar.Color
        overlay = BossBar.Overlay.PROGRESS // BossBar.Overlay
    }
}
```