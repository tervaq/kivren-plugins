# Kivren plugin

Two concise workflows for Codex and Claude Code:

- **kivren-computer-inspect**: inspect selected files on an owner-connected computer.
- **kivren-room-coordinate**: use a separately owner-configured room connection to
  read decisions and coordinate approved work.

The bundled HTTP MCP server is `https://mcp.kivren.link/mcp` and provides computer
access after Kivren OAuth and owner consent. It does **not** provide project-room
tools. Runtime availability and permissions are checked when a skill runs. The
packaged endpoint's authenticated deployed catalog still needs owner acceptance;
source validation is not a successful live connection.

## Install from the Kivren marketplace

Review the package before installation. The plugin runs no installation hooks.
Use the published marketplace or a reviewed local copy.

Codex:

```sh
codex plugin marketplace add tervaq/kivren-plugins
codex plugin add kivren@kivren-plugins
```

Open the desktop Plugins directory, select **Kivren**, and install **Kivren**.
Follow the host's connection/OAuth UI for computer access. Refresh/restart the
host as required, then use the skill picker to select the installed skill.
Marketplace registration alone is not installation or authentication.

Claude Code:

```sh
claude plugin marketplace add tervaq/kivren-plugins
claude plugin install kivren@kivren-plugins
```

In Claude Code, its skill commands are
`/kivren:kivren-computer-inspect` and `/kivren:kivren-room-coordinate`.
Use `/mcp` to inspect/authenticate the computer connection. Authenticate through the host when prompted. Installing a plugin does not provide
a model subscription or complete computer authorization.

## Room setup is separate

Use Kivren's existing native owner-confirmed Codex/Claude Code integration and
publish the intended project room to that profile. The existing local connection
uses the installed `kivren mcp-proxy` with owner-selected data/profile arguments.
It is intentionally not hard-coded into this package: paths, profiles and grants
belong to the owner. Preserve any existing managed `kivren` entry. This plugin's
server is named `kivren-computer` to keep those identities separate.

Verify the room connection actually advertises `kivren_rules` and `kivren_context`
before using the room skill. No signup is implied for local collaboration.
Do not substitute computer tools for a room connection or assume that installing
this plugin enrolls a device or starts a daemon. Remove/disable the plugin through
the host's Plugins UI; revoke computer access separately in Kivren if desired.

## Review and distribution status

Version 0.1.0 is a development-preview plugin. Installing from this marketplace
is separate from a reviewed listing in the OpenAI or Anthropic directories.
The two host manifests share skills, one MCP manifest and the unchanged approved
Kivren mark. No runtime binary, hook, credential, model override, automatic tool
approval, or client settings file is bundled. The server can expose more powerful
tools than these inspection instructions; installation does not narrow existing
server grants. Host/native permissions remain authoritative. Computer file data
and results are readable by Kivren's gateway and the selected provider.

Kivren and its brand assets remain proprietary; this package makes no new
open-source license grant. Service use is governed by the published [Kivren terms](https://kivren.link/terms/).
For support, visit [Kivren](https://kivren.link/about/).
See the [privacy notice](https://kivren.link/privacy/) for data handling.
