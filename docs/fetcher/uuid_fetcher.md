---
sidebar_position: 1
---

# UUID Fetcher

The UUID fetcher is a simple fetcher that fetches the name of a player from the UUID or the UUID from the name.

## Name from their UUID

````kotlin
val uniqueId = UUID.randomUUID() // UUID of the player to fetch
val name = UniqueIdFetcher.fetchName(uniqueId) // Name of the player
````

## UUID from their name

````kotlin
val playerName = "Notch" // Name of the player to fetch
val uniqueId = NameFetcher.fetchUniqueId(playerName) // UUID of the player
````

## Cache options

The fetcher stores all results in a hash map.
If you want to force the fetcher to fetch the data again, you can use the `useCache` parameter.

````kotlin
val uniqueId = UUID.randomUUID() // UUID of the player to fetch
val name = UniqueIdFetcher.fetchName(uniqueId, useCache = false) // Name of the player (fetches the data again)
````

````kotlin
val playerName = "Notch" // Name of the player to fetch
val uniqueId = NameFetcher.fetchUniqueId(playerName, useCache = false) // UUID of the player (fetches the data again)
````