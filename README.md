# Research Multi-Agent System Generator

This generator can automatically create a complete, immediately runnable multi-agent research system based on your research project requirements.

## Usage

### 1. Fill in User Input

Open [user_input.md](user_input.md) and fill in your research project information as prompted:

- Research topic and core questions
- Data collection requirements
- Analysis methods
- Report format and style

If you're unsure about certain questions, you can fill in "Suggested by AI".

### 2. Invoke the Generator

Execute in Claude Code:

```
Please read the information I filled in generator/user_input.md,
then use the generator/generator.md prompt,
to generate a research multi-agent system for me.
```

### 3. Obtain the Generated System

The generator will create a complete project for you, including:

```
{your-project-name}/
├── agents/                  # 4 agent blueprints
├── data/                    # Data directories (3 phases)
├── references/              # Reference materials
├── wip/                     # Work-in-progress notes
└── README.md                # Project documentation
```

### 4. Run the System

After generation, execute:

```
Please use agents/00.orchestrator.md to start executing the research task
```

The system will automatically complete: data collection → analysis → report generation

## Generated System Architecture

Based on **declarative multi-agent architecture**, using five core patterns:

1. **Prompt-Defined Agents** - Define agent behavior with natural language
2. **Orchestrated Pipeline** - Three-phase sequential execution, data refined progressively
3. **Filesystem Data Bus** - Data passed through files, completely transparent
4. **Parallel Instance Execution** - Support parallel processing of multiple data sources
5. **Reference Data Configuration** - Domain knowledge externalized as independent files

For detailed architecture description, see [generator.md](generator.md).

## Suitable Scenarios

Particularly suitable for:
- Information-intensive research (extensive data collection and analysis)
- Periodic research (repeatable execution)
- Quality-first research (transparent and traceable)

## File Descriptions

- [user_input.md](user_input.md) - User fills in research project information
- [generator.md](generator.md) - Generator prompt (includes architecture principles and generation logic)
- README.md - This file (usage instructions)

---

Quick start: First fill in [user_input.md](user_input.md), then invoke the generator!
