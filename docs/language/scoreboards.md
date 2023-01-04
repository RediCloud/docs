---
sidebar_position: 9
---

# Scoreboards

```kotlin
private val scope = CoroutineScope(Dispatchers.Default) // Default dispatcher
    private val lobbyScoreBoard = ScoreboardFactory().apply { // Create a new scoreboard factory
        title = { // Set the title of the scoreboard
            val player = it.getPlayer()!! // Get the player from the provided uuid
            {
                key = "title" // set the language database key
                content = Component.text("Scoreboard: <player_name>").color(NamedTextColor.RED) // Set the content for the title
                placeholderProvider = { // Access the placeholder provider
                    addStaticPlaceholder("name", player.username) // Add a static placeholder
                }
            }
        }
        empty(1) // Add an empty line
        line {
            score = 2 // Set the score of the line
            name = "health" // Set the name of the line
            content = {
                val player = it.getPlayer()!! // Get the player from the provided uuid
                {
                    key = "health" // Set the language database key
                    content = Component.text("Health: <player_health>").color(NamedTextColor.GOLD) // Set the content for the line
                    placeholderProvider = {// Access the placeholder provider
                        addStaticPlaceholder("health", "${player.health}") // Add a static placeholder
                    }
                }
            }
        }
    }.minestom() // Create the minestom scoreboard (for paper use paper())

    fun onJoin(player: Player) {
        // Do something
        scope.launch {
            lobbyScoreBoard.set(player.uuid) // show the scoreboard to the player
        }
    }

    fun onQuit(player: Player) {
        // Do something
        scope.launch {
            lobbyScoreBoard.remove(player.uuid) // remove the scoreboard from the player
        }
    }
```