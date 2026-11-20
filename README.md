# Remote Device Hub for Antigravity

This plugin connects Google Antigravity to Easelian's Remote Device Hub (RDH).
It bundles the hosted RDH MCP server and the `remote-device-operations` skill
for checking enrolled Linux, macOS, and Windows devices and working with their
files, processes, and browsers when those capabilities are available.

## Install

Install the plugin from GitHub with the Antigravity CLI.

```sh
agy plugin install https://github.com/easelian/remote-device-plugin-antigravity
```

For local development, run these commands from a checkout of the repository.

```sh
agy plugin validate --strict .
agy plugin install .
agy plugin list --json
```

For the App or standalone IDE, place the checkout in
`<workspace>/.agents/plugins/remote-device-hub/` for a single workspace or in
`~/.gemini/config/plugins/remote-device-hub/` for all workspaces. See the
[Antigravity plugin guide](https://antigravity.google/docs/plugins).

## Connect an RDH account

In the Antigravity App, open **Customizations → Installed → MCP Servers** and
select **Authenticate** for `remote-device-hub_rdh`. In the CLI, use
`/mcp` to inspect the server and follow the sign-in prompt. Use the RDH
account associated with the enrolled devices.

After sign-in, ask “Which of my Remote Device Hub devices are online?” The
skill starts with the read-only `list_devices` call. An empty list means the
connected account has no devices to show. Manage devices in the
[RDH console](https://rdh.easelian.com/).

The plugin connects to `https://rdh.easelian.com/mcp` over Streamable HTTP.
Antigravity discovers the RDH OAuth issuer and handles browser sign-in. See the
[Antigravity MCP authentication guide](https://antigravity.google/docs/mcp/#oauth).

For help with setup or troubleshooting, [contact Easelian](https://easelian.com/contact).

## License

Apache-2.0. See [LICENSE](LICENSE).
