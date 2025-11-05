# Multi-Agent Systems: Software Modularity in the AI Era

> From the Dilemma of Long Prompts to the Modular Design of Agents

## 1. The Dilemma of Long Prompts

When we begin to use Large Language Models (LLMs) intensively for complex tasks, we quickly encounter a seemingly paradoxical phenomenon: prompt engineering techniques proliferate and prompts themselves grow longer, yet the results do not always improve proportionally.

### 1.1 The Evolution of Prompt Engineering

Prompt engineering has rapidly evolved as an emerging practice over the past few years. We've learned to use Problem Orientation—stating the problem to be solved before giving specific instructions; Epistemology Frame—explicitly specifying analytical perspectives and theoretical frameworks; Exhaustive Input—providing sufficient background information and context; Prescribed Process—breaking down task execution into step-by-step instructions; Structured Output—precisely defining output formats; and Style Mimicry—providing examples for the LLM to learn specific styles. These techniques are indeed effective, but they also mean prompts are becoming increasingly lengthy.

From a few initial sentences to hundreds of words of detailed instructions, then to thousands of words of complex prompts. When we tackle genuinely complex knowledge work—such as writing research reports or conducting multi-dimensional analyses—prompts can easily reach tens of thousands of words. Going further, we've even developed the Attachment pattern: uploading numerous documents as part of the prompt. These documents might include methodology descriptions (such as dialectical analysis methods, tens of thousands of words), theoretical frameworks (such as Marxist epistemology, tens of thousands of words), style guides (such as academic writing standards, thousands of words), and various reference materials. Essentially, these "attachments" are all components of an extremely long prompt. In some cases, the complete prompt can reach 30,000-50,000 words.

### 1.2 Three Major Problems with Long Prompts

As a programmer, I quickly realized that the problems brought by long prompts are structural.

The first problem is attention diffusion. Even without exceeding context window limits, when prompts contain numerous and detailed instructions, LLMs struggle to execute all requirements perfectly. Much like humans reading a lengthy document, LLMs experience attention dilution and overlook certain details, autonomously simplify instructions and execute according to their own understanding, and lose prioritization among multiple objectives. The result is unstable output quality, making it difficult to achieve the perfection that long prompts aspire to.

The second problem is the lack of module isolation. You might think you've achieved "module division" in your prompt—for example, "step one does this, step two does that." But in reality, all content is loaded into the LLM at once. This means: "pulling one hair moves the whole body"—modifying the contradiction analysis method might inadvertently affect class analysis execution; there are no true boundaries, with all modules influencing each other within the same context; isolation cannot be achieved, and coupling between different parts is uncontrollable.

It's like writing all code in one giant function—although you've divided it into paragraphs with comments, it's fundamentally still a monolith.

The third problem is maintenance difficulty. Long prompts make flexible parameter passing and process control nearly impossible. Parameter passing is impossible: you can only set some "global constants" at the outermost layer (such as "analyze country XXX"); it's nearly impossible to generate variables from one module and use these variables to invoke other modules. Dynamic process control is difficult: want the "information collection" to loop three rounds, evaluating effectiveness and filling gaps after each round? Nearly impossible in long prompts—you cannot have the LLM "pause," check intermediate results, and then "continue." High modification cost: if you want to adjust the style guide, you need to reload the entire 30,000-word prompt; if you want to add a new analytical dimension, the entire prompt becomes longer and complexity rises exponentially.

### 1.3 The Essence of the Problem

Careful consideration reveals that long prompts are essentially static code includes. You concatenate multiple parts (role definitions, process descriptions, methodology documents, style guides) together, and what executes is one complete "source file." This is no different in essence from `#include` or text concatenation in early programming languages. This is the most primitive form of software modularity and reuse—it inevitably brings all the problems mentioned above.

## 2. Insights from Software Engineering

As software practitioners, we are not unfamiliar with this problem. Software engineering over the past several decades has addressed precisely this kind of modularity problem.

### 2.1 The Evolution of Modularity

Reviewing the evolution of software modularity reveals a clear developmental path:
- Stage 0 is all code in one file, the most primitive approach where all logic is written together; the problem is difficulty in understanding, difficulty in maintenance, and inability to reuse.
- Stage 1 is source code include/import (merge at compile time), allowing code to be distributed across multiple files, merged into a whole at compile or interpretation time; the problem is all content ultimately still resides in one namespace, with unclear boundaries and tight coupling.
- Stage 2 is static linking libraries (independent compilation, merge at link time), where modules can be independently compiled and then assembled into an executable at link time; the advance is the concept of compilation units, but at runtime it's still a monolith.
- Stage 3 is dynamic linking libraries (runtime loading, independent lifecycle), where modules are dynamically loaded at runtime, can be loaded on demand and released when finished; the key breakthrough is modules having independent lifecycles.
- Stage 4 is RPC/Web Services (independent processes, network communication), where modules can run in different processes on different machines, invoking each other's services through the network, further achieving physical isolation and decoupling.
- Stage 5 is microservices (independent deployment, loose coupling), where each service is independently developed, deployed, and scaled, communicating through well-defined interfaces, achieving maximum module autonomy.

Each evolution addresses problems from the previous stage: unclear boundaries, tight coupling, difficulty in reuse, difficulty in maintenance.

### 2.2 Essential Characteristics of Modules

From this evolutionary journey, we can summarize that a true module must possess four characteristics.
- **Boundary** means a clear scope of responsibility, not confused with other modules' responsibilities, exposing interfaces while hiding internal implementation.
- **Lifecycle** means an independent process of creation, execution, and destruction, can be started and terminated on demand, resources can be reclaimed and reused.
- **Interface** means clear input-output definitions, callers don't need to understand internal implementation, collaboration through contracts rather than implementation.
- **Isolation** means internal implementation is invisible externally, modifying internal implementation doesn't affect other modules, resources (memory, context) don't leak or conflict.

### 2.3 Comparison Table: Three Paradigms Compared

Let's compare different stages of traditional programming, current prompt engineering, and the multi-agent systems we'll discuss:

| Dimension | Traditional Programming (Primitive) | Prompt Engineering (Current) | Multi-Agent Systems (Future) |
|-----------|-----------------------------------|------------------------------|------------------------------|
| **Code Organization** | All code in one .c file | Long prompts concatenating multiple instruction segments | Independent agent modules |
| **Namespace** | Global variables | Global "constants" (outer parameters) | Module-private + parameter passing |
| **Lifecycle** | Program start to end | Single LLM invocation | On-demand agent instance creation/destruction |
| **Context/Memory** | Shared global memory space | Shared single context window | Each agent independent context window |
| **Data Transfer** | Global variables + function parameters | Concatenated into prompts | Parameters + file pipelines |
| **Concurrent Execution** | Sequential execution | Not supported | Supports parallel scheduling |
| **Reuse Method** | Copy-paste code | Copy-paste text fragments | Invoke agent modules |
| **Impact Scope** | Modifying one place may affect globally | Modifying one segment affects entire prompt | Internal module modifications don't affect externally |

This comparison clearly shows: prompt engineering currently remains at "Stage 1" (source code include). Software engineering experience tells us we need to evolve to "Stage 3+"—true modules with independent lifecycles and clear boundaries.

## 3. Multi-Agent Systems (MAS)

Based on insights from software engineering, we need to introduce true modularity concepts for AI applications. This is the Multi-Agent System (MAS).

### 3.1 What is MAS

Multi-Agent System (MAS) is a modular system implemented using Large Language Models (LLMs). In MAS, each module is called an "Agent," multiple agents collaborate to complete complex tasks, each agent possesses true module characteristics: clear boundaries, independent lifecycles, clear input-output interfaces, mutually isolated runtime contexts.

Compared to traditional software modules, the special aspect of agents is that they are defined in natural language (rather than programming languages), can understand complex intentions and contexts, can autonomously decide execution strategies (rather than mechanically executing instructions), can use tools to complete tasks (such as search, reading/writing files).

### 3.2 Core Conceptual Framework

To clearly discuss MAS, we need to establish a precise conceptual framework.

**Module** is a general concept in software engineering, an independent unit with clear boundaries, lifecycle, and input-output, can be implemented with various technologies (functions, classes, libraries, services, containers, etc.), is an abstract concept not specific to any technology.

**Agent** is a module implemented using LLM. In addition to traditional module characteristics, it also possesses the ability to understand natural language instructions (doesn't require precise programming syntax), autonomously decide execution strategies (flexibly adjust methods based on circumstances), use tools to complete tasks (such as file operations, web search, data analysis). It must be clarified that a single LLM invocation is not an agent (although it uses LLM, it lacks clear boundaries and lifecycle management), a paragraph in a long prompt is not an agent (although it's logically "a part," it lacks true isolation), traditional APIs or functions are not agents (although they are modules, they don't use LLM and cannot understand natural language intentions).

**Agent Blueprint** is the "source code" of an agent, typically a Markdown document containing role definition (who you are and what you're responsible for), input specification (what parameters and data to receive), workflow (how to complete the task, can be declarative rather than imperative detailed steps), output specification (what results to produce and where to write them), quality standards (how to self-check and what constitutes good results). By analogy to object-oriented programming, the blueprint is the class definition.

**Agent Instance** is the runtime instantiation of a blueprint, possessing an independent context window (not shared with other instances), executing specific tasks (with concrete parameters), releasing resources upon completion (context window reclaimed). By analogy to object-oriented programming, the instance is the object. You can create multiple instances from the same blueprint, such as simultaneously creating 3 "information collection agent" instances to separately collect economic, political, and social information, or iteratively creating "analysis agent" instances to analyze multiple countries.

**Parameters** are data passed when invoking an agent, can be quite short (such as country code "ARG," date "2024-10-15"), can also be relatively long (such as a problem description, a set of guiding principles), but should not be especially long (long data should be passed through files). Note that in existing runtime environments (such as Claude Code), typically only input parameters are supported, explicit output parameters or return values are not supported. When an agent finishes executing, it's simply finished; the caller cannot directly obtain a "return value." So how do agents transfer data between each other? The answer is files.

**File-based Pipeline** is the primary communication method between agents: one agent's output file is another agent's input file, coordinating data flow through agreed-upon file paths. This approach has three major advantages: complete transparency (humans can directly read and review any intermediate products), simple and straightforward (doesn't require complex message queues or RPC configurations), persistent (traceable, recoverable, can restart from intermediate stages if problems occur).

**Reference Library** is static storage of domain knowledge. It is relatively static, doesn't change with each task, is relatively stable knowledge (methodologies, theoretical frameworks, standards, etc.). It is shared across agents, multiple agents can read the same reference library, avoiding duplication of knowledge definitions. It is configurable, modifying the reference library can change system behavior without modifying agent blueprints themselves. Its content types include methodology documents (such as `dialectical-analysis-method.md`), style guides (such as `academic-writing-style.md`), theoretical frameworks (such as `marxist-epistemology.md`), domain ontologies (such as `class-analysis-framework.md`). It needs to be distinguished that input files are task-specific data (such as "raw materials for a certain country"), while reference libraries are general knowledge; agent blueprints describe "what to do and how to do it," while reference libraries provide "what knowledge to use in doing it."

### 3.3 Key Advantages of MAS

Having understood these concepts, we can see the fundamental advantages of MAS compared to long prompts.

First is breaking through context limitations. Each agent uses an independent context window: Agent A might use 150,000 tokens, execute and release, Agent B starts fresh again with a complete context budget, theoretically can handle infinitely large tasks (as long as module division is reasonable). This is like dynamic link libraries that can be loaded and unloaded on demand, rather than keeping all libraries resident in memory.

Second is true module isolation. Modifying one agent doesn't affect other agents: improving contradiction analysis methods only requires updating the `dialectical-analysis-method.md` reference library, adjusting report format only requires modifying the report generation agent's blueprint, adding new analytical dimensions only requires adding a new agent while existing agents need no modification. Each agent has clear boundaries and responsibilities, easy to test and optimize.

Third is support for complex collaboration. MAS supports various collaboration modes: sequential execution (pipeline mode, one stage's output is the next stage's input), parallel execution (multiple agents working simultaneously, such as simultaneously collecting economic, political, and social information), iterative loops (orchestrator can invoke the same agent multiple rounds, checking quality each round), dynamic decision-making (orchestrator decides what to execute next based on intermediate results). This is nearly impossible with long prompts.

Fourth is maintainability. MAS systems have significant maintainability advantages: natural language definitions allow non-programmers to understand and maintain agent blueprints, configuration-driven allows modifying reference libraries to adjust behavior without changing "code," complete audit trail is a byproduct of file pipelines with all intermediate steps visible, progressive optimization can individually optimize a certain agent and immediately see effects.

## 4. Runtime Environment

Having established the concept of MAS, the next question is: where does it run?

### 4.1 Core Requirements for MAS Runtime

A complete MAS runtime environment needs to support four core capabilities:
1. Independent context window management: able to create new context windows (start new agent instances), release resources upon completion (reclaim context windows), multiple instances don't share context.
2. File system operations: read input files and reference libraries, write output files, create and manage directory structures, perform file path operations (relative paths, absolute paths).
3. Parallel task scheduling: run multiple agent instances simultaneously, automatically manage concurrency and resources, wait for all parallel tasks to complete before continuing.
4. Parameter passing mechanism: pass runtime parameters to agents, support variable substitution (such as `{TOPIC}`, `{COUNTRY_CODE}`), parameters can be simple values or relatively long text.

And all four of these capabilities require the large model behind the runtime environment (such as Claude Sonnet) to flexibly schedule based on specific, clear (but not rigid) requirements.

### 4.2 Capability Levels of Different Environments

Let's compare several common runtime environments:

| Environment Type | Context Isolation | File Operations | Parallel Scheduling | Parameter Passing | Overall Assessment |
|-----------------|-------------------|-----------------|---------------------|-------------------|-------------------|
| **Web Interface**<br>(ChatGPT/Gemini) | Manual new session needed | Manual copy-paste needed | Cannot parallel | Available in prompts | Inefficient but feasible |
| **Claude Code** | Subagent native support | Bash tools | Automatic parallel Tasks | Parameter substitution | Most convenient |
| **Programming Frameworks**<br>(AutoGen/LangGraph) | Code control | Code control | Code control | Code control | Full-featured, requires programming |

Web interface limitations are that you need to manually open new sessions in ChatGPT/Gemini (simulating "new context windows"), need to manually copy-paste file content to transfer data between sessions, cannot automate or parallel, but theoretically feasible just extremely inefficient.

Claude Code's convenience is that Subagent capability can start sub-agents automatically managing independent contexts, Bash tools can read/write files and operate directories, Task parallelism can run multiple Tasks simultaneously automatically waiting for completion, parameter passing uses variable substitution in prompts, making Claude Code an ideal environment for rapid prototyping and experimentation.

Programming framework functionality is that AutoGen, LangGraph, CrewAI and other frameworks provide complete MAS capabilities, but require writing Python code to define and orchestrate agents, suitable for scenarios requiring complex logic control, version management, and team collaboration, steep learning curve but full-featured.

### 4.3 Why Now? The Tipping Point of Technical Maturity

The concept of multi-agent is not new (academia has long had frameworks like JADE), but why has MAS only now become practical? Because multiple technologies have matured simultaneously.

- **LLM Capability Breakthrough** has enabled models like Claude 3.5 Sonnet and GPT-4 to understand complex agent blueprints, understand collaborative relationships and data dependencies, autonomously decide execution strategies rather than mechanically execute instructions.
- **Long Context Windows** allow individual agents to handle quite complex tasks, can read large amounts of reference materials and input data at once, reducing pressure on module division.
- **Tool Usage Capability** allows LLMs to manipulate file systems, invoke search engines, APIs, databases, evolving from "conversation partners" to "actors."
- **Cost Reduction** has brought token prices down to a level where complex systems can be run at scale, a MAS task involving dozens of agent invocations can be controlled to a few dollars in cost, making MAS evolve from laboratory concept to practical tool.

These factors working together have made MAS evolve from theoretical concept to a practical technology for daily use.

## 5. Case Study: Multi-Agent System for Regional Research

Concepts, no matter how clear, need concrete examples to aid understanding. Let's look at an actual MAS application: a multi-agent system for regional country research.

### 5.1 Task Background

The research objective is to comprehensively analyze a country's economic, political, and social conditions during a specific period, generating a structured research report. Complexity analysis shows this task requires collecting large amounts of information (news reports, academic literature, statistical data, historical background, etc.), requires applying multiple analytical frameworks (class analysis, contradiction analysis, economic assessment, etc.), requires generating a structured research report conforming to specific style and format, with information volume and task complexity far exceeding the processing capacity of a single LLM invocation.

If using a long prompt, you would need to prepare an extremely long prompt of approximately 30,000-50,000 words, containing instructions for all steps and all reference materials. Even then, you face all the problems we discussed earlier: attention diffusion, lack of isolation, inability to parallel, rigid process, maintenance difficulty.

Using MAS implementation, we decompose this complex task into a three-stage pipeline, completed through collaboration of 7 specialized agents.

### 5.2 System Architecture

The entire system follows a clear three-stage pipeline architecture:

- **Phase 1: Data Collection** → Outputs to `data/01.materials/`
- **Phase 2: Analysis** → Outputs to `data/02.analysis/`
- **Phase 3: Report Generation** → Outputs to `data/03.reports/`

Each phase's output becomes the next phase's input, transferring data through the file system.

The system contains 7 agents, with functional division as follows:

**0. orchestrator (Orchestrator)**

The special agent coordinating the entire research process, understands user requirements, formulates execution plans, sequentially invokes various agents, monitors progress.
- Input: Country code (such as "ARG"), research dimensions, analytical frameworks
- Workflow: Read user requirements and reference library → Create directory structure → Sequentially invoke phase agents → Check output quality → Loop invoke if necessary
- Output: None (coordinator doesn't produce content)

**Phase 1: Data Collection Agents**

- **1.1 broad-reconnaissance (Broad Reconnaissance)**
  - Responsibility: Quickly collect basic information and important events about the country, establish information map
  - Input: Country code parameter
  - Output: `data/01.materials/overview.md` (overview document, contains topic list)

- **1.2 focused-collection (Focused Collection)**
  - Responsibility: In-depth information collection on key topics
  - Input: Country code + `overview.md`
  - Output: `topic-economy.md`, `topic-politics.md`, `topic-society.md`, etc.
  - Note: Can parallel start 3-5 instances to separately collect different topic domains

**Phase 2: Analysis Agents** (Three agents can execute in parallel)

- **2.1 contradiction-analyzer (Contradiction Analyzer)**
  - Responsibility: Apply dialectics to identify main and secondary social contradictions
  - Input: All material files + `references/dialectical-analysis-method.md`
  - Output: `data/02.analysis/contradictions.md`

- **2.2 class-analyzer (Class Analyzer)**
  - Responsibility: Analyze class composition and class struggle situation
  - Input: All material files + `references/class-analysis-framework.md`
  - Output: `data/02.analysis/class-structure.md`

- **2.3 economic-evaluator (Economic Evaluator)**
  - Responsibility: Evaluate economic conditions and development trends
  - Input: All material files (particularly focused on economic topics)
  - Output: `data/02.analysis/economic-assessment.md`

**Phase 3: Report Generation Agent**

- **3.1 report-synthesizer (Report Synthesizer)**
  - Responsibility: Synthesize all analyses into a structured, stylistically unified final report
  - Input: All analysis results + report template + style guide
  - Output: `data/03.reports/final-report.md`

### 5.3 Manifestation of Module Boundaries

This system perfectly embodies the four key characteristics of modularity.

**Boundary isolation** is manifested in `focused-collection` only being responsible for collecting materials without needing to know what analyses will follow, `contradiction-analyzer` only focuses on contradiction analysis without knowing what other analyzers are doing, modifications to each module don't affect each other: improving class analysis methods doesn't affect contradiction analysis.

**Independent lifecycle** is manifested in `broad-reconnaissance` releasing its context window immediately upon completion, even if it processed 100,000 tokens of information it doesn't affect subsequent agents' context budgets, each agent is created on demand and destroyed after use.

**Clear interface** is manifested in each agent clearly knowing where input comes from (parameters like country code, file paths like `overview.md`, reference libraries like `class-analysis-framework.md`), where to write output (specific file paths like `data/02.analysis/contradictions.md`), what responsibilities are (role definition clear without overstepping), callers (orchestrator) only need to know interfaces without needing to know internal implementation.

**Transparent traceability** is manifested in all intermediate products being saved as files that humans can inspect at any time, can see what topics `overview.md` identified, can see what information `topic-economy.md` collected, can see the analysis quality of `contradictions.md`, when problems occur can restart from any intermediate stage without needing to run from the beginning.

### 5.4 Comparison with Long Prompts

Let's explicitly compare the differences between implementing the same task with long prompts versus MAS.

If implementing the same task with long prompts, you would need to concatenate all instructions and reference materials into one complete prompt (total length approximately 30,000+ words), including:
- Role definition and overall requirements (approximately 500 words)
- Step 1: Broad reconnaissance (approximately 800 words)
- Step 2: Focused collection (approximately 1000 words)
- Step 3: Contradiction analysis (approximately 1200 words)
- Step 4: Class analysis (approximately 1000 words)
- Step 5: Economic assessment (approximately 800 words)
- Step 6: Report synthesis (approximately 1000 words)
- Attachment 1: Marxist epistemology framework (approximately 10,000 words)
- Attachment 2: Dialectical analysis method (approximately 5000 words)
- Attachment 3: Class analysis paradigm (approximately 8000 words)
- Attachment 4: Report template (approximately 2000 words)
- Attachment 5: Writing style guide (approximately 1500 words)

The problems with this approach are:
- Attention diffusion: Although not exceeding context window, the LLM needs to simultaneously "remember" requirements for 6 steps, by the time it executes step five, details of step one may already be blurred
- Lack of isolation: Modifying the dialectical analysis method (Attachment 2) might inadvertently affect class analysis execution, because all content is in one context and the LLM might produce unexpected "crosstalk"
- Cannot parallel: Must execute all 6 steps sequentially even though contradiction analysis, class analysis, and economic assessment can actually proceed simultaneously
- Rigid process: Want "focused collection" to loop three rounds, evaluating effectiveness and filling gaps after each round? Nearly impossible in long prompts; you cannot have the LLM "pause," check intermediate results, and then "continue"
- Maintenance difficulty: Want to adjust style guide? Need to reload the entire 30,000-word prompt; want to add "international relations analysis"? The entire prompt becomes longer and complexity rises exponentially

When implementing with MAS, the system is split into 7 independent agents. Each agent blueprint is 500-1200 words, each agent at runtime only loads reference libraries it needs (1-2 documents totaling approximately 10,000 words). More concise and clear, while also bringing some benefits:
- **Parallel execution**. Can simultaneously start 3-5 agents collecting information on different problem domains (such as economy, politics, society) without conflict, Phase 2's three analyzers can also run in parallel saving significant time.
- **Iterative loops**. Orchestrator can invoke focused-collection three rounds, checking collection quality each round and dynamically deciding whether to continue.
- **Independent maintenance**. Modifying dialectical analysis method only requires updating the `dialectical-analysis-method.md` reference library without affecting other agents, adding "international relations analysis" only requires adding a new agent.
- **Transparent control**. Each phase's output is visible, can be manually reviewed, can restart from any stage.

## 6. From Modules to Design Principles

At this point, we've established a complete conceptual framework for MAS and have seen a concrete example. But this is only the starting point.

### 6.1 Elevating the Level of Discussion

With MAS's conceptual framework, our discussion of AI applications is no longer about "how to write prompts more effectively," "how to make LLMs understand my intentions," "how to prevent LLMs from deviating from the topic," but upgrades to "is this agent's responsibility single," "is coupling between modules reasonable," "is the interface design clear," "is the system easy to extend and maintain," "how to balance module granularity and communication costs." This is design-level discussion, not technique-level debugging. Just as software engineering elevated from "how to write code" to "how to design systems," MAS allows us to elevate from "how to write prompts" to "how to design agent systems."

### 6.2 Applicability of Software Engineering Design Principles

Since MAS is a modular system, classic software design principles can be applied, for example:

- **Single Responsibility Principle (SRP)**. Requires that an agent should have only one clear responsibility, only one reason to change.

- **Open-Closed Principle (OCP)**. Requires that agents should be open for extension, closed for modification.

- **Dependency Inversion Principle (DIP)**. Requires that agents should depend on abstract interfaces rather than concrete implementations.

- **Law of Demeter (LoD)**. Requires that agents should only communicate with direct collaborators, should not understand the system's global structure.

- **Composite Reuse Principle (CRP)**. Requires prioritizing composition of agents to implement complex functionality, rather than attempting to write one "omnipotent" agent.

### 6.3 Next Steps: Deep Exploration of Design Principles

These brief introductions to principles are just appetizers. In subsequent articles, we will combine past software design experience to discuss in detail more agent design-related issues, for example (but not limited to):
- How to apply these principles to agent design (detailed explanations and examples of each principle, how to identify designs that violate principles, how to refactor to follow principles)
- Common patterns in agent design (Orchestrator pattern, Pipeline pattern, Parallel Execution pattern, Iterative Refinement pattern, Specialist Collaboration pattern, etc.)
- How to evaluate the quality of a MAS design (Cohesion metrics, Coupling metrics, Testability assessment, Maintainability assessment, etc.)
- Trade-offs and challenges in MAS design (choosing module granularity—too coarse or too fine, communication cost vs isolation benefits, debugging and monitoring strategies, error handling and recovery mechanisms, etc.)

---

## Appendix: Key Terminology Reference Table

| Chinese | English | Notes |
|---------|---------|-------|
| 多智能体系统 | Multi-Agent System (MAS) | System of multiple collaborating agents |
| 智能体 | Agent | Module implemented using LLM |
| 智能体蓝图 | Agent Blueprint | Agent definition document (source code) |
| 智能体实例 | Agent Instance | Running agent (object instance) |
| 编排者 | Orchestrator | Special agent coordinating other agents |
| 文件管道 | File-based Pipeline | Method of passing data through file system |
| 参考库 | Reference Library | Shared domain knowledge documents |
| 上下文窗口 | Context Window | Number of tokens LLM can process at once |
| 模块 | Module | General concept in software engineering |
| 边界 | Boundary | Scope of module responsibility |
| 生命周期 | Lifecycle | Process of creation, execution, destruction |
| 接口 | Interface | Definition of input-output |
| 隔离 | Isolation | Characteristic of modules not interfering with each other |

---

## Conclusion

Starting from the dilemma of long prompts, we've seen insights from software engineering modularity, established the conceptual framework of multi-agent systems, explored runtime environment requirements, understood MAS operation through a concrete example, and finally pointed toward the direction of design principles for the next step.

Multi-agent systems may herald a new form of software in the AI era. Not traditional "writing code" but "designing agents," not "compile and execute" but "orchestrate and collaborate," not "function calls" but "module dialogue," but fundamentally still software engineering, just expressed in natural language rather than programming languages.

For software practitioners, this is an exciting turning point. The software engineering knowledge we've accumulated—modularity, design principles, architectural patterns—has not become obsolete, but rather has found new application scenarios. MAS is not a disruption of software engineering, but inheritance and evolution.
