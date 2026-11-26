# C4Lens

C4Lens turns a text model of your software architecture into an interactive diagram you open straight from disk.
You write the model in the `.c4` DSL. It draws C4 views, keeps hand-made layouts when the model changes, exports SVG and PNG for READMEs and wikis, and lets a coding agent read and update the model through MCP.

It runs locally and works offline. No server and no account are needed.

Get the latest build from the [Releases page](../../releases?q=c4-lens) (tagged `c4-lens-v<version>`).

## Install

Requires [Node.js](https://nodejs.org) 22.22.3 or newer.

1. Download `c4lens-<version>.tgz` from the release.
2. Install it:

   ```bash
   npm install -g ./c4lens-<version>.tgz
   ```

3. Check it: `c4lens --version`

To update, download the newer `.tgz` and run the same command. To remove it, run `npm uninstall -g c4lens`.

## Use it

In the repo you want to document:

```bash
c4lens init
```

This writes a starter model at `docs/architecture/model/model.c4`, a `c4lens.config.json`, and a `.mcp.json` entry so Claude Code finds the MCP server. Nothing existing is overwritten unless you pass `--force`.

Run `c4lens --help` for the other commands: build the viewer, edit layouts, export SVG and PNG, and migrate C4 InterFlow models.

## Your data

C4Lens reads the files in your repo and writes its output beside them. It makes no network calls of its own.

## Use responsibly

It is provided as-is, with no warranty.

## License

Apache License 2.0 — see [LICENSE](LICENSE). Third-party components and credits are listed in [NOTICE](NOTICE).
