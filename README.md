# everything-ai-need

A comprehensive configuration repository for AI-powered development with Claude Code and OpenCode. Contains rules, commands, skills, and agents for structured, high-quality software engineering.

---

## Overview

This repository provides a complete setup for AI-assisted development including:

- **Rules** - Development standards and best practices
- **Commands** - Slash commands for common workflows
- **Skills** - Domain-specific knowledge guides (Rust, Kotlin, Go, Python, etc.)
- **Agents** - Specialized AI agents for planning, review, and execution

---

## Setup Instructions

### For Claude Code (Workspace Setup)

This setup makes agents, commands, and skills available when working in the workspace directory.

#### Step 1: Install Claude Code

```bash
# Install globally via npm
npm install -g @anthropics/claude-code

# Or use npx (no install)
npx @anthropics/claude-code
```

#### Step 2: Configure Claude Code

```bash
# Run initial setup (configures API key, theme, etc.)
claude config

# Set your Anthropic API key
claude config set apiKey sk-ant-api-...

# Or use environment variable
export ANTHROPIC_API_KEY=sk-ant-api-...
```

#### Step 3: Setup Workspace Configuration

Choose or create a workspace directory where you want to use these configurations:

```bash
# Navigate to your workspace directory
cd ~/your-workspace

# Create the .claude directory structure
mkdir -p .claude/{agents,commands,skills}

# Copy agents from this repository
cp /path/to/everything-ai-need/agents/*.md .claude/agents/

# Copy commands from this repository
cp /path/to/everything-ai-need/commands/*.md .claude/commands/

# Copy skills from this repository
cp /path/to/everything-ai-need/skills/*.md .claude/skills/
```

Or use symlinks for easier updates:

```bash
cd ~/your-workspace
ln -sf /path/to/everything-ai-need/agents .claude/agents
ln -sf /path/to/everything-ai-need/commands .claude/commands
ln -sf /path/to/everything-ai-need/skills .claude/skills
```

#### Step 4: Launch Claude Code in Workspace

```bash
# Navigate to your workspace directory
cd ~/your-workspace

# Launch Claude Code
claude

# Claude Code will automatically load agents, commands, and skills from .claude/
```

#### Step 5: Verify Setup

Once inside Claude Code, run:

```
/reload-plugins    # Reload plugins to pick up new agents/skills
/agents            # Should list available agents
/skills            # Should list available skills
```

#### Step 6: Use Commands

Available slash commands:

```
/plan <feature>           # Create implementation plans
/tdd                      # Run test-driven development workflow
/code-review              # Review code for quality and security
/rust-build               # Fix Rust build errors
/go-test                  # Enforce TDD for Go
/kotlin-test              # Enforce TDD for Kotlin
/multi-workflow <project> # Multi-model collaborative workflow
```

See `commands/` directory for full list of 50+ commands.

---

### For OpenCode

#### Step 1: Install OpenCode

```bash
# Install globally via npm
npm install -g opencode

# Or via yarn
yarn global add opencode
```

#### Step 2: Configure OpenCode

```bash
# Run setup wizard
opencode init

# Set API key
opencode config set api.key sk-ant-api-...

# Or edit config directly
opencode config edit
```

#### Step 3: Link Configuration

OpenCode uses a different configuration structure. Copy or symlink this repository's configuration:

```bash
# Option 1: Copy files to OpenCode config
mkdir -p ~/.config/opencode
cp -r /path/to/everything-ai-need/agents ~/.config/opencode/
cp -r /path/to/everything-ai-need/commands ~/.config/opencode/
cp -r /path/to/everything-ai-need/skills ~/.config/opencode/

# Option 2: Symlink for easier updates (recommended)
ln -sf /path/to/everything-ai-need/agents ~/.config/opencode/agents
ln -sf /path/to/everything-ai-need/commands ~/.config/opencode/commands
ln -sf /path/to/everything-ai-need/skills ~/.config/opencode/skills
```

#### Step 4: Use Commands

```bash
# Launch OpenCode in any project directory
opencode

# Use commands (syntax may vary by OpenCode version)
@plan <feature>
@tdd
@code-review
@rust-build
```

---

## Repository Structure

```
.
├── rules/           # Development standards and guidelines
│   └── common.md    # Core development rules
│
├── commands/        # Slash commands for workflows
│   ├── plan.md      # Planning command
│   ├── tdd.md       # TDD workflow
│   ├── code-review.md
│   ├── rust-build.md
│   ├── go-test.md
│   ├── kotlin-test.md
│   └── ...          # 50+ commands
│
├── skills/          # Domain-specific knowledge
│   ├── rust.md      # Rust development guide
│   ├── deep-research.md
│   ├── tdd-workflow.md
│   ├── continuous-learning.md
│   └── ...
│
├── agents/          # Specialized AI agents
│   ├── planner.md   # Planning specialist
│   ├── code-reviewer.md
│   ├── tdd-guide.md
│   ├── security-reviewer.md
│   └── ...
│
└── settings.json    # Environment configuration
```

---

## Quick Reference

### Available Commands

| Command | Description |
|---------|-------------|
| `/plan` | Create implementation plans |
| `/tdd` | Test-driven development workflow |
| `/code-review` | Code quality review |
| `/security-review` | Security analysis |
| `/rust-build` | Fix Rust compilation errors |
| `/rust-test` | Rust TDD workflow |
| `/go-build` | Fix Go build errors |
| `/go-test` | Go TDD workflow |
| `/kotlin-build` | Fix Kotlin build errors |
| `/kotlin-test` | Kotlin TDD workflow |
| `/multi-workflow` | Multi-model collaborative workflow |
| `/e2e` | Generate E2E tests |
| `/verify` | Run verification checks |

### Available Agents

| Agent | Description |
|-------|-------------|
| `planner` | Expert planning specialist |
| `code-reviewer` | Code quality and security review |
| `security-reviewer` | Security analysis specialist |
| `tdd-guide` | TDD workflow guidance |
| `architect` | Architecture decisions |
| `build-error-resolver` | Fix build errors |
| `database-reviewer` | Database review specialist |

### Available Skills

| Skill | Description |
|-------|-------------|
| `/rust` | Rust development patterns |
| `/deep-research` | Research methodology |
| `/tdd-workflow` | TDD best practices |
| `/frontend-patterns` | Frontend architecture |
| `/market-research` | Market analysis |

---

## Key Principles

### Development Workflow
- **Research First** - Search existing solutions before writing code
- **Plan Before Code** - Create detailed implementation plans
- **Test-Driven** - Write tests first, aim for 80%+ coverage
- **Review Always** - Code review is mandatory

### Security
- No hardcoded secrets
- Validate all inputs
- Use parameterized queries
- Implement rate limiting
- Follow security review protocol

### Testing
- Unit tests for functions
- Integration tests for APIs
- E2E tests for critical flows
- 80% minimum coverage
- 100% for critical code

---

## Troubleshooting

### Agents/Skills Not Loading

1. **Check directory structure** - Ensure `.claude/` is in the correct location
2. **Reload plugins** - Run `/reload-plugins` in Claude Code
3. **Check file permissions** - Files should be readable
4. **Verify YAML frontmatter** - Agents need proper frontmatter with `name` and `description`

### Commands Not Available

1. **Check current directory** - Must be in workspace where `.claude/` exists
2. **Verify commands directory** - Should contain `.md` files with proper frontmatter
3. **Restart Claude Code** - Sometimes needs a full restart

---

## Contributing

1. Follow existing patterns in the repository
2. Update this README when adding new commands/skills
3. Maintain consistency with existing documentation style

---

## License

MIT
