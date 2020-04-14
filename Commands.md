# Negativity Commands

## /negativity

The main command.

You can open the check menu of a player by specifying its name (e.g `/negativity elikill58`)

Permission: `negativity.negativity`

### verif

Starts checking the given player for specific or all cheats. 

Permission: `negativity.verif`

Usage: `/negativity verif <player> [cheats...]`
- `player` is the player to check
- `cheats` is the list of cheats to test the player for. If ignored it will test for all cheats

### reload

Reloads the configuration of the plugin.

Usage: `/negativity reload`

### admin

Opens the cheat manager. It also has subcommands.

Permission: `negativity.managecheat` (`negativity.admin` for proxies)

#### updateMessages

Updates the message files by replacing them with the bundled files.

The current files are backed up in `lang_backup` or `messages_backup`, depending on the platform.

Permission: `negativity.managecheat` (`negativity.admin` for proxies)

## /lang

Changes your language. Only usable if translations are enabled.

Permission: `negativity.lang`
Usage: `/lang <language>`

## /mod

Opens the mod menu.

Permission: `negativity.mod`

## /report

Allows users to send reports to the staff. Must be enabled in the configuration.

Players with the `negativity.seereport` permission will be able to see reports.

The command has a configurable cooldown that can be bypassed with the `negativity.reportwait` permission.

Permission: `negativity.report`

Usage: `/report <player> <reason>`
- `player` the player to report
- `reason` the reason of the report

## /negkick

Kicks a player for a given reason.

Permission: `negativity.kick`
Usage: `/negkick <player> <reason>`
- `player` the player to kick
- `reason` the reason to display

## /negban

Bans a player temporarily or definitively.

Permission: `negativity.ban`
Alias: `nban`
Usage: `/nban <player> <definitive | duration> <reason>`
- `player` the player to ban
- `definitive` if the player should be banned forever
- `duration` the duration of the ban, formatted like `1h30m` for an hour and a half. Available markers are:
  - `s` seconds
  - `m` minutes
  - `h` hours
  - `d` days
  - `mo` months
  - `y` years
- `reason` the text displayed when the player is banned and when they attempt to connect when still banned

## /negunban

Revokes the ban of a player

Permission: `negativity.unban`
Alias: `nunban`
Usage: `/negunban <player>`
- `player` the name of a banned player
