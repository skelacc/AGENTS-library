# Agent-Kit Integration Guide

This guide walks you through integrating Agent-Kit into any project, regardless of technology stack or structure.

## Prerequisites

- An AI coding assistant (Claude, GPT-4, Copilot, etc.)
- Ability to reference markdown files in your AI assistant's context
- A project where you want to automate workflows

## Integration Steps

### Step 1: Copy Agent-Kit to Your Project

Choose one of these approaches:

#### Option A: Root-Level Integration (Recommended)
```bash
# Copy entire agent-kit to project root
cp -r agent-kit/ /path/to/your/project/agent-kit/
```

#### Option B: Docs Integration
```bash
# Copy to documentation folder
cp -r agent-kit/ /path/to/your/project/docs/agent-kit/
```

#### Option C: Tools Integration
```bash
# Copy to tools/automation folder
cp -r agent-kit/ /path/to/your/project/tools/agent-kit/
```

### Step 2: Configure Paths

Edit `agent-kit/config.json` to match your chosen location:

```json
{
  "paths": {
    "agents_directory": "agent-kit/agents",
    "skills_directory": "agent-kit/skills"
  },
  "documentation": {
    "agents_file": "AGENTS.md",
    "location": "root"
  }
}
```

**Path Configuration Examples:**

For root integration:
```json
"agents_directory": "agent-kit/agents"
```

For docs integration:
```json
"agents_directory": "docs/agent-kit/agents"
```

For tools integration:
```json
"agents_directory": "tools/agent-kit/agents"
```

### Step 3: Set Up Documentation

Create or update your project's AGENTS.md file:

```bash
# If AGENTS.md doesn't exist in your project
cp agent-kit/templates/AGENTS.md.template AGENTS.md

# Or if it exists, manually add the agent entries
cat agent-kit/templates/AGENTS.md.template >> AGENTS.md
```

### Step 4: Configure AI Assistant Access

Ensure your AI assistant can access agent instructions. Methods vary by tool:

#### GitHub Copilot (VS Code)
Add to `.github/copilot-instructions.md`:
```markdown
## Agent System

This project uses AI agents from agent-kit/. Reference these files:
- agent-kit/AGENTS.md - Agent discovery
- agent-kit/agents/*/instructions.md - Agent behavior
- agent-kit/prompts/agent-standards.md - Creation rules
```

#### Cursor / Windsurf
Add to `.cursorrules` or `.windsurfrules`:
```markdown
@file:agent-kit/AGENTS.md
@file:agent-kit/prompts/agent-standards.md
```

#### Claude / ChatGPT (Direct)
Upload these files to your conversation:
- `agent-kit/AGENTS.md`
- `agent-kit/agents/create-agent-agent/instructions.md`
- `agent-kit/agents/doc-registry-agent/instructions.md`

### Step 5: Verify Integration

Test that agents respond to triggers:

```
"Update AGENTS.md"
```

Expected: doc-registry-agent scans agent-kit/agents/ and updates AGENTS.md

```
"Create an agent that validates commit messages"
```

Expected: create-agent-agent generates new agent in agent-kit/agents/

## Project-Specific Customization

### Adapting for Python Projects

Update agent instructions to reference Python-specific tools:

```json
{
  "tools": ["create", "view", "edit", "bash", "python-env", "pip"]
}
```

### Adapting for JavaScript Projects

Update agent instructions to reference JavaScript-specific tools:

```json
{
  "tools": ["create", "view", "edit", "bash", "npm", "node"]
}
```

### Adapting for Mobile Projects (Kivy, React Native, etc.)

Add project-specific paths to config.json:

```json
{
  "project_specific": {
    "source_directory": "src",
    "build_directory": "buildozer",
    "config_files": ["buildozer.spec", "main.py"]
  }
}
```

## Using Agents in Your Existing Project

### Scenario 1: Creating a Test Agent

```
"Create an agent that runs pytest on changed files and reports coverage"
```

The create-agent-agent will:
1. Generate agent-kit/agents/test-runner-agent/
2. Create agent.json with pytest-specific triggers
3. Write instructions.md with test running behavior
4. Add examples showing how to use it

### Scenario 2: Creating a Build Agent

```
"Create an agent that watches for buildozer.spec changes and rebuilds the APK"
```

The agent will be tailored to your build system.

### Scenario 3: Creating a Documentation Agent

```
"Create an agent that ensures all public functions have docstrings"
```

The agent will scan your codebase and validate documentation.

## Advanced Configuration

### Multi-Project Setup

If you use agent-kit across multiple projects:

```json
{
  "paths": {
    "agents_directory": "/home/user/shared-agents/agents",
    "use_absolute_paths": true
  }
}
```

### Custom Agent Locations

If your project has a specific structure:

```json
{
  "paths": {
    "agents_directory": "automation/ai-agents",
    "skills_directory": "automation/ai-skills"
  }
}
```

### Selective Agent Loading

Only activate specific agents:

```json
{
  "active_agents": [
    "create-agent-agent",
    "doc-registry-agent"
  ]
}
```

## Troubleshooting Integration

### Problem: Agents Don't Activate

**Solution**:
1. Verify AGENTS.md is accessible to your AI assistant
2. Check that trigger phrases match those in AGENTS.md
3. Ensure agent status is "active" in agent.json

### Problem: Paths Not Resolving

**Solution**:
1. Use relative paths from project root
2. Update config.json with correct structure
3. Test paths with `ls agent-kit/agents/`

### Problem: Agents Generate in Wrong Location

**Solution**:
1. Update agents_directory in config.json
2. Ensure create-agent-agent reads config before generation
3. Manually move misplaced agents

### Problem: Standards Not Being Followed

**Solution**:
1. Verify prompts/ directory is accessible
2. Check that agent instructions reference prompts/agent-standards.md
3. Regenerate agent with updated standards

## Best Practices for Integration

1. **Keep agent-kit isolated**: Don't modify core agent files for project-specific needs
2. **Create new agents**: Instead of modifying existing ones, create project-specific agents
3. **Version control**: Commit agent-kit/ to version control for team collaboration
4. **Document triggers**: Keep AGENTS.md updated so team members can discover agents
5. **Test before deploying**: Use examples.md to validate agent behavior

## Removing Agent-Kit

If you need to remove agent-kit from your project:

```bash
# Backup any custom agents you created
cp -r agent-kit/agents/your-custom-agent/ backup/

# Remove agent-kit
rm -rf agent-kit/

# Clean up references in your AI assistant config
# Remove from .github/copilot-instructions.md, .cursorrules, etc.
```

## Getting Help

- Review agent-kit/README.md for overview
- Check agent-kit/examples/ for usage patterns
- Read individual agent instructions.md files for specific behavior
- Refer to prompts/agent-standards.md for creation guidelines

## Next Steps

After integration:
1. Create your first custom agent: `"Create an agent that [does X]"`
2. Review generated files in agent-kit/agents/
3. Test agent with examples from examples.md
4. Update AGENTS.md: `"Update AGENTS.md"`
5. Share with team and document custom agents

---

**Integration Support**: This guide covers common scenarios. For unique project structures, adapt paths in config.json and agent instructions as needed.
