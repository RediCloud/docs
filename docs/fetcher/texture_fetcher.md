---
sidebar_position: 2
---

# Texture Fetcher

The texture fetcher is a simple fetcher that fetches the texture url of a player from the UUID.
The fetcher don´t fetch the texture url directly from the Mojang API, it uses the [Minetools api](https://api.minetools.eu).

```kotlin
val uniqueId = UUID.randomUUID() // UUID of the player to fetch
val textureUrl = TextureFetcher.fetchTextureUrl(uniqueId) // Texture url of the player
```

## Cache options

The fetcher stores all results in a hash map.
If you want to force the fetcher to fetch the data again, you can use the `useCache` parameter.

````kotlin
val uniqueId = UUID.randomUUID() // UUID of the player to fetch
val textureUrl = TextureFetcher.fetchTextureUrl(uniqueId, useCache = false) // Texture url of the player (fetches the data again)
````