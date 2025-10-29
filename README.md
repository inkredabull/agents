# My Agent Marketplace

A simple Claude Code marketplace for custom plugins.

## Structure

```
agents/
├── .claude-plugin/
│   └── marketplace.json       # Marketplace manifest
└── hello-plugin/              # First plugin
    ├── .claude-plugin/
    │   └── plugin.json        # Plugin metadata
    └── commands/
        └── hello.md           # /hello command
```

## Installation

From within Claude Code, run:

```
/plugin marketplace add /Users/inkredabull/Code/inkredabull/agents
/plugin install hello-plugin@my-agent-marketplace
```

## Usage

After installation, you can use:

```
/hello
```

This will trigger the hello command from the plugin.

## Next Steps

You can extend this marketplace by:
- Adding more plugins to the marketplace.json
- Creating custom agents in the `agents/` directory
- Adding skills in the `skills/` directory
- Configuring hooks in `hooks/hooks.json`
