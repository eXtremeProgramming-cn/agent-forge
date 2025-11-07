# MAS Architecture Taxonomy: What Should AI Do and What Should Humans Do?

## A Real Puzzle

When using AI tools to assist with research or analysis tasks, you encounter a phenomenon: sometimes letting AI run fully automatically produces high-quality work in just a few hours; but other times, even with massive computational resources, the output is shallow and lacks insight. Worse, it's hard to predict which scenario will occur.

The root of this puzzle lies in: **different types of tasks require fundamentally different MAS (Multi-Agent System) configurations and human-AI collaboration patterns**. Yet we lack a systematic framework to assess task nature and select appropriate design strategies.

This article introduces the Cynefin framework and proposes an MAS architecture taxonomy to help you:
- Diagnose which category a task belongs to
- Select appropriate system configurations
- Clarify human-AI collaboration interfaces
- Understand how systems should evolve

## Cynefin Framework: Problem Nature Determines Method Selection

Proposed by Dave Snowden, the Cynefin framework's core insight is: **the nature of a problem determines the appropriate decision-making pattern**. The framework divides problem contexts into four domains:

![Cynefin Framework](https://upload.wikimedia.org/wikipedia/commons/a/ab/Cynefin_framework_2022.jpg)

- **Clear Domain**: Clear cause-effect relationships, best practices exist. Decision pattern: Sense-Categorize-Respond
- **Complicated Domain**: Cause-effect relationships exist but require expert analysis. Decision pattern: Sense-Analyze-Respond
- **Complex Domain**: Cause-effect relationships only identifiable in retrospect, require exploration. Decision pattern: Probe-Sense-Respond
- **Chaotic Domain**: Cause-effect relationships indiscernible, require immediate action. Decision pattern: Act-Sense-Respond

In MAS design, this framework helps us answer core questions: **Can tasks be automated? To what extent? Where do humans intervene?**

Key insight: **The system boundary is the research process itself, not the research object**. The MAS we design doesn't simulate or act directly on research objects, but assists the research process—the entire cognitive activity from searching materials, analyzing data, constructing theories to writing reports.

## Clear Domain: Fully Automated Pipeline

### Task Characteristics

Required information clearly exists, retrieval paths are clear, processing flows are straightforward, requiring no judgment or choice.

**Typical Scenarios**: Batch file downloads, format conversion, data cleaning, simple information extraction.

### Criteria

- **Information Existence**: Files exist at specific locations, locations are determinable
- **Clear Causality**: Access URL → Download file → Store, steps are explicit
- **No Expert Judgment**: No content evaluation or quality assessment involved
- **Standardizable Process**: Entire process can be written as explicit algorithms

### Business Architecture

```
Single-Stage Pipeline:
Input: URL list + Naming rules
  ↓
Process: Iterate URLs → Download files → Name by rules → Organize directories
  ↓
Output: Well-organized file collection
```

**Architectural Features**:
- Single responsibility, linear flow, no complex branching
- Deterministic: same input produces same output
- No human-AI collaboration point: fully automated

### Real Case: News on China Newsletter Download

News on China is a weekly newsletter, with all past issues stored on the website as PDFs following a fixed URL pattern. Researchers need these newsletters as material for analyzing media discourse evolution.

**Execution Flow**:
1. Human defines: URL pattern, time range, naming rules, storage location
2. AI executes: Generate URL list (~250 files), parallel download, name by rules, generate logs
3. Result: Takes ~15 minutes, saving humans ~3 hours of manual downloading

### Human-AI Collaboration Pattern

- **Design Phase** (human-led): Define target URLs, file naming conventions, storage locations
- **Execution Phase** (AI fully automated): No human intervention needed
- **Validation Phase** (human spot-check): Check file count and content

This is the simplest collaboration pattern: humans define tasks, AI executes, humans validate. No iteration or feedback loops.

### Design Principles

- **Clarity First**: Fully specify URLs, naming, storage structure before execution
- **Recoverability**: Implement resumable downloads, record downloaded file lists
- **Rate Control**: Avoid being identified as malicious crawlers
- **Flexible Tool Selection**: Simple tasks don't need complex architecture, Claude Code single session suffices

## Complicated Domain: Parallelizable Analysis Pipeline

### Task Characteristics

Requires professional judgment and interpretation of information, but the evaluation framework itself is stable and predetermined. Analysis paths are clear, but application requires expert-level capabilities.

**Typical Scenarios**: Indicator evaluation, compliance checks, multi-dimensional analysis.

### Criteria

- **Information Exists but Needs Interpretation**: Information exists on the internet but requires expert capabilities to understand and evaluate
- **Clear but Analysis-Requiring Causality**: Analysis paths are clear but require judgment
- **Requires Expert Judgment**: Needs evidence synthesis and degree assessment
- **Framework Predetermined**: Evaluation dimensions and indicator systems are designed in advance, not emergent during evaluation

**Distinction from Clear**: "Does country X have law A?" (yes/no) is Clear; "How well is law A executed?" requires evidence synthesis and judgment—Complicated.

### Business Architecture

```
Three-Stage Pipeline:

[Data Collection] → [Structured Analysis] → [Report Generation]
       ↓                    ↓                       ↓
For each indicator    Apply scoring rules      Aggregate results
Search information   Synthesize evidence      Generate assessment
```

**Architectural Features**:
- Clear flow, decomposable into independent stages
- Different indicators can be processed in parallel (fully leveraging MAS capabilities)
- Each stage produces verifiable intermediate results
- Humans can review between stages but typically don't need to intervene

### Real Case: Digital Sovereignty Index (DSI) Assessment

DSI is an indicator system for evaluating national digital sovereignty, containing 4 dimensions and 16 indicators. Each indicator is refined into 15-20 specific questions.

**Assessment Flow**:
1. **Data Collection**: For each question, collect information from government websites, policy documents, news reports, etc.
2. **Analysis & Scoring**: According to predefined scoring rules, score each indicator one by one (requires judging "degree of data localization implementation")
3. **Report Generation**: Aggregate scores from 16 indicators, generate comprehensive assessment

**Key Features**:
- What data to collect is clear: each indicator corresponds to an explicit question list
- How to analyze is clear: each indicator has explicit scoring rules
- Can parallelize: 16 indicators' assessments don't interfere with each other; each country requires accessing thousands of web pages, but can execute in parallel

### Variant: Dynamic Question Generation

Sometimes fine-grained questions for data collection need to be dynamically generated based on research objects.

For example, assessing "agricultural production": for Nepal, questions should be "rice planting area," "rice annual yield"; for Ghana, questions become "cocoa annual yield," "cocoa export value."

In this case, the flow becomes: **overview → question generation → data collection → analysis → report**

First do coarse-grained research to understand the country's agricultural structure, then generate targeted questions, then proceed to collection and analysis.

But this still belongs to the Complicated domain because question generation, though dynamic, can be completed automatically through rules and context, requiring no human intervention.

### Human-AI Collaboration Pattern

- **Design Phase** (human-led): Define evaluation framework (dimensions and indicators) and scoring rules
- **Execution Phase** (AI-led): Data collection and analysis assessment
- **Review Phase** (human validation): Validate analysis quality, check if framework is correctly applied

Humans can validate intermediate results but don't need to intervene during the process.

### Design Principles

- **Task Decomposition**: Identify independently processable subtasks
- **Parallel Execution**: Fully leverage multi-agent parallelism
- **Explicit Rules**: Clearly model scoring rules for easy debugging and optimization
- **Verifiable Intermediate Results**: Each indicator's assessment result is traceable for human review

## Complex Domain: Iterative Human-AI Collaboration

### Task Characteristics

AI can process vast amounts of information, but critical insights must come from humans. Theoretical frameworks cannot be preset; they must be determined after understanding specific contexts. Answers emerge through exploration.

**Typical Scenarios**: Deep analysis guided by theoretical frameworks, content curation requiring editorial judgment.

### Criteria

- **Information Exists but Meaning Must Emerge**: Information exists, but its meaning and patterns can only surface through integrative understanding
- **Causality Only Identifiable Retrospectively**: Don't know what theoretical perspective to use; framework needs to be "discovered" during the process
- **Cannot Be Obtained by Applying Existing Frameworks**: Framework itself needs to be constructed
- **Requires Human Creative Insight**: "Eureka moments" of theoretical innovation, seeing deep connections beneath surface text

### Business Architecture

```
Three-Stage Human-AI Collaboration:

[AI: Exploratory Research] → [Human: Insight & Framework Building] → [AI: Framework-Based Deep Analysis]
         ↓                              ↓                                        ↓
    Prepare materials          Identify emergent patterns            Apply human-provided framework
    Initial organization       Build theoretical framework           Structured analysis (decompose to Complicated)
```

**Architectural Features**:
- Clear human intervention point (middle stage)
- Upstream and downstream stages decoupled: second stage doesn't care how first stage produces materials, only that material format is suitable
- Human-provided insights/frameworks become input for downstream analysis
- System evolution: human intervention decomposes Complex tasks into Complicated tasks

### Real Case 1: South Africa's Class and Contradiction Analysis

To conduct class analysis of a country (in the Marxist sense), the key feature is: **must have a theoretical framework applicable to this specific country; cannot apply a universal framework to all countries**.

Analyzing South Africa, if you don't understand the historical context and current state of racial issues, class analysis will completely miss the point. You might analyze petty bourgeoisie at length, but petty bourgeoisie is not the main contradiction in South Africa—South Africa's social contradictions unfold around racial issues, requiring a "neo-colonialism" framework to understand.

Similarly, analyzing India requires understanding the caste system; analyzing Middle Eastern countries requires understanding Islamic influence.

**Flow**:
1. **AI conducts preliminary research**: Use standardized indicators to collect information, including all left-wing organizations' and thinkers' analytical articles in that country, forming a conjunctural overview
2. **Human intervenes to form framework**: Read materials, form initial sense of the country's contradictions, exchange with experts, determine what theoretical framework to guide analysis
3. **AI deepens under framework**: Import theoretical framework into MAS, subsequent deep analysis proceeds under this framework (task now decomposes to Complicated)

**Key Point**: Theoretical framework is emergent, not preset. Must first understand specific context to select framework. AI provides materials but cannot replace human insight.

### Real Case 2: News on China News Selection

Producing "News on China" weekly news digest, flow divided into two segments:

**First Segment: News Selection** (must have human intervention)
- Select 10-12 stories from this week's all news to enter the newsletter
- Typical editorial judgment scenarios:
  - Several news items are actually about the same event (all about Fourth Plenum, different angles), AI can't identify this
  - Combine related but not completely identical news to tell a more complete story
  - Judge which types of news are more important, how to balance positive/negative news ratios
  - Overall rhythm and narrative logic of this issue

These judgments, AI doesn't do well; editors must think.

**Second Segment: Deep Research and Summary Writing** (can be automated)
- For selected news leads, conduct comprehensive research from 7 angles: full event picture, media coverage, expert commentary, historical background, specialized knowledge, geopolitics, impact analysis
- Based on research results, write concise summaries within 80 words
- Arrange into email newsletter format

**Two segments completely decoupled**: Second segment doesn't care how first segment selected news, only needs editors to provide a news lead list.

### Human-AI Collaboration Pattern

**AI does overview, humans provide framework or judgment, AI deepens analysis under framework**.

**Human-AI interface design must be clear**:
- What format materials does upstream AI produce for easy human reading and judgment?
- How do humans inject insights/frameworks into the system? (Documents? Structured input?)
- How does downstream AI understand and apply human-provided frameworks?

### Design Principles

- **Clear Human Intervention Points**: At which stage of the flow humans are needed, what are input/output formats
- **Context Transfer Mechanism**: How human insights transfer to downstream AI
- **Decoupled Design**: Upstream and downstream stages are independent, human intervention doesn't break overall flow
- **Support Domain Decomposition**: After human framework injection, downstream tasks decompose to Complicated, can be automated

The core challenge of Complex domain is carefully designing human-AI interfaces, clarifying the boundary between "what AI can do" and "what humans must do."

## Chaotic Domain: AI as Auxiliary Tool

### Task Characteristics

Required information doesn't exist in accessible data sources; must be obtained through human on-site judgment and creative work. Action precedes understanding: must do first to know.

**Typical Scenarios**: Fieldwork, original theory construction, innovation exploration.

### Criteria

- **Information Basically Doesn't Exist**: This is Chaotic domain's most critical feature
- **Cannot Complete Through Searching or Analyzing Existing Materials**: Must create new data through action
- **Causality Indiscernible at System Level**: Highly uncertain, need to sense through action

**Distinction from Complex**:
- Complex: Information exists (e.g., left-wing organizations' analytical articles), but needs human insight to identify patterns
- Chaotic: Information doesn't exist (e.g., Village Super traffic conversion mechanism, no public materials), must create through action

This distinction is crucial for business architecture design: determines whether task can be completed through web search + AI analysis (Complex), or must conduct fieldwork (Chaotic).

### Business Architecture

```
Human-Led Action Loop:

[Human: Field Action] → [Human: Sense Patterns] → [Human: Adjust Strategy]
        ↓                       ↓                          ↓
   Create data          Learn through action        Iterative optimization
   Build relationships  Identify emergent patterns

[AI: Auxiliary Clear Tasks]
        ↓
   Audio transcription, note organization, background material retrieval
```

**Architectural Features**:
- AI is not the subject, only an auxiliary tool
- Core information collection and theory construction done by humans
- AI can only do Clear domain auxiliary tasks

### Real Case: Guizhou Rongjiang Village Super Research

Researching Rongjiang Village Super, how digital technology assists rural revitalization. To make research solid, need to grasp many specifics:
- What's the actual monthly traffic?
- From which media/self-media does traffic come?
- How does the county operate the massive self-media matrix?
- How does traffic convert to township economy?
- What are conversion forms? What are effects?
- What work do townships and villages do to create and convert traffic?

**Core Problem**: This information doesn't exist on the internet, no archival records, AI has nowhere to get it. Must go to grassroots for research, talk to people actually doing the work, refine theoretical frameworks through this process.

More importantly, don't know what questions to ask beforehand. Only on site, understanding actual operational methods, can you pose theoretically meaningful questions.

### Human-AI Collaboration Pattern

**Humans are subjects, AI is tool**:
- Organize interview recordings (speech-to-text)
- Organize field notes
- Retrieve background materials
- Generate preliminary material classification

These are all Clear domain tasks AI can do. But core field observation, theory construction, insight formation must be done by humans.

### Design Principles

**Accept AI's limitations**. Don't try to design "automated fieldwork systems." Clarify auxiliary work AI can do, doing them well is sufficient.

Chaotic domain reminds us: identifying AI's boundaries is as important as identifying AI's capabilities.

## How to Determine Which Domain a Task Belongs To?

### Three-Question Decision Tree

```
Question 1: Does information required to complete the task already exist?
├─ Basically doesn't exist → Chaotic domain (need creative action to generate new data)
│   Example: Rongjiang Village Super traffic conversion mechanism (needs fieldwork)
│
└─ Exists (can obtain through search, literature, public materials) → Continue judgment
    │
    Question 2: Is the causality/analytical path from information to conclusion clear?
    ├─ Clear (know "how to analyze") → Continue judgment
    │   │
    │   Question 3: Does it require expert-level judgment and interpretation?
    │   ├─ No → Clear domain (standard process can handle)
    │   │   Example: Download specified URL files, transcribe audio
    │   │
    │   └─ Yes → Complicated domain (needs analysis but path is clear)
    │       Example: Apply DSI indicators to assess digital sovereignty
    │
    └─ Not clear (don't know "what perspective to use for analysis") → Complex domain (needs exploration)
        Example: Build class analysis framework for South Africa, select 10 key news stories for weekly
```

### Typical Feature Comparison Table

| Domain | Information Existence | Processing Complexity | Framework Certainty | AI Capability | Human Role |
|---|----------|----------|----------|--------|---------|
| **Clear** | Clearly exists | Simple & direct | No framework needed | Fully automated | Define tasks, validate results |
| **Complicated** | Clearly exists | Needs analysis | Framework can be preset | Expert system | Define rules and frameworks |
| **Complex** | Clearly exists | Needs insight | Framework emergent | Assist material preparation | Provide insights and frameworks |
| **Chaotic** | Doesn't exist/inaccessible | Highly uncertain | Framework to be built | Only assist Clear tasks | Lead entire process |

## Design Principles Summary

### Clear Domain: Monitoring and Fault Tolerance

- Pipeline design: unidirectional flow, clear steps
- Exception handling: network interruption, data corruption, permission issues
- Progress visibility: real-time monitoring, determine if running normally
- Idempotency: support resumable operations, avoid duplicate work

### Complicated Domain: Parallelization and Rule Engine

- Task decomposition: identify independently processable subtasks
- Parallel execution: fully leverage multi-agent parallel capabilities
- Explicit rules: clearly model analysis rules for easy debugging and optimization
- Verifiable intermediate results: each stage's output is traceable and verifiable

### Complex Domain: Human-AI Interface Design

- Clear intervention points: clarify at which stage of flow human judgment is needed
- Interface standardization: what format materials does AI produce for humans? How do humans inject insights into system?
- Decoupled design: upstream and downstream stages are independent, human intervention doesn't break overall flow
- Context transfer: how human frameworks and insights transfer to downstream AI

### Chaotic Domain: Accept Limitations

- Humans are subjects: don't try to automate core processes
- AI assists: identify Clear domain tasks that can assist (organization, retrieval, transcription)
- Tool positioning: treat AI as tool to augment human capabilities, not replace humans

### Core Insight

**Don't try to automate all tasks**. Identify task nature, select appropriate MAS configuration, clarify human role—this is good system design.

Forcing automation of Complex or Chaotic domain tasks often results in producing large amounts of shallow, insight-lacking content. Accurately identifying task domain and designing appropriate human-AI collaboration approaches unleashes the irreplaceable strengths of both AI and humans.

## Domain Decomposition: System Evolution Perspective

A final important insight: **research processes are often domain decomposition processes**.

Research typically starts from Chaotic or Complex:
- First time researching a new problem, don't know what theoretical framework to use (Complex)
- Don't even know where information is, what questions to ask (Chaotic)

But as research deepens:
- Formed theoretical framework, next time researching similar problems, task decomposes from Complex to Complicated
- Figured out data sources and analysis rules, task further decomposes, some stages even become Clear

**Evolution Path**:
```
Chaotic → Complex → Complicated → Clear
(Create data) → (Explore framework) → (Structured analysis) → (Standardized execution)
```

### MAS Design Evolution Implications

**Systems must support evolution**. A good research-oriented MAS should:
- In Complex stage, provide flexible human intervention mechanisms
- When framework is clear, support solidifying human insights into rules, decomposing to Complicated domain
- When rules are stable, support further automation, decomposing to Clear domain

This way, systems progressively automate as researchers' understanding deepens, rather than forcing automation of all stages from the start.

### Real Case: South Africa Class Analysis Evolution

First time analyzing South Africa:
- Chaotic: Don't know what to ask, need extensive reading to build feel
- Complex: Determine to use "neo-colonialism" framework
- Complicated: Deep analysis under framework

Second time analyzing similar country (e.g., Zimbabwe):
- Skip Chaotic: Already know what types of questions to ask
- May still need Complex: Need to judge if same framework applies, or needs adjustment
- Faster entry to Complicated: After framework is determined, large amounts of analytical work can be automated

After multiple iterations, even possible:
- Form a standard analytical framework applicable to Southern African countries
- Entire flow decomposes to Complicated, can rapidly batch analyze

## Conclusion

The Cynefin framework provides a systematic thinking tool for MAS design:

- **Diagnose task nature**: Which domain does this task belong to?
- **Select configuration**: What kind of system architecture should be adopted?
- **Clarify boundaries**: Which parts let AI do, which parts must humans do?
- **Plan evolution**: How to progressively automate as understanding deepens?

Next time designing MAS, first judge the task's domain, then select appropriate configuration. Don't let AI do what it's not good at, and don't let humans do what AI can do well.

This is true human-AI collaboration.
