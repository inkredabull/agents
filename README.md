# Quite an Inkredabull Marketplace

A simple Claude Code marketplace for custom plugins.

## Structure

```
agents/
├── .claude-plugin/
│   └── marketplace.json       # Marketplace manifest
└── spin-doctor/               # Spin Doctor plugin
    ├── .claude-plugin/
    │   └── plugin.json        # Plugin metadata
    └── commands/
        └── spin.md            # /spin command
```

## Installation

From within Claude Code, run:

```
/plugin marketplace add https://github.com/inkredabull/agents
/plugin install spin-doctor@quite-an-inkredabull-marketplace
```

## Usage

After installation, you can use:

```
/spin [your message or situation]
```

The Spin Doctor will reframe any message or situation in a positive, constructive way!

## Next Steps

You can extend this marketplace by:
- Adding more plugins to the marketplace.json
- Creating custom agents in the `agents/` directory
- Adding skills in the `skills/` directory
- Configuring hooks in `hooks/hooks.json`
