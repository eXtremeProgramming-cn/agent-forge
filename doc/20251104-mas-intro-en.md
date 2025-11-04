# Multi-Agent Systems: Software Modularity in the AI Era

> From the Dilemma of Long Prompts to Modular Design of Agents

## 1. The Dilemma of Long Prompts

When we begin to use large language models (LLMs) extensively for complex tasks, we quickly encounter a seemingly paradoxical phenomenon: prompt engineering techniques are becoming increasingly sophisticated, prompts themselves are growing longer, yet the results don't always improve accordingly.

### 1.1 The Evolution of Prompt Engineering

Prompt engineering, as an emerging practice, has developed rapidly over the past few years. We've learned to use various techniques to enhance LLM output quality:

- **Problem Orientation**: State the problem first, then provide specific instructions
- **Epistemology Frame**: Explicitly specify analytical perspectives and theoretical frameworks
- **Exhaustive Input**: Provide sufficient background information and context
- **Prescribed Process**: Break down the task step-by-step
- **Structured Output**: Precisely define output format
- **Style Mimicry**: Provide examples for the LLM to learn specific styles

These techniques are indeed effective. But they also mean one thing: **prompts are getting longer and longer**.

From initial simple phrases to detailed instructions of hundreds of words, then to complex prompts of thousands of words. When we handle truly complex knowledge work—such as writing research reports or conducting multi-dimensional analyses—prompts can easily reach tens of thousands of words in scale.

Furthermore, we've even developed an "Attachment" pattern: uploading large documents as part of the prompt. These documents might include:

- Methodological descriptions (e.g., dialectical analysis methods, tens of thousands of words)
- Theoretical frameworks (e.g., Marxist epistemology, tens of thousands of words)
- Style guides (e.g., academic writing standards, thousands of words)
- Reference materials (various background documents)

Essentially, these "attachments" are all components of an enormously long prompt. Sometimes, a complete prompt can reach a scale of 30,000-50,000 words.

### 1.2 Three Major Problems with Long Prompts

As a programmer, I quickly realized that the problems with long prompts are structural:

**Problem One: Attention Dilution**

Even without exceeding context window limits, when prompts contain large amounts of detailed instructions, LLMs struggle to perfectly execute all requirements. Just like humans reading a lengthy document, LLMs experience:

- Attention dilution, overlooking certain details
- Autonomous simplification of instructions, executing according to their own understanding
- Loss of priority judgment among multiple goals

The result is unstable output quality, making it difficult to achieve the perfect results that long prompts aim for.

**Problem Two: Lack of Module Isolation**

You might think you've done "module division" in your prompt—like "do this in step one, do that in step two." But in reality, all content is loaded into the LLM at once. This means:

- "Pull one hair and move the whole body": modifying the contradiction analysis method might unexpectedly affect the execution of class analysis
- No true boundaries: all modules influence each other in the same context
- No isolation possible: coupling between different parts is uncontrollable

This is like writing all code in one giant function—although you've divided it into sections with comments, it's essentially still a monolith.

**Problem Three: Difficult to Maintain**

Long prompts make it nearly impossible to implement flexible parameter passing and flow control:
- **Parameter passing impossible**: You can only set some "global constants" at the outermost layer (like "analyze XXX country"); it's nearly impossible to generate variables from one module and then use those variables to invoke other modules
- **Dynamic flow control difficult**: Want "information collection" to loop three rounds, with evaluation and gap-filling after each round? Nearly impossible in long prompts—you can't make the LLM "pause," check intermediate results, and "continue"
- **High modification cost**: Want to adjust the style guide? Need to reload the entire 30,000-word prompt; want to add a new analytical dimension? The entire prompt becomes longer, complexity grows exponentially

### 1.3 The Nature of the Problem

Thinking carefully reveals that **long prompts are essentially static code inclusion**.

You concatenate multiple parts (role definitions, process descriptions, methodology documents, style guides) together, ultimately executing a complete "source file." This is no different from `#include` in early programming languages or text concatenation.

This is the most primitive way of software modularization and reuse—it inevitably brings all the problems mentioned above.
## 2. Insights from Software Engineering

As software practitioners, we are no strangers to this problem. Software engineering has spent the past few decades solving similar modularity challenges.

### 2.1 The Evolution of Modularity

Looking back at the evolution of software modularity, we can see a clear development path:

**Stage 0: All code in one file**
- The most primitive approach, all logic written together
- Problem: difficult to understand, difficult to maintain, impossible to reuse

**Stage 1: Source code include/import (merge at compile time)**
- Code can be distributed across multiple files
- Merged into a single entity at compile/interpretation time
- Problem: all content ultimately still in one namespace, unclear boundaries, tight coupling

**Stage 2: Static linking libraries (compile independently, merge at link time)**
- Modules can be compiled independently
- Assembled into executable at link time
- Progress: concept of compilation units emerged, but still a single entity at runtime

**Stage 3: Dynamic linking libraries (load at runtime, independent lifecycle)**
- Modules are loaded dynamically at runtime
- Can be loaded on demand and released after use
- Key breakthrough: modules have independent lifecycles

**Stage 4: RPC/Web Services (independent processes, network communication)**
- Modules can run in different processes, on different machines
- Call each other's services through the network
- Further decoupling: physical isolation

**Stage 5: Microservices (independent deployment, loose coupling)**
- Each service is developed, deployed, and scaled independently
- Communicate through well-defined interfaces
- Maximum module autonomy

Each evolution addresses problems from the previous stage: **unclear boundaries, tight coupling, difficulty in reuse, difficulty in maintenance**.

### 2.2 Essential Characteristics of Modules

From this evolutionary history, we can summarize that a true module must have:

**Boundary**:
- Clear scope of responsibilities
- No confusion with other modules' responsibilities
- Exposes interfaces to the outside, hides internal implementation

**Lifecycle**:
- Independent creation, execution, and destruction process
- Can be started and terminated on demand
- Resources can be reclaimed and reused

**Interface**:
- Clear input and output definitions
- Callers don't need to understand internal implementation
- Collaborate through contracts rather than implementations

**Isolation**:
- Internal implementation is invisible from outside
- Modifying internal implementation doesn't affect other modules
- Resources (memory, context) don't leak or conflict

### 2.3 Comparison Table: Three Paradigms

Let's compare different stages of traditional programming, current prompt engineering, and the multi-agent systems we'll discuss:

| Dimension | Traditional Programming (Primitive) | Prompt Engineering (Current) | Multi-Agent Systems (Future) |
|------|----------------|-----------------|------------------|
| **Code Organization** | All code in one .c file | Long prompts concatenating multiple instructions | Independent agent modules |
| **Namespace** | Global variables | Global "constants" (outer parameters) | Module-private + parameter passing |
| **Lifecycle** | Program start to end | Single LLM call | Create/destroy agent instances on demand |
| **Context/Memory** | Shared global memory space | Shared context window | Each agent has independent context window |
| **Data Transfer** | Global variables + function parameters | Concatenated into prompt | Parameters + file pipelines |
| **Concurrent Execution** | Sequential execution | Not supported | Supports parallel scheduling |
| **Reuse Method** | Copy-paste code | Copy-paste text fragments | Call agent modules |
| **Impact Scope** | Modifying one place may affect globally | Modifying one section affects entire prompt | Internal module modifications don't affect external |

This comparison clearly shows: **Prompt engineering is currently stuck at "Stage 1" (source code include)**.

And software engineering experience tells us we need to evolve to "Stage 3+"—modules with truly independent lifecycles and clear boundaries.
## 3. Multi-Agent Systems (MAS)

Based on insights from software engineering, we need to introduce genuine modularization concepts to AI applications. This is what Multi-Agent Systems (MAS) are all about.

### 3.1 What is MAS

**A Multi-Agent System (MAS) is a modular system implemented using Large Language Models (LLMs).**

In MAS:
- Each module is called an "agent"
- Multiple agents collaborate to complete complex tasks
- Each agent possesses true modular characteristics: boundary, lifecycle, interface, and isolation

Compared to traditional software modules, the special features of agents are:
- They are defined using natural language (rather than programming languages)
- They can understand complex intentions and context
- They can autonomously decide execution strategies (rather than mechanically following instructions)
- They can use tools to complete tasks (such as search, file operations)

### 3.2 Core Conceptual Framework

To discuss MAS clearly, we need to establish a precise conceptual framework.

#### 3.2.1 Conceptual Hierarchy

From abstract to concrete, we have four levels of concepts:

```
[Abstract Layer] Module
    ↓ Implemented in AI domain as
[Implementation Layer] Agent
    ↓ Definition form
[Definition Layer] Agent Blueprint
    ↓ Runtime form
[Runtime Layer] Agent Instance
```

This hierarchical relationship is similar to the conceptual hierarchy in object-oriented programming: Interface → Class → Class Definition → Object Instance.

#### 3.2.2 Detailed Concept Definitions

Let's define these core concepts one by one:

**Module**

This is a general concept in software engineering:
- An independent unit with clear boundaries, lifecycle, and input/output
- Can be implemented using various technologies (functions, classes, libraries, services, containers, etc.)
- An abstract concept, not specific to any particular technology

**Agent**

An agent is a module implemented using LLMs. In addition to the characteristics of traditional modules, it also has:
- Understanding of natural language instructions (no need for precise programming syntax)
- Autonomous decision-making on execution strategies (flexibly adjusting methods based on circumstances)
- Use of tools to complete tasks (such as file operations, web search, data analysis)

**What is NOT an agent?** This is important:
- ❌ **Single LLM call**: Although it uses LLM, it lacks clear boundaries and lifecycle management
- ❌ **A section of a long prompt**: Although it is logically "a part," it lacks true isolation
- ❌ **Traditional API or function**: Although it is a module, it doesn't use LLM and cannot understand natural language intentions

**Agent Blueprint**

An agent blueprint is the "source code" of an agent. It is typically a Markdown document containing:
- **Role definition**: Who you are, what you're responsible for
- **Input specification**: What parameters and data you receive
- **Workflow**: How to complete the task (can be declarative, not imperative detailed steps)
- **Output specification**: What results you produce, where to write them
- **Quality standards**: How to self-check, what constitutes a good result

As an analogy to object-oriented programming, a blueprint is like a class definition.

An example of a simplified agent blueprint:

```markdown
# Information Collection Agent

## Your Role
You are a professional information collection assistant, responsible for gathering high-quality information on specific topics.

## Input
- Parameter: {TOPIC} - The topic to collect information on
- Parameter: {DEPTH} - Collection depth (broad/focused)

## Workflow
1. Understand the key concepts and scope of the topic
2. Search for relevant authoritative sources
3. Extract and organize key information
4. Evaluate information quality and reliability

## Output
- File path: data/materials/{TOPIC}.md
- Format: Markdown document with categorized information and source citations

## Quality Standards
- Information sources are reliable and diverse
- Covers major aspects of the topic
- Has clear source citations
```

**Agent Instance**

An agent instance is the runtime materialization of a blueprint:
- Has an independent context window (not shared with other instances)
- Executes specific tasks (with concrete parameters)
- Releases resources after execution is complete (context window is recycled)

As an analogy to object-oriented programming, an instance is an object. You can create multiple instances from the same blueprint, such as:
- Simultaneously creating 3 "information collection agent" instances to collect economic, political, and social information respectively
- Creating "analysis agent" instances in a loop to analyze multiple countries

**Parameters**

Parameters are data passed in when invoking an agent:
- Can be very short (such as country code "ARG", date "2024-10-15")
- Can also be relatively long (such as a problem description, a set of guiding principles)
- But not recommended to be very long (long data should be passed through files)

**Current limitation**: In existing runtime environments (such as Claude Code), typically only input parameters are supported, not explicit output parameters or return values. When an agent finishes execution, that's it—the caller cannot directly obtain a "return value."

So how do agents pass data between each other? The answer is files.

**File-based Pipeline**

File-based pipelines are the primary communication method between agents:
- One agent's output file = another agent's input file
- Data flow is coordinated through agreed-upon file paths

This approach has three major advantages:
- **Complete transparency**: Humans can directly read and review any intermediate products
- **Simple and direct**: No need for complex message queues or RPC configurations
- **Persistent**: Traceable and recoverable; if something goes wrong, you can restart from intermediate stages

For example:
```
[Collection Agent] → data/materials/economy.md
                         ↓
              [Analysis Agent] reads economy.md
                         ↓
              [Analysis Agent] → data/analysis/economic-assessment.md
```

**Reference Library**

A reference library is static storage for domain knowledge, with several important characteristics:

**Relatively static**:
- Doesn't change with each task
- Contains relatively stable knowledge (methodologies, theoretical frameworks, standards, etc.)

**Shared across agents**:
- Multiple agents can read the same reference library
- Avoids redundant knowledge definitions

**Configurable**:
- Modifying the reference library can change system behavior
- No need to modify agent blueprints themselves

**Content types**:
- Methodology documents (such as `dialectical-analysis-method.md`)
- Style guides (such as `academic-writing-style.md`)
- Theoretical frameworks (such as `marxist-epistemology.md`)
- Domain ontologies (such as `class-analysis-framework.md`)

**Distinction from other concepts**:
- Difference from **input files**: Input files are task-specific data (such as "raw materials on a certain country"), while reference libraries are general knowledge
- Difference from **agent blueprints**: Blueprints describe "what to do, how to do it," while reference libraries provide "what knowledge to use for doing it"

### 3.3 Key Advantages of MAS

After understanding these concepts, we can see the fundamental advantages of MAS compared to long prompts:

**Advantage 1: Breaking Through Context Limitations**

Each agent uses an independent context window:
- Agent A might have used 150K tokens and then releases them upon completion
- Agent B starts fresh with a full context budget again
- Theoretically can handle infinitely large tasks (as long as module division is reasonable)

This is like how dynamic link libraries can be loaded and unloaded on demand, rather than keeping all libraries resident in memory.

**Advantage 2: True Module Isolation**

Modifying one agent doesn't affect other agents:
- Improving contradiction analysis method: Only need to update the `dialectical-analysis-method.md` reference library
- Adjusting report format: Only need to modify the report generation agent's blueprint
- Adding a new analysis dimension: Add a new agent; existing agents need no modification

Each agent has clear boundaries and responsibilities, making them easy to test and optimize.

**Advantage 3: Supporting Complex Collaboration**

MAS supports various collaboration patterns:
- **Sequential execution**: Pipeline pattern, where one stage's output is the next stage's input
- **Parallel execution**: Multiple agents working simultaneously (such as collecting economic, political, and social information at the same time)
- **Iterative loops**: The orchestrator can invoke the same agent multiple rounds, checking quality each time
- **Dynamic decision-making**: The orchestrator decides what to execute next based on intermediate results

This is nearly impossible with long prompts.

**Advantage 4: Maintainability**

MAS systems have significant maintainability advantages:
- **Natural language definition**: Non-programmers can also understand and maintain agent blueprints
- **Configuration-driven**: Modifying reference libraries can adjust behavior without changing "code"
- **Complete audit trail**: A byproduct of file-based pipelines—all intermediate steps are visible
- **Progressive optimization**: Can optimize a single agent individually and see results immediately
## 4. Runtime Environment

Once we have the concepts of MAS, the next question is: where do we run it?

### 4.1 Core Requirements for MAS Runtime

A complete MAS runtime environment needs to support four core capabilities:

**1. Independent Context Window Management**
- Ability to create new context windows (start new agent instances)
- Release resources after execution completes (recycle context windows)
- Multiple instances do not share contexts

**2. File System Operations**
- Read input files and reference libraries
- Write output files
- Create and manage directory structures
- File path operations (relative paths, absolute paths)

**3. Parallel Task Scheduling**
- Run multiple agent instances simultaneously
- Automatically manage concurrency and resources
- Wait for all parallel tasks to complete before continuing

**4. Parameter Passing Mechanism**
- Pass runtime parameters to agents
- Support variable substitution (e.g., `{TOPIC}`, `{COUNTRY_CODE}`)
- Parameters can be simple values or longer text

### 4.2 Capability Levels of Different Environments

Let's compare several common runtime environments:

| Environment Type | Context Isolation | File Operations | Parallel Scheduling | Parameter Passing | Overall Assessment |
|---------|----------|---------|---------|---------|---------|
| **Web Interface**<br>(ChatGPT/Gemini) | ❌ Manual new session required | ❌ Manual copy-paste needed | ❌ No parallelization | ✅ In prompts | Inefficient but viable |
| **Claude Code** | ✅ Native Subagent support | ✅ Bash tools | ✅ Automatic parallel Tasks | ✅ Parameter substitution | Most convenient |
| **Programming Frameworks**<br>(AutoGen/LangGraph) | ✅ Code-controlled | ✅ Code-controlled | ✅ Code-controlled | ✅ Code-controlled | Full-featured, requires programming |
| **Custom Systems** | ✅ Fully controllable | ✅ Fully controllable | ✅ Fully controllable | ✅ Fully controllable | Most flexible, high development cost |

**Web Interface Limitations**:
- You need to manually open new sessions in ChatGPT/Gemini (to simulate "new context windows")
- Need to manually copy-paste file contents between sessions for data transfer
- Cannot be automated, cannot parallelize
- Theoretically viable, but extremely inefficient

**Claude Code's Convenience**:
- Subagent capability: Can launch sub-agents with automatically managed independent contexts
- Bash tools: Can read/write files and manipulate directories
- Task parallelization: Can run multiple Tasks simultaneously with automatic completion waiting
- Parameter passing: Variable substitution in prompts
- This makes Claude Code an ideal environment for rapid prototyping and experimentation

**Programming Framework Functionality**:
- AutoGen, LangGraph, CrewAI, and other frameworks provide complete MAS capabilities
- Requires writing Python code to define and orchestrate agents
- Suitable for scenarios requiring complex logic control, version management, and team collaboration
- Steeper learning curve, but fully featured

**Custom System Flexibility**:
- Can be completely customized as needed
- Can integrate with internal enterprise systems
- Full control over security, cost, and performance
- Highest development cost, but potentially better for long-term maintenance

### 4.3 Why Now? The Tipping Point of Technological Maturity

The concept of multi-agent systems is not new (academia has had frameworks like JADE for years), but why is MAS becoming practical only now? Because multiple technologies have matured simultaneously:

**LLM Capability Breakthrough**:
- Models like Claude 3.5 Sonnet and GPT-4 can understand complex agent blueprints
- Can understand collaborative relationships and data dependencies
- Can autonomously decide execution strategies rather than mechanically following instructions

**Long Context Windows**:
- 200K token context windows allow individual agents to handle quite complex tasks
- Can read large amounts of reference materials and input data at once
- Reduces pressure on module division

**Tool-Use Capabilities**:
- Function calling allows LLMs to manipulate file systems
- Can call search engines, APIs, and databases
- Evolution from "conversation partner" to "actor"

**Cost Reduction**:
- Token prices have dropped to levels allowing large-scale operation of complex systems
- A MAS task involving dozens of agent invocations can cost just a few dollars
- Transforms MAS from a laboratory concept to a practical tool

These factors working together have transformed MAS from a theoretical concept to a practical technology that can be used daily.

### 4.4 Selection Recommendations

Based on different scenarios, my recommendations are:

**Exploration Phase**:
- Use Claude Code for rapid prototype validation
- Can build a runnable MAS in a few hours
- Suitable for proof of concept and feasibility exploration

**Personal Projects**:
- If you're familiar with programming: consider AutoGen or LangGraph frameworks
- If you're not familiar with programming: continue using Claude Code
- The key is rapid iteration and learning

**Team Collaboration**:
- Consider programming frameworks or custom systems
- Facilitates version control (Git), code review, and continuous integration
- Can establish team best practices and pattern libraries

**Production Environment**:
- Custom system with full control over security, cost, and performance
- Can integrate enterprise authentication, audit logs, etc.
- Can be optimized for specific scenarios
## 5. Case Study: A Multi-Agent System for Regional Research

Concepts, no matter how clear, need concrete examples to aid understanding. Let's examine an actual MAS application: a multi-agent system for regional country research.

### 5.1 Task Background

**Research Objective**:
Conduct a comprehensive analysis of a country's economic, political, and social conditions during a specific period, generating a structured research report.

**Complexity Analysis**:
- Requires collecting vast amounts of information: news reports, academic literature, statistical data, historical background, etc.
- Requires applying multiple analytical frameworks: class analysis, contradiction analysis, economic assessment, etc.
- Requires generating a structured research report that conforms to specific styles and formats
- The volume of information and task complexity far exceeds what a single LLM call can handle

**If using a long prompt**:
You would need to prepare an ultra-long prompt of approximately 30,000-50,000 words, containing instructions for all steps and all reference materials. Even then, you would face all the problems we discussed earlier: attention dilution, lack of isolation, inability to parallelize, rigid workflows, and maintenance difficulties.

**Implementing with MAS**:
We break down this complex task into a three-phase pipeline, accomplished collaboratively by 7 specialized agents.

### 5.2 System Architecture

#### Three-Phase Pipeline

The entire system follows a clear pipeline architecture:

```
Phase 1: Data Collection     Phase 2: Analysis          Phase 3: Report Generation
     ↓                           ↓                           ↓
data/01.materials/        data/02.analysis/         data/03.reports/
```

The output of each phase becomes the input for the next, with data passed through the file system.

#### Agent Role Distribution

Let's examine each agent's responsibilities in detail:

**0. orchestrator (Orchestrator)**

This is a special agent responsible for coordinating the entire research workflow.

- **Responsibilities**: Understand user requirements, formulate execution plans, call agents sequentially, monitor progress
- **Input**:
  - User-specified country code (e.g., "ARG" for Argentina)
  - Research dimensions (economy, politics, society, etc.)
  - Analytical framework (e.g., "dialectical-materialism")
- **Workflow**:
  1. Read user requirements document (`user_input.md`)
  2. Read all reference libraries, understand methodologies and standards
  3. Create directory structure (`data/01.materials/`, `data/02.analysis/`, etc.)
  4. Sequentially call agents in Phase 1, Phase 2, and Phase 3
  5. Check output quality for each phase
  6. If needed, can loop calls to an agent (e.g., multiple rounds of information collection)
- **Output**: No direct output (it is a coordinator, not a content producer)

**Phase 1: Data Collection Agents**

This phase is responsible for collecting raw information.

**1.1 broad-reconnaissance (Broad Reconnaissance)**
- **Responsibilities**: Rapidly collect basic information and major events about the country, establish an information map
- **Input**:
  - Parameter: country code (e.g., "ARG")
- **Workflow**:
  1. Search for important news and events in the country for the recent period (e.g., past year)
  2. Identify key themes and focal issues (e.g., "economic crisis," "political turmoil," "social movements")
  3. Generate an information map marking the importance and information density of each theme
- **Output**:
  - `data/01.materials/overview.md`: Overview document containing topic list and preliminary information

**1.2 focused-collection (Focused Collection)**
- **Responsibilities**: Collect in-depth information on identified key themes
- **Input**:
  - Parameter: country code
  - File: `data/01.materials/overview.md` (output from previous step)
- **Workflow**:
  1. Read overview, identify themes requiring deep investigation
  2. Conduct deep information collection for each theme (search academic literature, statistical data, in-depth reports)
  3. Organize materials by theme, annotate information sources and reliability
- **Output**:
  - `data/01.materials/topic-economy.md`
  - `data/01.materials/topic-politics.md`
  - `data/01.materials/topic-society.md`
  - (Possibly more, depending on number of discovered themes)

**Note**: In actual execution, the orchestrator can simultaneously launch 3-5 focused-collection instances, each responsible for different thematic domains (economy, politics, society, international relations, etc.), achieving parallel collection. This is something long prompts cannot do.

**Phase 2: Analysis Agents**

This phase applies different analytical frameworks to process the collected materials.

**2.1 contradiction-analyzer (Contradiction Analyzer)**
- **Responsibilities**: Apply dialectics to identify primary and secondary social contradictions
- **Input**:
  - Parameter: analytical framework ("dialectical-materialism")
  - Files: `data/01.materials/*.md` (all collected materials)
  - Reference library: `references/dialectical-analysis-method.md` (dialectical analysis methodology, approximately 5000 words)
- **Workflow**:
  1. Read reference library, understand dialectical analysis methods and standards
  2. Read all collected materials
  3. Identify primary contradictions in society (e.g., class contradictions, national contradictions, etc.)
  4. Determine primary-secondary relationships and development trends
- **Output**:
  - `data/02.analysis/contradictions.md`: Contradiction analysis report

**2.2 class-analyzer (Class Analyzer)**
- **Responsibilities**: Analyze class composition and class struggle dynamics
- **Input**:
  - Files: `data/01.materials/*.md`
  - Reference library: `references/class-analysis-framework.md` (class analysis paradigm, approximately 8000 words)
- **Workflow**:
  1. Identify major classes and strata (bourgeoisie, proletariat, petty bourgeoisie, etc.)
  2. Analyze each class's economic base, political positions, ideology
  3. Assess class power balance and struggle dynamics
- **Output**:
  - `data/02.analysis/class-structure.md`: Class analysis report

**2.3 economic-evaluator (Economic Evaluator)**
- **Responsibilities**: Assess economic conditions and development trends
- **Input**:
  - Files: `data/01.materials/*.md` (especially focusing on economic themes)
- **Workflow**:
  1. Extract economic data and indicators (GDP, inflation rate, unemployment rate, trade data, etc.)
  2. Analyze economic structure and problems (industrial structure, debt situation, dependency relations, etc.)
  3. Forecast development trends and potential crises
- **Output**:
  - `data/02.analysis/economic-assessment.md`: Economic assessment report

**Important**: The three agents in Phase 2 can **execute in parallel** because they are mutually independent, all reading Phase 1 materials and producing independent analysis reports.

**Phase 3: Report Generation**

The final phase synthesizes all analyses into the final report.

**3.1 report-synthesizer (Report Synthesizer)**
- **Responsibilities**: Synthesize all analyses into a structured, stylistically unified final report
- **Input**:
  - Files: `data/02.analysis/*.md` (all analysis results)
  - Reference libraries:
    - `references/report-template.md` (report template, approximately 2000 words)
    - `references/style-guide.md` (writing style guide, approximately 1500 words)
- **Workflow**:
  1. Read all analysis results, understand findings from each dimension
  2. Organize content according to report template (summary, background, analysis, conclusions, etc.)
  3. Synthesize connections between different analyses (e.g., how economic base influences class struggle)
  4. Apply style guide for polishing, ensure terminology consistency and logical clarity
  5. Generate final report
- **Output**:
  - `data/03.reports/final-report.md`: Complete research report

### 5.3 Manifestation of Module Boundaries

This system perfectly embodies the four key characteristics of modularity:

**Boundary Isolation**:
- `focused-collection` only collects materials, doesn't need to know what analysis follows
- `contradiction-analyzer` focuses solely on contradiction analysis, unaware of what other analyzers are doing
- Modifications to each module don't affect each other: improving class analysis methods won't affect contradiction analysis

**Independent Lifecycle**:
- After `broad-reconnaissance` completes, its context window is immediately released
- Even if it processed 100K tokens of information, it doesn't affect subsequent agents' context budgets
- Each agent is created on-demand, destroyed after use

**Clear Interfaces**:
- Each agent clearly knows:
  - **Where input comes from**: parameters (e.g., country code), file paths (e.g., `overview.md`), reference libraries (e.g., `class-analysis-framework.md`)
  - **Where output goes**: specific file paths (e.g., `data/02.analysis/contradictions.md`)
  - **What its responsibilities are**: role definition is clear, stays within boundaries
- The caller (orchestrator) only needs to know the interface, not internal implementation

**Transparent Traceability**:
- All intermediate products are saved as files, humans can inspect at any time
- Can see what themes `overview.md` identified
- Can see what information `topic-economy.md` collected
- Can see the quality of analysis in `contradictions.md`
- If problems occur, can restart from any intermediate stage without running from the beginning

### 5.4 Comparison with Long Prompts

Let's explicitly compare the differences between implementing the same task with long prompts versus MAS.

**If implementing the same task with a long prompt**:

You would need to concatenate all instructions and reference materials into one complete prompt:

```
Long Prompt (approximately 30,000-50,000 words):

[Role Definition & Overall Requirements] (500 words)
You are a regional research expert who needs to complete the following tasks...

[Step 1: Broad Reconnaissance] (800 words)
First, quickly scan recent important information about the country, identify key themes...

[Step 2: Focused Collection] (1000 words)
Based on key themes discovered in step one, collect detailed information for each theme...

[Step 3: Contradiction Analysis] (1200 words)
Apply dialectics to analyze primary and secondary social contradictions...

[Step 4: Class Analysis] (1000 words)
Identify major class composition and power balance...

[Step 5: Economic Assessment] (800 words)
Extract economic data and assess development trends...

[Step 6: Report Synthesis] (1000 words)
Integrate all analyses into final report...

[Attachment 1: Marxist Epistemology Framework] (10000 words)
[Attachment 2: Dialectical Analysis Method] (5000 words)
[Attachment 3: Class Analysis Paradigm] (8000 words)
[Attachment 4: Report Template] (2000 words)
[Attachment 5: Writing Style Guide] (1500 words)

Total: approximately 32000 words
```

**The problems are**:

1. **Attention Dilution**: Although not exceeding the context window, the LLM needs to simultaneously "remember" requirements for 6 steps. When executing step 5, details from step 1 may already be blurred.

2. **Lack of Isolation**: Modifying the dialectical analysis method (Attachment 2) might inadvertently affect class analysis execution—because all content is in one context, the LLM may produce unexpected "crosstalk."

3. **Cannot Parallelize**: Must execute all 6 steps sequentially, even though contradiction analysis, class analysis, and economic assessment could actually proceed simultaneously.

4. **Rigid Workflow**: Want to loop "focused collection" for three rounds, evaluating effectiveness after each round and filling gaps? Nearly impossible to implement in a long prompt—you cannot make the LLM "pause," check intermediate results, and "continue."

5. **Maintenance Difficulties**: Want to adjust the style guide? Need to reload the entire 30,000-word prompt; want to add "international relations analysis"? The entire prompt becomes longer, complexity increases exponentially.

**Implementing with MAS**:

The system is split into 7 independent agents:
- Each agent blueprint: 500-1200 words (concise and clear)
- Each agent at runtime only loads reference libraries it needs (1-2 documents, totaling around 10,000 words)
- **Parallel Execution**: Can simultaneously launch 3-5 agents to collect information for different problem domains (e.g., economy, politics, society) without conflict; Phase 2's three analyzers can also run in parallel, saving significant time
- **Iterative Loops**: Orchestrator can call focused-collection for three rounds, checking collection quality each round, dynamically deciding whether to continue
- **Independent Maintenance**: Modifying dialectical analysis method only requires updating the `dialectical-analysis-method.md` reference library, doesn't affect other agents; adding "international relations analysis" only requires adding a new agent
- **Transparent Control**: Output from each stage is visible, can be manually reviewed, can restart from any stage

**Key Difference Summary**:

| Dimension | Long Prompt Solution | MAS Solution |
|-----------|---------------------|--------------|
| **Context Usage** | 30K words loaded at once, one context window used throughout | 7 separate loads, each a few hundred to 10K words, each agent released after use |
| **Parallel Capability** | Not supported | Phase 1 can collect 3-5 themes in parallel, Phase 2 can run 3 analyzers in parallel |
| **Workflow Flexibility** | Rigid, cannot iterate loops | Can loop calls, make dynamic decisions |
| **Maintenance Cost** | Modifying any part requires reloading everything | Only need to modify relevant agent or reference library |
| **Transparency** | Can only see final output | All intermediate steps visible, reviewable |
| **Extensibility** | Adding features means longer prompts | Add new agents, existing agents need no modification |
## 6. From Modules to Design Principles

By this point, we have established a complete conceptual framework for MAS and examined a concrete example. But this is only the beginning.

### 6.1 Elevating the Discussion

With the MAS conceptual framework in place, our discussion of AI applications is no longer about:
- ❌ "How to write more effective prompts?"
- ❌ "How to make the LLM understand my intent?"
- ❌ "How to prevent the LLM from going off-topic?"

Instead, it upgrades to:
- ✅ "Does this agent have a single, well-defined responsibility?"
- ✅ "Is the coupling between modules reasonable?"
- ✅ "Is the interface design clear?"
- ✅ "Is the system easy to extend and maintain?"
- ✅ "How do we balance module granularity against communication costs?"

This is **design-level discussion**, not **technique-level debugging**.

Just as software engineering evolved from "how to write code" to "how to design systems," MAS elevates us from "how to write prompts" to "how to design agent systems."

### 6.2 Applicability of Software Engineering Design Principles

Since MAS is a modular system, classic software design principles can be applied. Let's briefly examine a few core principles:

**Single Responsibility Principle (SRP)**

An agent should have only one well-defined responsibility, only one reason to change.

- **Anti-pattern**: An agent that collects data, performs analysis, and generates reports
  - Mixed responsibilities, hard to reuse
  - Whenever you want to improve the analysis method, the entire agent needs modification

- **Good pattern**: Collector only collects, analyzer only analyzes, synthesizer only synthesizes
  - Each agent has clear responsibilities
  - Can be independently optimized and tested

**Open-Closed Principle (OCP)**

Agents should be open for extension, closed for modification.

- **Implementation**: Change behavior through reference library configuration, not by modifying blueprints
- **Examples**:
  - Want to change the analysis method? Modify the `analysis-method.md` reference library, agent blueprint stays unchanged
  - Want to add a new analysis dimension? Add a new analyzer agent, existing agents stay unchanged

**Dependency Inversion Principle (DIP)**

Agents should depend on abstract interfaces, not concrete implementations.

- **Example**: Analyzer depends on the abstract concept of "analysis method" (through reference library), rather than hard-coding a specific method
- **Benefit**: Can switch analysis methods without modifying the agent

**Law of Demeter (LoD)**

Agents should only communicate with direct collaborators, not need to understand the global system structure.

- **Example**: Focused-collection only needs to know "read overview.md, output topic-*.md," doesn't need to know what analyzers come next
- **Benefit**: Reduces coupling, improves system flexibility

**Composite Reuse Principle (CRP)**

Prioritize implementing complex functionality through agent composition, rather than trying to write an "omnipotent" agent.

- **Example**: Don't write an "omnipotent analyzer," instead compose contradiction-analyzer, class-analyzer, and economic-evaluator as specialized analyzers
- **Benefit**: Each agent stays simple, system stays flexible

### 6.3 Next Steps: Deep Dive into Design Principles

This brief introduction to these principles is just an appetizer. In subsequent articles, we will discuss in detail:

- **How to apply these principles to agent design**
  - Detailed explanations and examples of each principle
  - How to identify designs that violate principles
  - How to refactor to comply with principles

- **Common patterns in agent design**
  - Orchestrator pattern
  - Pipeline pattern
  - Parallel Execution pattern
  - Iterative Refinement pattern
  - Specialist Collaboration pattern

- **How to evaluate the quality of an MAS design**
  - Module cohesion metrics
  - Module coupling metrics
  - Testability assessment
  - Maintainability assessment

- **Trade-offs and challenges in MAS design**
  - Choosing module granularity: too coarse or too fine?
  - Communication costs vs. isolation benefits
  - Debugging and monitoring strategies
  - Error handling and recovery mechanisms

Our goal is to evolve from "knowing how to use MAS" to "designing excellent MAS."

---

## Appendix: Key Terminology Reference Table

| Chinese | English | Description |
|-----|------|------|
| 多智能体系统 | Multi-Agent System (MAS) | A system of multiple collaborating agents |
| 智能体 | Agent | A module implemented with LLM |
| 智能体蓝图 | Agent Blueprint | The definition document of an agent (source code) |
| 智能体实例 | Agent Instance | A running agent (object instance) |
| 编排者 | Orchestrator | A special agent that coordinates other agents |
| 文件管道 | File-based Pipeline | A method of passing data through the file system |
| 参考库 | Reference Library | Shared domain knowledge documents |
| 上下文窗口 | Context Window | The number of tokens an LLM can process at once |
| 模块 | Module | A general concept in software engineering |
| 边界 | Boundary | The scope of a module's responsibilities |
| 生命周期 | Lifecycle | The process of creation, execution, and destruction |
| 接口 | Interface | The definition of inputs and outputs |
| 隔离 | Isolation | The property of modules not interfering with each other |

---

## Conclusion

Starting from the dilemma of long prompts, we've seen the inspiration from software engineering modularity, established the conceptual framework for multi-agent systems, explored runtime environment requirements, understood how MAS operates through a concrete example, and finally pointed toward the next direction of design principles.

Multi-agent systems may herald a new form of software in the AI era:
- Not traditional "writing code," but "designing agents"
- Not "compile and execute," but "orchestrate and collaborate"
- Not "function calls," but "module dialogues"
- But fundamentally, it's still software engineering—just expressed in natural language rather than programming languages

For software practitioners, this is an exciting turning point. The software engineering knowledge we've accumulated—modularity, design principles, architectural patterns—hasn't become obsolete; rather, it has found new application scenarios.

MAS is not a disruption of software engineering, but an inheritance and evolution.

(End of Article)

---

**About This Article**

This article is part of the "AgentForge" project. AgentForge is a meta-generator for multi-agent systems that can automatically generate customized MAS based on user requirements.

Related resources:
- Project repository: [to be added]
- PLOP paper (Pattern Language Of Prompts): See `doc/references/plop_paper v4.0.md`
- Upcoming articles: Detailed explanation of MAS design principles (to be published)

Discussion and feedback are welcome.
