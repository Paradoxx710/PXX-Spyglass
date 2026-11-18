# Permissions

Every permission defaults to **op**. Give them to staff with your permissions plugin, like LuckPerms.

| Permission | Allows |
| --- | --- |
| `spyglass.use` | `/sg help`, `/sg events`, `/sg page`, `/sg version`, `/sg stats` |
| `spyglass.search` | `/sg search`, and `/sgv` on the proxy |
| `spyglass.search.ip` | Seeing IP addresses in results, and the `ip:` key. Without it, IPs show as `(ip hidden)` |
| `spyglass.tool` | The inspection wand (`/sg tool`) |
| `spyglass.tele` | Teleporting by clicking a search result |
| `spyglass.worldedit` | The `-we` flag (search inside your WorldEdit selection) |
| `spyglass.rollback` | `/sg rollback`, `/sg restore`, `/sg undo`, `/sg rbqueue` |
| `spyglass.salvage` | `/sg inventory`: taking back items rollbacks destroyed |
| `spyglass.snapshot` | `/sg snapshot`: viewing past inventories and containers |
| `spyglass.snapshot.take` | Taking a copy of an item out of a snapshot |
| `spyglass.import` | `/sg import` |
| `spyglass.migrate` | `/sg migrate` |
| `spyglass.reload` | `/sg reload` |
| `spyglass.update` | Getting update notices in chat |

## Per-action permissions

In `config.conf`, each event type under `events` can define granular permissions:

- **`permission`**: Restricts who can search, inspect with the wand (`/sg tool`), or tab-complete that specific action. For example, if `events.break.permission = "spyglass.action.break"`, players need both `spyglass.search` and `spyglass.action.break` to see break records. If omitted or empty, it defaults to standard `spyglass.search`.
- **`rollback-permission`**: Restricts who can roll back or restore that specific action. For example, if `events.break.rollback-permission = "spyglass.rollback.break"`, executing `/sg rollback a:break` requires that permission node. If omitted or empty, it defaults to `spyglass.rollback`.

This allows granting junior staff access to roll back common griefs (like block placements or breaks) without granting permission to roll back containers, inventory, or entity events.

## Suggested staff setup

| Role | Permissions |
| --- | --- |
| Helper | `spyglass.use`, `spyglass.search`, `spyglass.tool`, `spyglass.tele` |
| Moderator | Helper, plus `spyglass.rollback`, `spyglass.salvage`, `spyglass.snapshot`, `spyglass.worldedit` |
| Admin | Moderator, plus `spyglass.search.ip`, `spyglass.snapshot.take` |
| Owner | Everything: op, or `spyglass.*` in LuckPerms |

Some permissions are deliberately separate: `spyglass.salvage` and `spyglass.snapshot.take` let someone take items, and `spyglass.search.ip` shows personal data, so none of them come with `spyglass.search` or `spyglass.rollback`.
