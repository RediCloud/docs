---
sidebar_position: 2
---

# Sub paths

This page covers the `@CommandSubPath` annotation.

One Command can have multiple sub paths. This is useful for commands that have a lot of functionality.
You can imagine a sub path like a sub command.

## Command with no sub commands

Command: `/coins`

```kotlin

@CommandSubPath // the player can be any type of player (Paper, Velocity, APIPlayer, CloudNetPlayer, etc.)
fun handle(player : Player){ // the function name can be anything
    //your code
}

```

## Command with sub commands

Command: `/coins top`

```kotlin
@CommandSubPath("top")
fun handleTop(player : Player){
    //your code
}
```

## Command with sub commands and arguments

Command: `/coins Panda260`

```kotlin
@CommandSubPath("<target>")
fun get(player : Player,
	@CommandArgument("target") target : Player){ // the argument name must be the same as the sub path

	target.kill() // the argument will get automatically parsed to the correct type

	//your code
}
```

## Command with path and arguments

Command: `/coins add Panda260 100`

```kotlin
@CommandSubPath("add <target> <amount>")
fun add(player : Player,
	@CommandArgument("target") target : Player,
	@CommandArgument("amount") amount : Int){


	//your code
}
```

## Subcommand with permission

Command: `/coins add Panda260 100`

```kotlin
@CommandSubPath("add <target> <amount>", permission = "coins.add")
```
