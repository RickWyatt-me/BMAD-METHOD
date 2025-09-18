# Claude Code Extension Setup Guide

This guide provides step-by-step instructions for installing and using the Claude Code extension with BMAD-METHOD™ agents.

## Overview

The Claude Code extension by Anthropic brings Claude AI directly into VS Code, allowing you to interact with AI through a dedicated chat panel and slash commands. When combined with BMAD-METHOD™, you get access to specialized AI agents for different development roles.

## Prerequisites

- **VS Code**: Version 1.80 or higher
- **Node.js**: Version 20 or higher
- **Anthropic API Key**: Required for Claude Code extension

## Installation Steps

### Step 1: Install Claude Code Extension

1. Open VS Code
2. Go to Extensions view (Ctrl+Shift+X or Cmd+Shift+X)
3. Search for "Claude Code" or "Claude" by Anthropic
4. Click "Install" on the official Claude Code extension

### Step 2: Configure API Key

1. After installation, click the Claude icon in your VS Code sidebar
2. Follow the setup prompts to configure your Anthropic API key
3. Get your API key from [Anthropic Console](https://console.anthropic.com)
4. Test the connection by asking Claude a simple question

### Step 3: Install BMAD-METHOD™ Agents

In your project directory, run:

```bash
# For new projects
npx bmad-method install --full --ide claude-code

# For existing BMAD projects
npx bmad-method install --ide claude-code
```

This creates the `.claude/commands/BMad/` directory structure with all agent commands.

## Usage Guide

### Activating Agents

**Method 1: Slash Commands (Recommended)**

1. Open Claude Code chat panel (click Claude icon in sidebar)
2. Type `/` followed by agent name:
   - `/dev` - Full Stack Developer
   - `/pm` - Product Manager
   - `/architect` - System Architect
   - `/qa` - Quality Assurance Engineer
   - `/analyst` - Business Analyst
   - `/sm` - Scrum Master
   - `/po` - Product Owner
   - `/ux-expert` - UX Expert
   - `/bmad-orchestrator` - Multi-agent coordinator

**Method 2: Command Palette**

1. Press Ctrl+Shift+P (Cmd+Shift+P on Mac)
2. Type "Claude" to see available commands
3. Select from BMad agent commands

### Using Agent Commands

Once an agent is activated, you can use their specific commands:

```text
*help - Show all available commands for the current agent
*create - Create new user stories (SM agent)
*shard-doc docs/prd.md prd - Break down documents
*review - Review code or documents (QA agent)
*analyze - Analyze requirements (Analyst agent)
```

### Best Practices

1. **Start Fresh Chats**: When switching agents, start a new chat for best results
2. **Use Specific Agents**: Choose the right agent for your task (dev for coding, pm for planning)
3. **Load Context**: Agents automatically load project configuration from `.bmad-core/core-config.yaml`
4. **Follow Workflows**: Use agent commands to follow BMad workflows (planning → development → testing)

## File Structure

After installation, your project will have:

```
your-project/
├── .claude/
│   └── commands/
│       └── BMad/
│           ├── agents/           # Agent command files
│           │   ├── dev.md
│           │   ├── pm.md
│           │   ├── architect.md
│           │   └── ...
│           └── tasks/            # Task command files
│               ├── create-doc.md
│               ├── shard-doc.md
│               └── ...
└── .bmad-core/                   # Core BMad framework
    ├── agents/                   # Agent definitions
    ├── tasks/                    # Task definitions
    ├── templates/                # Document templates
    └── core-config.yaml         # Project configuration
```

## Troubleshooting

### Common Issues

**Agent commands not appearing**

- Ensure you ran `npx bmad-method install --ide claude-code`
- Check that `.claude/commands/BMad/` directory exists
- Restart VS Code

**Extension not responding**

- Reload VS Code window (Ctrl+Shift+P → "Developer: Reload Window")
- Check your Anthropic API key configuration
- Verify internet connection

**Agent personas not working correctly**

- Make sure you're using slash commands (`/dev` not `dev`)
- Start a new chat when switching agents
- Check that agent files exist in `.claude/commands/BMad/agents/`

**Commands missing or incomplete**

- Re-run the installer: `npx bmad-method install --ide claude-code`
- Check that `.bmad-core/` directory contains all agent files
- Verify file permissions

### Getting Help

1. **Agent Help**: Type `*help` after activating any agent
2. **BMad Orchestrator**: Use `/bmad-orchestrator` for multi-agent guidance
3. **Documentation**: Check `.bmad-core/user-guide.md` for complete workflow
4. **Community**: Join the BMad Discord community for support

## Advanced Usage

### Custom Agent Workflows

You can create custom workflows by combining agents:

1. **Planning Phase**: `/pm` → `/analyst` → `/architect`
2. **Development Phase**: `/sm` → `/dev` → `/qa`
3. **Review Phase**: `/qa` → `/ux-expert` → `/pm`

### Multi-Agent Coordination

Use the BMad Orchestrator for complex tasks:

```text
/bmad-orchestrator
I need to plan and implement a new feature for user authentication
```

The orchestrator will guide you through the appropriate agent sequence.

### Integration with VS Code Features

- **File Operations**: Agents can read and modify files in your workspace
- **Git Integration**: Agents understand your git history and changes
- **Extension Ecosystem**: Works alongside other VS Code extensions
- **Terminal Integration**: Agents can suggest and run terminal commands

## Next Steps

After setup, follow the [BMAD-METHOD™ User Guide](../bmad-core/user-guide.md) to learn the complete workflow from planning to implementation.

For specific development workflows, see:

- [Working in the Brownfield](working-in-the-brownfield.md) - Existing codebases
- [Core Architecture](core-architecture.md) - Technical deep dive
- [Expansion Packs](expansion-packs.md) - Extending BMad for your domain
