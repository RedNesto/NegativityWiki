# Permissions

Negativity has its own cross-platform permissions management layer.

It is based on a _checker_ that will indicate if a player has the permission to do an action.

The checker can be set in the configuration `Permissions.checker` (defaults to `platform`).

The `platform` checker delegates the check to the underlying permission system (usually a permissions plugin).

Other plugins can register their own checkers to hold their own logic and make their decision based on other information (like a power system, or a per-player state)

---

The following permissions are used for commands and can't be changed:
![Negativity permissions](https://img.eliapp.fr/negativity_permission.png)

the following permissions can be edited in the configuration.
* showAlert : Allow to show cheating alerts
* verif : Allow to run verif with /negativity verif <player> command
* manageCheat : Add an item in Mod Inventory to manage cheat
* report_wait : Remove time between 2 reports
* notBanned : Allow to bypass all ban system
* bypass : Allow to bypass a specific cheat 
