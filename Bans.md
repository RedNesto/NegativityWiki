# The Bans Subsystem

Negativity has its own ban subsystem, it is flexible and can be used in two ways:
- manually, with commands
- automatically, by banning a player when they have too many warns

## Configuration

The ban subsystem configuration is located in the main config file (`config.yml` or `config.conf`), and is quite simple:
- `active`: the main 'switch' of the subsystem, if `true` ban-related commands of the plugins can be used and
 players may be banned automatically for cheating (if they fulfill configurable conditions). Defaults to `false`
- `processor`: the ID of the processor to use. Processors are used to execute and fetch bans. Defaults to `file`
- `time.calculator`: a JavaScript code snippet to compute the duration of a ban. It supports the following placeholders:
  - `%reliability%`: the reliability of the alert triggering the ban
  - `%alert%`: the number of alerts for the cheat of the alert
  - `%all_alert%`: all alerts for the detected cheat since you added Negativity on your server
- `reliability_need`: the minimum reliability of the alert needed to ban a player. Defaults to `95`
- `alert_need`: the number of alerts for the same cheat required before trying banning the player. Defaults to `10`
- `def.time`: the number of bans for a player before banning him definitely. Defaults to `2`

## Processors

### File

ID: `file`
Platform: All

Stores bans on the local filesystem. Useful if you only have one server.

Its configuration is located in the main config file, under `ban.file`:
- `log_bans`: whether old bans (expired or manually revoked) should be kept. Defaults to `true`.

### Database

ID: `database`
Platform: All

Stores bans in a database. Requires a valid database configuration.

Its configuration is located in the main config file, under `ban.database`:
- `log_bans`: whether old bans (expired or manually revoked) should be kept. Defaults to `true`.

### Command

ID: `command`
Platform: All

Executes bans via custom commands. Since this one only uses commands it does not support logged bans.

Its configuration is in the main config file, under `ban.command`:
- `ban` is the list of command to execute when executing bans
- `unban` is the same than `ban`, but for revoking bans

Both lists must contain strings, the order of the commands is respected.

Each command can contain the following placeholders:
- `%uuid%`: the UUID of the player
- `%name%`: the name of the player
- `%ip%`: the IP address of the player
- `%reason%`: the reason of the ban
- `%alert%`: the number of alerts for the detected cheat that triggered the ban
- `%all_alert%`: all alerts for the detected cheat since you added Negativity on your server
- `%life%`: the health of the player at the moment the command is executed
- `%level%`: the level of the player
- `%gm%`: the gamemode of the player
- `%walk_speed%`: the speed at which the player should walk

### Bukkit

ID: `bukkit`
Platform: Spigot

Uses Bukkit's ban system (which by extension is vanilla's one).

### MaxBans

ID: `maxbans`
Platform: Spigot

Uses [MaxBans](https://dev.bukkit.org/projects/maxbans).

### AdvancedBan

ID: `advancedban`
Platform: Spigot

Uses [AdvancedBan](https://www.spigotmc.org/resources/advancedban.8695/).

### Sponge

ID: `sponge`
Platform: Sponge

Uses Sponge's BanService (which delegates to the vanilla system by default).
 Ban plugins usually provide their own service implementation.

However, it has the drawback of not supporting logged bans.

### Proxy

ID: `proxy`
Platform: Spigot & Sponge

Forwards ban execution and revocations to the proxy companion plugin.

**You must enable bans on the proxy plugin's configuration for it to work**
