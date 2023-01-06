---
sidebar_position: 2
---

# Texture Fetcher

The texture fetcher is a simple fetcher that fetches the texture url of a player from the UUID.

```kotlin
val uniqueId = UUID.randomUUID() // UUID of the player to fetch
val textureUrl = TextureFetcher.fetchTextureUrl(uniqueId) // Texture url of the player
```