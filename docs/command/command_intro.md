---
sidebar_position: 1
---

# Command intro

The command api is cross-platform annotation based api that allows you to create commands.
It currently supports the following platforms:

- Paper
- Velocity
- Minestom

## Creating a command class

To create a command you need to create a class that extends `Command` class for your platform.

`<platformCommand>` can be one of the following:

- `PaperCommand`
- `VelocityCommand`
- `MinestomCommand`

```kotlin

object CoinsCommand : <platformCommand>(
	commandName = "coins",
	commandDescription = "shows your coins", // optional
	commandAliases = arrayOf("money", "cash"), // optional
	commandPermission = "dustrean.coins", // optional
) {
	...
}

```

## Registering a command

To register a command you need to call `registerCommand` function on your platforms `CommandManager` class.

```kotlin

ICoreAPI.getInstance().getCommandManager()?.registerCommand(CoinsCommand)

```
