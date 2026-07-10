# Discourse MCP Snap

Strict snap packaging for [discourse/discourse-mcp](https://github.com/discourse/discourse-mcp).

The snap defaults to `https://forum.snapcraft.io` and uses upstream's read-only mode unless configured otherwise.

Snap Store page: <https://snapcraft.io/discourse-mcp>

## Install

Install from the edge channel:

```bash
sudo snap install --edge discourse-mcp
```

## Build and Install Locally

```bash
snapcraft
```

Install a locally built snap:

```bash
sudo snap install --dangerous discourse-mcp_*.snap
```

## Runtime Configuration

This snap does not use the `home` interface. Configure it with `snap set`; do not pass profile files from your home directory.

Default site:

```bash
discourse-mcp
```

Set a different site:

```bash
sudo snap set discourse-mcp site=https://meta.discourse.org
```

Reset to the default site:

```bash
sudo snap unset discourse-mcp site
```

Configure authentication:

```bash
sudo snap set discourse-mcp auth-pairs='[{"site":"https://forum.snapcraft.io","user_api_key":"<key>"}]'
```

Enable writes:

```bash
sudo snap set discourse-mcp allow-writes=true read-only=false
```

Other supported keys:

```text
site              -> --site
read-only         -> --read_only
allow-writes      -> --allow_writes
show-emails       -> --show_emails
auth-pairs        -> --auth_pairs
concurrency       -> --concurrency
default-search    -> --default-search
log-level         -> --log_level
max-read-length   -> --max-read-length
timeout-ms        -> --timeout_ms
tools-mode        -> --tools_mode
```

Additional arguments passed to `discourse-mcp` are appended after snap configuration flags.

## Confinement

The snap plugs only `network`.

Local file uploads and profile files from home directories are intentionally unsupported in this strict package. HTTP transport is not enabled by default because it would require `network-bind`.
