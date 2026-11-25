---
name: squarecoil
description: Reads Aria's SquareCoil (ariasigns.squarecoil.net), the sign shop's project system, through the command line Alexandria installs on the person's own Windows PC. Use it for any question about a SquareCoil project or job number, a client or customer, an address, a project's notes, designs, tasks or files, or the design department's request queue.
---

# SquareCoil

SquareCoil has no API, and its connector can't run on your cloud computer. Each person's Windows PC has Alexandria's SquareCoil command line, signed in with that person's own SquareCoil login. Run every command on the **local computer**, never on the cloud computer: the cloud computer has neither the program nor the login.

In PowerShell on the local computer:

```powershell
$sc = "$env:USERPROFILE\.alexandria\claude_connectors\squarecoil"
& "$sc\.venv\Scripts\python.exe" -X utf8 "$sc\squarecoil.py" search "W Gray"
```

In cmd it is one line:

```bat
"%USERPROFILE%\.alexandria\claude_connectors\squarecoil\.venv\Scripts\python.exe" -X utf8 "%USERPROFILE%\.alexandria\claude_connectors\squarecoil\squarecoil.py" search "W Gray"
```

In place of `search "W Gray"`:

| Command | Gives |
|---|---|
| `search "text"` | Projects whose number, name, address, customer or description matches. One field only: `--number`, `--name`, `--status`, `--address`, `--city`, `--state`, `--description`, `--billing-name`, `--purchase-order`, `--salesperson`, `--project-manager`. More results: `--page 2` |
| `project 260675 --include all` | One project by its number: client, contacts, address, scope of work and notes. `--include` adds designs, status, tasks, documents, photos, production_files, contacts, activity, costs (comma-separated, or `all`) |
| `customers "text"` | Customers whose name matches |
| `designs --json --section "In Progress"` | The design request queue. Sections: In Progress, Next Job, On Hold (leave `--section` out for all three). Also `--assigned-to NAME`, `--overdue` |
| `design 5489` | One design request's details, by the `design_key` that `designs` gives (not its Design Id such as 250617-01) |
| `download URL` | Saves one of a project's files, by a URL from `project`, to the person's `Downloads\SquareCoil` folder |

Each prints JSON, except `design`, which prints text. All of it is read-only: the program reads SquareCoil's pages and refuses any page that would change something.

Every project that `project` opens is written to SquareCoil's activity log under the person's name, so open only the projects the question needs.

If `python.exe` isn't there, or the program says no SquareCoil login is stored, the connectors aren't installed on that PC. Tell the person to run **Install Connectors** on Rhino's Alexandria Tools tab, or `Install AI Connectors.cmd` from the shared Alexandria packages folder; it asks for their SquareCoil login. Never ask for the password in chat.
