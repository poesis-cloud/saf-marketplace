# Poesis SAF marketplace

The plugin marketplace for the **Systemic Agentic Framework (SAF)** by Poesis, for GitHub Copilot
(the Copilot CLI, the GitHub Copilot app, and VS Code with the Copilot session target) and for
**Claude Code**. One catalogue per host, same channels and plugin names:

| Host | Catalogue |
| --- | --- |
| GitHub Copilot | `.github/plugin/marketplace.json` |
| Claude Code | `.claude-plugin/marketplace.json` |

| Channel | Branch | Marketplace id | Receives |
| --- | --- | --- | --- |
| Stable | `main` | `poesis-saf` | final releases |
| Preview | `preview` | `poesis-saf-preview` | pre-releases (`-alpha`, `-beta`, `-rc`) |

## Plugins

| Plugin | Description |
| --- | --- |
| `poesis-saf-agentic-harness` | Deterministic governance - regulation - supervision - coordination of agentic organization: workflow orchestration; step, model, skill, instruction resolution; artifact transaction and versioning; logging; agent authorization. |
| `poesis-saf-agentic-organization` | A governed - regulated - supervised - coordinated SAFe-shaped agentic organization: portfolio, program and team orchestrators with a specialist bench. |

Install both: the organization is governed by the harness.

## Install

Copilot CLI (stable):

```bash
copilot plugin marketplace add poesis-cloud/saf-marketplace
copilot plugin install poesis-saf-agentic-harness@poesis-saf
copilot plugin install poesis-saf-agentic-organization@poesis-saf
```

Preview channel: add the `preview` branch of this repository as a marketplace and install from
`@poesis-saf-preview`.

GitHub Copilot app: Customize, then add the marketplace `poesis-cloud/saf-marketplace`, then install
both plugins.

VS Code: enable `chat.plugins.enabled`, add `poesis-cloud/saf-marketplace` to
`chat.plugins.marketplaces`, install both plugins from the Agent Customizations editor, and use
the **Copilot** session target.

Claude Code (stable):

```bash
claude plugin marketplace add poesis-cloud/saf-marketplace
claude plugin install poesis-saf-agentic-harness@poesis-saf
claude plugin install poesis-saf-agentic-organization@poesis-saf
```

Claude Code preview channel: declare the `preview` branch in `.claude/settings.json`, then
install from `@poesis-saf-preview`:

```json
{
    "extraKnownMarketplaces": {
        "poesis-saf-preview": {
            "source": { "source": "github", "repo": "poesis-cloud/saf-marketplace", "ref": "preview" }
        }
    }
}
```

The SAF `init` skill writes this file for a new workspace. A Claude Code entry appears once its
plugin repository has released a Claude Code plugin (orphan branch `claude-plugin`, tag
`claude-plugin-v<version>`).

Full documentation: <https://docs.poesis.cloud/saf/>.

## How this repository is updated

Release workflows of the plugin repositories open a pull request here, bumping the entry's
`version`, `ref` and `sha` in both catalogues (the Copilot plugin's and the Claude Code plugin's). The pull request merges automatically once its validation passes.
Auto-update is opt-in for users.

## License

Apache-2.0.
