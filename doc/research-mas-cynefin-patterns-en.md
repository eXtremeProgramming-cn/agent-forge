# Research-Oriented Multi-Agent Systems: A Cynefin-Based Pattern Language

**为研究而生的多智能体系统:基于Cynefin框架的模式语言**

---

## Abstract

This paper proposes a design framework for Research-Oriented Multi-Agent Systems (Research MAS). We first delineate the scope of "Research MAS"—systems whose boundary is the research process itself rather than the research object, aimed at knowledge discovery and insight generation, primarily processing unstructured qualitative materials. Addressing the problem that existing MAS design methodologies lack systematic guidance on "what should be built," we introduce Dave Snowden's Cynefin Framework and reinterpret it in the research context.

We introduce the concept of "Business Architecture" to distinguish it from technical architecture, establish a decision tree for classifying research tasks into Cynefin domains, and reveal the essence of the research process—the evolutionary path of Domain Decomposition (Chaotic → Complex → Complicated → Clear). Based on this framework, we distill four exemplars representing typical patterns in each Cynefin domain: Batch Retrieval of Archival Files (Clear), Indicator-Based Evaluation System (Complicated), Theoretical Framework Discovery Research (Complex), and Creative Fieldwork Research (Chaotic). Each exemplar is a complete design pattern including context, problem, business architecture, MAS design, human-AI collaboration patterns, concrete examples, and key design principles.

The core contributions of this paper include: (1) clearly defining the scope and characteristics of "Research MAS"; (2) introducing "Business Architecture" as a design level distinct from technical architecture; (3) reinterpreting the Cynefin Framework in research contexts, proposing "information existence" as a key classification criterion; (4) revealing domain decomposition as the core mechanism of research evolution; (5) providing reusable design patterns as practical guidance.

This pattern language provides systematic design principles for researchers and AI system designers in social sciences, humanities, and area studies, enabling them to select appropriate MAS architectures based on the nature of research problems, clarify human-AI collaboration boundaries, and optimize research workflows.

**Keywords:** Multi-Agent Systems, Cynefin Framework, Research Methodology, Knowledge Engineering, Pattern Language, Human-AI Collaboration, Domain Decomposition

---

## Table of Contents

**Part 1: Defining the Domain**
- 1.1 What is "Research MAS"?
- 1.2 Why Do We Need a New Design Framework?

**Part 2: Conceptual Framework**
- 2.1 Introducing the Concept of "Business Architecture"
- 2.2 Reinterpreting the Cynefin Framework in the Research Context
- 2.3 Decision Tree for Domain Classification
- 2.4 Domain Decomposition: The Evolutionary Path of Research

**Part 3: Exemplars as Patterns**
- 3.1 Clear Domain Exemplar: Batch Retrieval of Archival Files
- 3.2 Complicated Domain Exemplar: Indicator-Based Evaluation System
- 3.3 Complex Domain Exemplars: Framework Discovery and Editorial Judgment
- 3.4 Chaotic Domain Exemplar: Creative Fieldwork Research

**Appendices**
- Four-Domain Quick Reference Table
- References

---

## Introduction

In an era when artificial intelligence is profoundly transforming academic research paradigms, we stand at a critical crossroads. On one hand, Large Language Models (LLMs) and their derivative multi-agent systems (MAS) demonstrate astonishing information processing capabilities, completing in hours what would take human researchers weeks—literature reviews, content analysis, data integration. On the other hand, we increasingly recognize that simply applying AI tools to research tasks often produces shallow results lacking insight—outputs that are formally complete but lack research's most valuable qualities: **deep understanding** and **original insight**.

The problem's root lies not in AI's capabilities but in our lack of a systematic framework to guide "how to design AI systems for research." Existing multi-agent system design methodologies primarily come from engineering, business, and gaming domains, focusing on efficient task execution, precise decision support, and reliable system operation. These methodologies are not fully applicable to research—a domain centered on **knowledge discovery**, driven by **theory construction**, and filled with **epistemological uncertainty**.

This paper aims to fill this gap. We propose a design framework specifically for **Research-Oriented Multi-Agent Systems** that answers not only "how to build" but systematically addresses "what should be built" and "why build it this way." Our core insight is: **the nature of research tasks determines the appropriate MAS architecture**. A literature download task, an indicator evaluation task, a theoretical framework construction task, and a fieldwork research task are epistemologically distinct and thus require fundamentally different system designs.

To systematically identify these distinctions and guide design, we introduce Dave Snowden's **Cynefin Framework**—a proven decision-making framework that divides problem contexts into four domains (Clear, Complicated, Complex, Chaotic), each corresponding to different decision patterns and methodologies. By reinterpreting the Cynefin Framework in the research context, we can:

1. **Diagnose research tasks**: Systematically judge which Cynefin domain a specific research task belongs to
2. **Select architectural patterns**: Choose appropriate MAS design strategies based on domain characteristics
3. **Clarify human-AI boundaries**: Identify which tasks can be automated and which require human insight
4. **Plan evolutionary paths**: Understand how research processes progressively reduce uncertainty through domain decomposition
5. **Reuse design patterns**: Apply validated exemplars as practical guidance

This framework's uniqueness lies not in providing a universal technical solution but in establishing a **pattern language**—borrowing Christopher Alexander's concept. A pattern language is not an isolated collection of techniques but an organic system where each pattern describes a recurring problem and its solution, with patterns interrelating to form a complete design guidance system.

This paper is structured as follows:

**Part 1** delineates the scope of "Research MAS," clarifies its distinctions from other types of MAS, and argues why a specialized design framework is needed.

**Part 2** establishes the conceptual framework, introduces the concept of "Business Architecture," reinterprets the Cynefin Framework in research contexts, presents a domain classification decision tree, and explores domain decomposition as the core mechanism of research evolution.

**Part 3** presents exemplars from the four Cynefin domains, each a complete design case including real research scenarios (such as Digital Sovereignty Index evaluation, South Africa class analysis, News on China curation, Rongjiang Village Super fieldwork), providing reusable business architecture patterns and key design principles.

We believe this pattern language will help researchers and AI system designers in social sciences, humanities, and area studies more systematically and thoughtfully leverage multi-agent systems, significantly improving research efficiency while maintaining research depth and originality. More importantly, it will facilitate genuine collaboration between researchers and AI—not simple automation, but leveraging each's irreplaceable strengths to advance the boundaries of knowledge together.

---

# Research-Oriented Multi-Agent Systems: A Cynefin-Based Pattern Language

**为研究而生的多智能体系统:基于Cynefin框架的模式语言**

---

## Abstract

This paper proposes a design framework for Research-Oriented Multi-Agent Systems (Research MAS). We begin by defining the scope of "Research MAS"—systems whose boundaries encompass the research process itself rather than the research subject, with the purpose of knowledge discovery and insight generation, primarily processing unstructured qualitative materials. Addressing the lack of systematic guidance on "what to build" in existing MAS design methods, this paper introduces Dave Snowden's Cynefin framework and reinterprets it within the research context.

We introduce the concept of "business architecture" to distinguish it from technical architecture, establish a decision tree for classifying research tasks into Cynefin domains, and reveal the essence of the research process—the evolutionary path of Domain Decomposition (Chaotic → Complex → Complicated → Clear). Based on this framework, we distill four exemplars representing typical patterns in the Cynefin domains: bulk archival file retrieval (Clear), indicator-based evaluation systems (Complicated), theoretical framework discovery research (Complex), and creative fieldwork (Chaotic). Each exemplar constitutes a complete design pattern, including context, problem, business architecture, MAS design, human-AI collaboration model, concrete examples, and key design principles.

The core contributions of this paper are: (1) clearly defining the scope and characteristics of "Research MAS"; (2) introducing "business architecture" as a design layer distinct from technical architecture; (3) reinterpreting the Cynefin framework for research contexts, proposing "information existence" as a key classification criterion; (4) revealing domain decomposition as the core mechanism of research evolution; (5) providing reusable design patterns as practical guidance.

This pattern language offers systematic design principles for researchers and AI system designers in fields such as social sciences, humanities, and area studies, enabling them to select appropriate MAS architectures based on the nature of research questions, clarify human-AI collaboration boundaries, and optimize research workflows.

**Keywords:** Multi-Agent Systems, Cynefin Framework, Research Methodology, Knowledge Engineering, Pattern Language, Human-AI Collaboration, Domain Decomposition

---

## Table of Contents

**Part 1: Defining the Domain**
- 1.1 What is "Research MAS"?
- 1.2 Why Do We Need a New Design Framework?

**Part 2: Conceptual Framework**
- 2.1 Introducing the Concept of "Business Architecture"
- 2.2 Reinterpreting the Cynefin Framework in Research Context
- 2.3 Decision Tree for Domain Classification
- 2.4 Domain Decomposition: The Evolutionary Path of Research

**Part 3: Exemplary Patterns**
- 3.1 Clear Domain Exemplar: Bulk Archival File Retrieval
- 3.2 Complicated Domain Exemplar: Indicator-Based Evaluation Systems
- 3.3 Complex Domain Exemplar: Theoretical Framework Discovery and Editorial Judgment
- 3.4 Chaotic Domain Exemplar: Creative Fieldwork

**Appendices**
- Quick Reference Table for Four Domains
- References

---

## Introduction

At a time when artificial intelligence is profoundly transforming academic research paradigms, we stand at a critical crossroads. On one hand, Large Language Models (LLMs) and their derivative Multi-Agent Systems (MAS) demonstrate remarkable information processing capabilities, completing in hours what would take human researchers weeks—literature reviews, content analysis, data integration. On the other hand, we increasingly recognize that simply applying AI tools to research tasks often produces shallow, insight-deficient results. While these outputs may appear formally complete, they lack the most precious qualities of research: **deep understanding** and **original insights**.

The root of the problem lies not in insufficient AI capabilities, but in our lack of a systematic framework to guide "how to design AI systems for research." Existing multi-agent system design methodologies primarily originate from engineering, business, and gaming domains, focusing on efficient task execution, precise decision support, and reliable system operation. These methodologies are not fully applicable to the research domain—a field characterized by **knowledge discovery** as its purpose, **theory construction** as its core, and pervasive **epistemological uncertainty**.

This paper aims to fill this gap. We propose a design framework specifically for **Research-Oriented Multi-Agent Systems** that not only answers "how to build" but systematically addresses "what to build" and "why build it this way." Our core insight is: **the nature of research tasks determines the appropriate MAS architecture**. A literature download task, an indicator evaluation task, a theoretical framework construction task, and a fieldwork task differ fundamentally in epistemological terms, requiring radically different system designs.

To systematically identify these differences and guide design, we introduce Dave Snowden's **Cynefin Framework**—a well-validated decision framework that divides problem contexts into four domains (Clear, Complicated, Complex, Chaotic), each corresponding to different decision patterns and methodologies. By reinterpreting the Cynefin framework in the research context, we can:

1. **Diagnose research tasks**: Systematically determine which Cynefin domain a specific research task belongs to
2. **Select architectural patterns**: Choose appropriate MAS design strategies based on domain characteristics
3. **Clarify human-AI boundaries**: Identify which tasks can be automated and which require human insight
4. **Plan evolutionary paths**: Understand how the research process gradually reduces uncertainty through domain decomposition
5. **Reuse design patterns**: Apply validated exemplars as practical guidance

The unique value of this framework lies not in providing a universal technical solution, but in establishing a **Pattern Language**—borrowing Christopher Alexander's concept. A pattern language is not an isolated collection of techniques but an organic system where each pattern describes a recurring problem and its solution, with patterns interconnected to form a complete design guidance system.

This paper is structured as follows:

**Part 1** defines the scope of "Research MAS," clarifying its distinction from other types of MAS and arguing why a specialized design framework is needed.

**Part 2** establishes the conceptual framework, introducing the concept of "business architecture," reinterpreting the Cynefin framework in research contexts, proposing a domain classification decision tree, and deeply exploring domain decomposition as the core mechanism of research evolution.

**Part 3** presents exemplars for the four Cynefin domains, each a complete design case study including real research scenarios (such as digital sovereignty index assessment, South African class analysis, News on China news curation, and Rongjiang Village football fieldwork), providing reusable business architecture patterns and key design principles.

We believe this pattern language will help researchers and AI system designers in social sciences, humanities, and area studies to more systematically and thoughtfully leverage multi-agent systems, significantly enhancing research efficiency while maintaining research depth and originality. More importantly, it will facilitate genuine collaboration between researchers and AI—not simple automation, but leveraging each party's irreplaceable strengths to jointly advance the boundaries of knowledge.

---

# Part 1: Defining the Domain

## 1.1 What is "Research MAS"?

In an era when artificial intelligence is rapidly penetrating academic research, we face a seemingly simple yet profoundly confusing question: When we talk about "applying Multi-Agent Systems (MAS) to research," what exactly are we talking about? Are we developing a MAS to study a phenomenon (such as economic systems or social networks), or are we using MAS to assist researchers in the research process itself? These two interpretations point to fundamentally different system design requirements.

This paper focuses on the **latter**—what we call "Research-Oriented Multi-Agent Systems" (Research MAS). To avoid ambiguity, we must begin with a clear definition.

### Core Definition and System Boundaries

**Research MAS** refers to a class of multi-agent systems whose design objective is to **assist and enhance the research process itself**, rather than simulate or directly act upon the research subject. In other words, **the system boundaries encompass the research process, not the research subject**.

This boundary demarcation is crucial. Consider a project studying social movements:
- **Research subject**: Social movements in a country (protests, organizational mobilization, political discourse, etc.)
- **Research process**: Literature review, archival search, content analysis, theory construction, report writing
- **Research MAS scope**: Assisting with information gathering, material organization, content analysis, literature review, and other tasks in the research process

If we develop a multi-agent simulation system to model individual behaviors and group dynamics in social movements, the system boundaries encompass the research subject itself—this is **not** what this paper discusses as "Research MAS." However, if we develop a multi-agent system to help researchers search, read, and analyze large volumes of literature and archival materials about social movements to generate insights, the system boundaries encompass the research process—this **is** our focus.

### Fundamental Purpose: Knowledge Discovery and Insight Generation

The fundamental purpose of Research MAS is not task execution or decision support, but **knowledge discovery and insight generation**. Such systems aim to help researchers distill understanding from massive, unstructured qualitative materials, construct theories, and produce previously non-existent knowledge.

"Knowledge discovery" here has a specific meaning: it is not mining statistical patterns from data (as in machine learning pattern recognition), but deep understanding and synthesis of semantic materials such as texts, archives, and interviews, involving concept definition, causal mechanism identification, and theoretical framework construction. This knowledge production activity is highly **creative** and **theoretical**, representing the core characteristic of humanities and social science research.

### Primary Objects: Unstructured Qualitative Materials

Research MAS primarily processes **unstructured qualitative materials**:
- **Literature**: Academic papers, book chapters, research reports
- **Archives**: Historical documents, government bulletins, organizational publications
- **Interviews**: Fieldwork records, oral histories, expert interviews
- **Web content**: News reports, social media content, organizational websites

The common characteristic of these materials is **high semantic density**—the value of information lies not in the quantity of data but in the meaning, context, and deep implications of texts. Understanding these materials requires not only natural language processing technology but also profound grasp of the research field, theoretical frameworks, and research questions.

This contrasts sharply with systems processing structured data (such as business intelligence or data analysis systems). The latter's inputs are numbers, tables, time series with relatively clear semantics; the former's inputs are texts, narratives, discourses whose meanings require interpretation and understanding.

### Application Domains: Social Sciences, Humanities, and Area Studies

Primary application domains for Research MAS include but are not limited to:
- **Social Sciences**: Political science, sociology, anthropology, international relations
- **Humanities**: History, cultural studies, intellectual history
- **Area and Country Studies**: Comprehensive political, economic, and social analysis of specific regions
- **Policy Analysis**: Public policy evaluation, think tank research

The common characteristics of these fields are: **complexity of research subjects**, **unstructured materials**, **centrality of theoretical frameworks**, **emergence of insights**. In these fields, research quality is determined not by data volume or computational power but by **depth of understanding** and **originality of theory**.

### Distinctions from Other Types of MAS

To further clarify the boundaries of "Research MAS," we compare it with two common MAS applications:

| Dimension | Research MAS | Business Analysis MAS (Finance/Market) | Operational MAS |
|-----------|--------------|---------------------------------------|-----------------|
| **Purpose** | Knowledge discovery | Decision support | Task execution |
| **Input** | Unstructured text | Structured data | Explicit instructions |
| **Output** | Insights and theories | Reports and recommendations | Action results |
| **Evaluation criteria** | Depth and originality | Accuracy and timeliness | Efficiency and reliability |
| **Human role** | Lead theory construction | Review and decide | Supervise and intervene |
| **Uncertainty** | High (exploring unknown) | Medium (predicting trends) | Low (executing known) |
| **Knowledge production** | Create new theories | Apply existing models | No knowledge production |
| **Time scale** | Long cycle (months, years) | Medium cycle (weeks, months) | Short cycle (seconds, minutes) |

**Business Analysis MAS** (such as financial analysis or market research systems) also process complex information, but their goal is **decision support** rather than knowledge discovery. These systems typically receive structured or semi-structured data (financial statements, market indicators, transaction data) as input and produce reports and recommendations (investment advice, market forecasts, risk assessments) as output. Evaluation criteria are **accuracy** and **timeliness**—Are predictions accurate? Are recommendations effective? The human role is primarily to review results and make final decisions.

**Operational MAS** (such as robot coordination or automated process systems) aim for **task execution**. These systems receive explicit instructions, perform specific operations, and produce observable action results. Evaluation criteria are **efficiency** and **reliability**—Are tasks completed quickly? Is the system running stably? Uncertainty is relatively low because task objectives and execution paths are clear.

In contrast, Research MAS faces **fundamental uncertainty**: research questions often have no standard answers, theoretical frameworks need to be explored and constructed during the research process, and insight generation is **emergent**—insights are not pre-existing waiting to be discovered but are created during the research process. This characteristic poses unique challenges for Research MAS design.

### Boundary Clarification: What's Included, What's Not

To avoid concept inflation, we need to clearly define the scope of "Research MAS":

**Included:**
- Tasks requiring deep semantic understanding (literature review, content analysis, theoretical synthesis)
- Tasks involving insight generation (pattern identification, framework construction, hypothesis formulation)
- Knowledge integration and synthesis (cross-literature synthesis, cross-case comparison)
- Tasks assisting researchers' cognitive processes (information organization, relationship visualization, argument structuring)

**Not included:**
- Purely data-driven experimental research (such as biomedical experiments, physics simulations)
- Research primarily relying on numerical computation (such as econometric models, statistical inference)
- Cases where the system itself is the research subject (such as multi-agent system simulation research)

**Gray areas:**
- **Quantitative social science research**: Partially applicable. If it involves extensive text analysis (such as political discourse analysis, policy text research), it falls within our scope; if primarily statistical modeling, it does not.
- **Mixed methods research**: Partially applicable. Research MAS can assist with qualitative analysis components but cannot replace statistical analysis.
- **Computational social science**: Depends on specific tasks. If semantic analysis and theory construction, applicable; if network analysis or big data modeling, may not be applicable.

### Key Characteristics

Synthesizing the above discussion, we can distill four key characteristics of Research MAS:

**1. Semantic Density of Information**

Research MAS processes not "data points" but "texts," where every passage contains rich semantics, context, and implicit meanings. The system must possess deep semantic understanding capabilities, not merely surface-level pattern recognition.

**2. Centrality of Theoretical Frameworks**

Research quality heavily depends on **appropriate theoretical perspectives**. The same materials analyzed through different theoretical frameworks produce radically different insights. Research MAS must be able to handle the selection, application, and adjustment of theoretical frameworks—this is the core of the research process, not peripheral assistance.

**3. Creative Knowledge Production**

The ultimate goal of Research MAS is to help generate **theoretical insights that did not previously exist**. This is not deriving conclusions from the known but discovering new connections, identifying new patterns, and constructing new explanatory frameworks through exploration. This creativity makes research tasks fundamentally **emergent**.

**4. Iterative Epistemology**

The research process is not linear "input → processing → output" but a spiral cognitive deepening process. Researchers' understanding evolves as research progresses, research questions may be redefined, analytical frameworks may be adjusted, and materials may be reinterpreted. Research MAS must support this **iterativity** and **adaptability**.

These four characteristics collectively determine the design challenges of Research MAS: we cannot simply apply traditional MAS architectures or existing AI tools directly to research scenarios but must develop new design methods tailored to the epistemological characteristics of research.

---

## 1.2 Why Do We Need a New Design Framework?

Given that multi-agent systems already have mature design methods and architectural patterns, why do we need a new framework specifically for "Research MAS"? The answer lies in this: existing MAS design methods primarily focus on **"how to build"**, while severely lacking systematic guidance on **"what to build"**—especially when "what to build" itself depends on the nature of the research question.

### Limitations of Existing MAS Design Methods

#### Limitation 1: Technical Architecture Prioritized, Business Logic Missing

Current literature and practice on MAS primarily focus on **technical architecture**: How to implement Agent communication? How to design coordination mechanisms? How to optimize parallel execution? These questions are certainly important, but they all presuppose a premise: you already know what kind of system to build.

However, in research scenarios, **"what to build" itself is a complex question**:
- How many stages should a literature review task have?
- Which stages can be automated? Which require human intervention?
- How should data flow between stages?
- How to ensure output quality meets academic standards?

These questions do not belong to the technical architecture level but to the **business architecture** (or "research process architecture") level. Existing MAS design methods pay insufficient attention to this level, often assuming business logic is already clear and only requiring technical implementation. But in the research domain, business logic itself is the core design challenge.

#### Limitation 2: Ignoring the Epistemological Specificity of Research

The research process has unique epistemological characteristics that are not prominent in traditional MAS application scenarios (such as industrial control, e-commerce recommendation, game AI):

**Exploratory Nature and Uncertainty**: Many research tasks do not have clear objectives at the outset; problems evolve as research deepens. This is fundamentally different from MAS executing predefined tasks.

**Centrality of Theory Construction**: Research is not merely "processing information" but "constructing understanding." This requires systems to handle abstract concepts, theoretical frameworks, and causal reasoning—all difficult to describe using traditional Agent behavior modeling methods.

**Complexity of Quality Standards**: Academic research quality standards (originality, depth, rigor, theoretical contribution) are far more complex and ambiguous than operational task quality standards (speed, accuracy, completion). How to embody these standards in MAS design?

**Emergence of Knowledge**: Research value often comes from **unexpected discoveries** and **emergent insights**, not accurate realization of expected results. This poses challenges for MAS design: How to build a system that not only executes predefined tasks but also supports the emergence of insights?

Existing MAS design methods lack systematic consideration of these epistemological characteristics, thus often proving maladapted when directly applied to research scenarios.

#### Limitation 3: Blurred Human-AI Collaboration Boundaries

In Research MAS, the role division between human researchers and AI Agents is a core design issue:
- Which tasks can be fully automated?
- Which tasks require human leadership with AI providing only assistance?
- Which tasks need human "insight intervention," and what are the timing and methods of such intervention?

The answers to these questions are not fixed but **highly dependent on task nature**. However, existing MAS design methods often treat "automation" as the default goal, lacking a refined analytical framework for human-AI collaboration boundaries.

The result is: either over-automation, making AI do theory construction work it's not good at, producing shallow outputs; or over-conservatism, making humans do extensive mechanical work, resulting in low efficiency. We need a framework that can **systematically guide the design of human-AI collaboration boundaries**.

### The Cynefin Framework: Problem Nature Determines Method Selection

Facing these limitations, what we need is not another set of technical architecture patterns but a **decision framework**: when facing research tasks of different natures, how to determine what kind of MAS design should be adopted?

Dave Snowden's **Cynefin Framework** (pronounced "kuh-NEV-in," Welsh for "habitat") is precisely such a framework. Originally designed for organizational management and decision-making, its core insight is: **the nature of problems determines the appropriate decision pattern**. Cynefin divides decision contexts into five domains:

- **Clear domain**: Clear cause-and-effect relationships, best practices exist
- **Complicated domain**: Cause-and-effect relationships exist but require expert analysis
- **Complex domain**: Cause-and-effect relationships can only be identified retrospectively, requiring exploration
- **Chaotic domain**: Cause-and-effect relationships are indiscernible, requiring immediate action
- **Disorder domain**: Uncertain which domain one is in

Each domain corresponds to different decision patterns (Sense-Categorize-Respond, Sense-Analyze-Respond, Probe-Sense-Respond, Act-Sense-Respond), which guide us to adopt fundamentally different approaches in different contexts.

### Value of the Cynefin Framework for Research MAS Design

Introducing the Cynefin framework into Research MAS design, we gain the following key capabilities:

#### Value 1: Contextualized Decision Guidance

Cynefin tells us: **there is no "one-size-fits-all" design method**. A literature search task (Clear domain) and a theoretical framework construction task (Complex domain) are fundamentally different, requiring completely different MAS design strategies.

The framework provides a **contextual diagnostic tool**: by determining which domain a task belongs to, we can determine:
- What degree of automation should the task have?
- Where should humans intervene?
- How should data flow be organized?
- How should quality be evaluated?

This contextualized guidance is precisely what existing MAS design methods lack.

#### Value 2: Distinguishing Essential Differences in Problems

The Cynefin framework helps us identify the **essential differences** rather than superficial differences between research tasks. For example:

- **"Download a batch of archival files"**: This is a Clear domain task, with clear cause-and-effect relationships (given URL → download file), fully automatable.
- **"Assess a country's digital sovereignty level"**: This is a Complicated domain task, with clear evaluation indicators, but requiring expert-level information search and judgment.
- **"Construct a theoretical framework for analyzing South African social classes"**: This is a Complex domain task, requiring exploratory research, with patterns emerging only during the process, human insight indispensable.
- **"Conduct unprecedented fieldwork"**: This is a Chaotic domain task, requiring establishing initial order through field action to create new data.

Identifying these essential differences enables us to design **fundamentally different MAS architectures** for different tasks, rather than attempting to use one "universal architecture" for all situations.

#### Value 3: Clarifying the Necessity of Human Intelligence Intervention

The Cynefin framework clearly reveals: **in certain domains, human intelligence is irreplaceable**.

In the **Clear domain**, AI can execute fully automatically; in the **Complicated domain**, AI can serve as an expert system with humans primarily reviewing results; but in the **Complex domain**, humans must lead **pattern recognition** and **theory construction**, with AI only assisting material preparation. This is not a limitation of technical capabilities but determined by **problem nature**: Complex domain insights are emergent and cannot be generated through predefined algorithms.

This recognition is crucial for designing Research MAS: it prevents us from excessively pursuing automation, helps us identify **key points for human intervention**, and design appropriate interfaces and workflows for these intervention points.

**(End of Part 1)**
# Part 2: Conceptual Framework

In Part 1, we delineated the scope of "Research-Oriented MAS"—a class of multi-agent systems aimed at knowledge discovery, operating on unstructured qualitative materials, and functioning within the research process itself. We also identified a core problem: existing MAS design methodologies lack systematic guidance on "what should be built."

The task of Part 2 is to establish an analytical framework to address this question. We will introduce the concept of "Business Architecture," reinterpret the Cynefin framework in the research context, and reveal the essence of the research process—the evolutionary path of Domain Decomposition.

---

## 2.1 Introducing the Concept of "Business Architecture"

### 2.1.1 What Problems Does Technical Architecture Solve?

In our previous research ("Architectural Analysis of Declarative Multi-Agent Systems"), we conducted an in-depth analysis of the technical architecture layer of Research MAS:

- **Agent Blueprint Pattern**: Defining agent behavior using natural language, enabling declarative design
- **Three-Layer Separation Principle**: Clear separation of the behavior definition layer (prompts/), domain knowledge layer (references/), and runtime data layer (data/)
- **File System Data Bus**: Agents pass data through agreed-upon directory structures and file formats
- **Intelligent Runtime Environment**: Claude Code understands natural language intent and intelligently selects execution methods
- **Data-Driven Behavior**: Changing system behavior by modifying externalized reference data, rather than modifying agent definitions

These technical architecture patterns answer the "How to build" question—how to implement a maintainable, extensible, declarative multi-agent system. They are proven engineering practices that provide reusable implementation mechanisms.

However, when we face a new research task, these technical architecture patterns do not directly tell us:

- **How many stages should a research task be divided into?**
- **What does each stage do? In what order are they executed?**
- **Which parts require human intervention? When?**
- **How does data flow and transform between stages?**
- **How do we judge whether a task is suitable for full automation or requires human-AI collaboration?**

These questions belong to another level of architectural decision-making.

### 2.1.2 What is Business Architecture?

We call this level **Business Architecture** (Research Process Architecture).

**Definition:**

> The **logical decomposition** and **process orchestration** of research tasks, specifying the **stage division**, **task sequence**, **data flow**, **human-AI collaboration points**, and **knowledge transformation pathways** required to accomplish research objectives.

Business Architecture focuses on the logical structure of the research process, not implementation details. It answers the "What to build" and "Why" questions:

- **What**: What processing stages should the system contain, and what responsibilities does each stage bear
- **Why**: Why divide it this way, what principles are the basis

### 2.1.3 The Relationship Between Business Architecture and Technical Architecture

| Dimension | Business Architecture | Technical Architecture |
|-----------|----------------------|------------------------|
| **Focus** | What & Why | How |
| **Level** | Research Logic | Implementation Mechanism |
| **Example** | "Three-stage process: Data Collection → Structured Analysis → Report Generation" | "Agent Blueprint Pattern," "File System Data Bus" |
| **Determining Factor** | Nature of research problem (Cynefin domain) | Engineering principles and technical capabilities |
| **Designer** | Researcher + AI Architect | AI Architect |
| **Stability** | Varies by problem, highly customized | Relatively stable, reusable across projects |
| **Reusability** | Reusable among similar problems | Reusable among different problems |

The relationship between the two is:

1. **Technical Architecture Provides Implementation Capability**: The declarative architecture provided by AgentForge is a universal platform that can implement multiple different business architectures
2. **Business Architecture Determines Usage Pattern**: For specific research problems, designers choose how to leverage technical architecture capabilities to construct research workflows
3. **Good Technical Architecture Enables Diverse Business Architectures**: The flexibility of technical architecture is reflected in its ability to support multiple business architectures, rather than constraining designers' choices

**Analogy**: If technical architecture is like a programming language, business architecture is the program written in that language. The Python language is stable and universal (technical architecture), but what program you write in Python and how you organize the logic depends on the specific problem you want to solve (business architecture).

### 2.1.4 Why Do We Need a Business Architecture Framework?

The current predicament is: **Business architecture design lacks systematic methodology**.

When designing Research-Oriented MAS, researchers often rely on intuition or experience:
- "This task seems like it can be divided into collection and analysis steps"
- "This part feels like AI can't do it well, better handle it manually"
- "Should we do preliminary research first, then deep analysis?"

This intuitive design sometimes works, but lacks:
- **Systematicity**: No clear judgment criteria, different people make different designs
- **Transferability**: Experience is difficult to share, every project requires re-exploration
- **Assessability**: Unable to judge whether the design is reasonable, can only "try and see"

We need a framework that provides a **systematic methodology for business architecture design**. This framework should:
1. Help us **understand the nature of research tasks**
2. Guide us to **select appropriate process structures**
3. Clarify **boundaries of human-AI collaboration**
4. Reveal **evolutionary laws of the research process**

The Cynefin framework is precisely such a tool.

---

## 2.2 Reinterpreting the Cynefin Framework in the Research Context

The Cynefin framework was originally proposed by Dave Snowden to help leaders make appropriate decisions in environments of varying complexity. It divides decision-making environments into five domains: Clear (simple), Complicated (complicated), Complex (complex emergent), Chaotic (chaotic), and Disorder (disorder). Each domain has different causal relationship characteristics and therefore requires different decision-making patterns.

However, to apply Cynefin to the business architecture design of Research-Oriented MAS, we need to conduct an **important conceptual reinterpretation** of the framework.

### 2.2.1 Redefining Core Concepts

The original concepts of the Cynefin framework were designed for organizational management and decision-making:

| Cynefin Original Definition | Reinterpretation in Research Context |
|----------------------------|-------------------------------------|
| **System** = Decision/management environment (organization, market, team) | **System** = Research process itself |
| **Action** = Organizational intervention/policy implementation/management measures | **Action** = Research activities (especially data creation activities) |

**Why is this redefinition crucial?**

In the original Cynefin, the system is external, a managed object (such as an organization, a market). However, in the context of Research-Oriented MAS:

- The system we develop **does not directly act on research subjects** (such as South African society, digital sovereignty policies)
- The system we develop **acts on the research process**, **indirectly** producing knowledge about research subjects by assisting the research process
- The boundary of the "system" is **the researcher's cognitive process and knowledge production activities**

This redefinition changes how we understand the four domains. We are not using Cynefin to analyze the nature of research subjects, but to analyze **the types of activities required to complete research tasks**.

### 2.2.2 Projecting the Four Domains in the Research Context

Based on this redefinition, let's re-examine the four main domains of Cynefin:

#### Clear Domain: Routine Information Processing

**Causal Relationships**: Clear and fully predictable

**Information State**: Structurally existing, can be obtained without understanding or judgment

**Research Activity Examples**:
- Downloading files from public URLs
- Transcribing audio recordings to text
- Converting PDF files to Markdown format
- Extracting metadata from literature according to rules (title, author, year)

**Decision Pattern**: Sense-Categorize-Respond
1. **Sense**: Identify task type ("This is a file download task")
2. **Categorize**: Classify into known standard procedure ("Standard procedure for downloading HTTP resources")
3. **Respond**: Execute standard procedure

**AI Capability**: Fully automated execution, no human intervention required

**Human Role**: Define task objectives, verify result correctness

**Key Characteristic**: Tasks can be completely programmed, results are deterministic

#### Complicated Domain: Structured Analysis

**Causal Relationships**: Exist but are not immediately obvious, require expert analysis to understand

**Information State**: Information exists, but requires application of analytical frameworks or professional knowledge to interpret

**Research Activity Examples**:
- Assessing a country's digital sovereignty status according to a predefined indicator system
- Applying a specific theoretical framework (such as Marxist class analysis) to encode texts
- Using structured literature review methods to organize the research status of a field
- Scoring policy documents according to clear evaluation criteria

**Decision Pattern**: Sense-Analyze-Respond
1. **Sense**: Collect and understand data
2. **Analyze**: Apply analytical framework, exercise professional judgment
3. **Respond**: Draw conclusions based on analysis

**AI Capability**: Can operate as an "expert system," applying human-defined frameworks for analysis

**Human Role**:
- **Design Phase**: Define analytical frameworks, scoring standards, judgment rules
- **Execution Phase**: Usually can be delegated to AI, but requires human review
- **Evaluation Phase**: Verify analysis quality, check whether framework was correctly applied

**Key Characteristic**: There exists a "right method," but there may be multiple effective paths (good practices rather than a single best practice)

#### Complex Domain: Emergent Theory Construction

**Causal Relationships**: Exist, but can only be identified retrospectively

**Information State**: Information exists, but its meaning and patterns can only emerge through integrative understanding

**Research Activity Examples**:
- Constructing an applicable class analysis theoretical framework for a specific country (universal frameworks don't apply)
- Identifying key contradictions and core variables from extensive fieldwork materials
- Identifying research trends in literature reviews that have not yet been explicitly articulated
- Making editorial judgments: selecting the 10 most important news items for a weekly

**Decision Pattern**: Probe-Sense-Respond
1. **Probe**: Conduct exploratory research, prepare materials
2. **Sense**: Identify emerging patterns and associations in materials
3. **Respond**: Construct theoretical frameworks or make judgments based on identified patterns

**AI Capability**:
- Can assist with material preparation and preliminary organization (Probe)
- **Cannot replace humans in pattern recognition and theory construction** (Sense)
- Can conduct subsequent work based on human-determined frameworks (Respond)

**Human Role**:
- **Core and irreplaceable**: Identifying emergent patterns, constructing theoretical frameworks, making value judgments
- **Exercising creative insight**: "Eureka moments" of theoretical innovation
- **Integrating multi-source information**: Seeing deep connections beneath surface texts

**Key Characteristics**:
- Answers don't exist beforehand, need to be "discovered" or "created" during the process
- Cannot be obtained by applying existing frameworks; frameworks themselves need to be constructed

#### Chaotic Domain: Creative Data Generation

**Causal Relationships**: Unidentifiable at the system level

**Information State**: **Basically non-existent**—this is the most critical characteristic of the Chaotic domain

**Research Activity Examples**:
- Conducting fieldwork in Rongjiang County, creating primary data through interviews, observation, and document collection
- Excavating unstudied historical archives, making them usable research materials
- Conducting original in-depth interviews, obtaining previously non-existent oral history materials
- Participatory action research: researchers intervene in practice and observe

**Decision Pattern**: Act-Sense-Respond
1. **Act**: **Immediate action**, creating information and order through action
2. **Sense**: Perceive feedback and emerging patterns in action
3. **Respond**: Adjust action strategy based on perception

**AI Capability**:
- **Almost cannot lead**: The core of the Chaotic domain is "creating non-existent data," which AI cannot accomplish
- **Can only assist with Clear subtasks**: Such as transcribing interview recordings, organizing field notes
- **Cannot replace physical intervention**: Fieldwork, archive excavation require human presence

**Human Role**:
- **Absolutely dominant** (95%+ of core work)
- Enter physical spaces, establish social relationships
- Create new data and knowledge through practice
- Maintain flexibility in high uncertainty

**Key Characteristics**:
- The **information itself needed to complete the task does not exist**
- Cannot be completed by searching or analyzing existing materials
- **Action precedes understanding**: Must do first, then know

**Why is "Information Existence" key?**

In the research context, the core defining characteristic of the Chaotic domain is not "causal relationships are unidentifiable" (this also exists in Complex), but that **the information needed to complete the task simply does not exist**.

- **Complex**: Information exists (such as leftist organizations' analytical articles), but requires human insight to identify patterns
- **Chaotic**: Information doesn't exist (such as the Village Super's traffic conversion mechanism, no public materials), must be created through action

This distinction is crucial for business architecture design: it determines whether a task can be completed through web search + AI analysis (Complex), or must conduct fieldwork (Chaotic).

### 2.2.3 Key Criteria for Distinguishing the Four Domains

To systematically judge which domain a research task belongs to, we summarize three key distinguishing criteria:

| Criterion | Clear | Complicated | Complex | Chaotic |
|-----------|-------|-------------|---------|---------|
| **Information Existence** | ✓ | ✓ | ✓ | ✗ |
| **Causal/Analytical Path Clear** | ✓ | ✓ | ✗ | ✗ |
| **Requires Expert Judgment** | ✗ | ✓ | ✓ | N/A |
| **Patterns Predetermined** | ✓ | ✓ | ✗ | ✗ |
| **AI Can Lead Execution** | ✓ | ✓ | ✗ | ✗ |

**First Criterion: Information Existence** (The most fundamental distinction)
- Does the information needed to complete the task already exist in accessible sources?
- If basically non-existent → **Chaotic**
- If exists → Continue judgment

**Second Criterion: Clarity of Causal/Analytical Path**
- Is the path from information to conclusion clear?
- If unclear, requires exploration → **Complex**
- If clear → Continue judgment

**Third Criterion: Need for Expert Judgment**
- Does it require applying professional knowledge and judgment?
- If not needed, standard procedures suffice → **Clear**
- If needed → **Complicated**

These three criteria form a **decision tree** (see next section), which can systematically judge which domain a task belongs to.

### 2.2.4 The Value of Reinterpretation

By reinterpreting Cynefin as a **classification framework for research processes**, we gain:

1. **Clear judgment of task nature**: Can systematically judge which domain a research task belongs to
2. **Guidance for method selection**: Different domains require different methods and MAS design strategies
3. **Clarification of human-AI boundaries**: Clearly know which domains AI can lead, which require human intervention
4. **Reasonable setting of quality expectations**: Different domains have different quality standards and possibility boundaries

Next, we will transform this theoretical framework into practical tools.

---

## 2.3 Domain Classification Decision Tree

To transform the theoretical framework into a practical tool, we need a **systematic judgment method** that helps researchers and system designers quickly and accurately determine which Cynefin domain a research task belongs to.

### 2.3.1 Three-Question Decision Tree

```
Question 1: Does the information needed to complete the task already exist?
├─ Essentially does not exist → Chaotic domain
│   └─ Requires creative action to generate new data
│       Examples:
│       - Traffic conversion mechanism of Rongjiang Village Super (requires field research)
│       - Unpublished internal organizational operations (requires in-depth interviews)
│       - Unresearched historical archives (requires archival excavation)
│
└─ Already exists (accessible through search, literature, public materials) → Continue judgment
    │
    Question 2: Is the causal relationship/analytical path from information to conclusion clear?
    ├─ Clear (know "how to analyze") → Continue judgment
    │   │
    │   Question 3: Does it require expert-level judgment and interpretation?
    │   ├─ No → Clear domain
    │   │   └─ Standard process can handle, no judgment needed
    │   │       Examples:
    │   │       - Download file at specified URL
    │   │       - Transcribe audio to text
    │   │       - Extract literature metadata in fixed format
    │   │
    │   └─ Yes → Complicated domain
    │       └─ Analysis required but path is clear
    │           Examples:
    │           - Apply DSI indicator system to assess digital sovereignty
    │           - Code text using established theoretical framework
    │           - Evaluate policy documents according to scoring criteria
    │
    └─ Not clear (don't know "what analytical lens to use") → Complex domain
        └─ Exploration needed, patterns must emerge
            Examples:
            - Construct theoretical framework for class analysis in South Africa
            - Identify emerging research trends not yet explicit in literature
            - Editorial judgment: select 10 key news items for weekly newsletter
```

### 2.3.2 Detailed Explanation of Judgment Criteria

#### Criterion 1: Information Existence

**Judgment Question**: "Does the critical information needed to complete this task already exist somewhere, accessible through search, reading, analysis, or other means?"

**Meaning of "exists"**:
- Information has been recorded (text, audio, video, database, etc.)
- Information can be accessed (publicly published, purchasable, obtainable through application)
- Information creation does not depend on the researcher's intervention

**Meaning of "does not exist"**:
- Information has not been recorded; it exists in people's minds or undocumented practices
- Information generation requires researcher intervention (interviews, observation, archival excavation)
- Even if information "objectively exists," there is no channel to access it (e.g., requires establishing field relationships)

**Comparative Cases**:

| Task | Information Existence | Reasoning | Domain |
|------|---------------------|-----------|---------|
| Analyze the ideology of a leftist organization | Exists | Organization has published numerous analytical articles accessible online | Complex/Complicated |
| Understand Village Super traffic conversion mechanism | Does not exist | Conversion mechanism not public, requires field interviews with grassroots officials and operators | Chaotic |
| Assess a nation's digital sovereignty level | Exists | Policy documents, news reports, academic analyses are abundant | Complicated |
| Compile all historical articles of a journal | Exists | Articles already published, downloadable via URL | Clear |

**Why is this the first criterion?**

Because it determines the **fundamental nature of research activity**:
- If information does not exist, research is fundamentally a **data creation activity**, which is the core characteristic of the Chaotic domain
- If information exists, research is a **data analysis/organization activity**, entering one of the other three domains

#### Criterion 2: Clarity of Analytical Path

**Judgment Question**: "From existing information to research conclusions, is the analytical path clear? Do we know 'how to analyze'?"

**Meaning of "clear"**:
- An applicable analytical framework or theoretical tool exists
- Analysis steps can be planned in advance
- We know what specific information to collect and how to judge and score
- The research question can be **operationalized** into specific analytical dimensions and indicators

**Meaning of "not clear"**:
- Uncertain which theoretical perspective to use
- Analytical framework needs to be "discovered" or "constructed" during the process
- Key variables and causal mechanisms need to be explored and identified
- Research question is currently "open-ended"

**Comparative Cases**:

| Task | Path Clarity | Reasoning | Domain |
|------|-------------|-----------|---------|
| Assess Nepal using DSI indicators | Clear | 16 indicators defined, each with explicit scoring rules | Complicated |
| Construct class analysis framework for South Africa | Not clear | Don't know which framework to use; must read materials before determining applicable theoretical perspective | Complex |
| Download specified file list | Clear | Standard HTTP download process | Clear |
| Select 10 key news items for weekly newsletter | Not clear | "Importance" difficult to define in advance; requires holistic understanding and editorial judgment | Complex |

**Why is this the second criterion?**

It distinguishes two types of information processing activities:
- **Path clear** → Task is "execution/application," enters Clear or Complicated
- **Path not clear** → Task is "exploration/discovery," enters Complex

#### Criterion 3: Need for Expert Judgment

**Judgment Question**: "Does completing the task require applying professional knowledge, experience, and judgment?"

This criterion is only used when the **path is clear**, to distinguish between Clear and Complicated.

**Meaning of "requires expert judgment"**:
- Requires understanding domain-specific concepts
- Requires choosing among multiple "good" options
- Requires adjusting standards according to context
- Scoring/classification rules are explicit, but application requires interpretation

**Meaning of "does not require expert judgment"**:
- Anyone can complete it by following the operation manual
- Rules are mechanical and require no interpretation
- No gray areas or boundary cases exist

**Comparative Cases**:

| Task | Requires Expert Judgment | Reasoning | Domain |
|------|------------------------|-----------|---------|
| Assess digital sovereignty using indicators | Yes | Judging "whether a country has implemented data localization" requires understanding policy texts; gray areas exist | Complicated |
| Transcribe audio to text | No | Pure speech recognition, no need to understand content | Clear |
| Download file at specified URL | No | Standard HTTP operation | Clear |
| Extract literature metadata by template | No (if format is standardized) | Mechanically identify title, author, year fields | Clear |

### 2.3.3 Decision Tree Usage Process

**Step 1**: Clarify the specific task
- Don't ask "what domain does this research project belong to" (too macro)
- Instead ask "what domain does this **specific task** (e.g., 'search for organizational activities,' 'construct analytical framework') belong to"

**Step 2**: Apply the three-question decision tree
- Strictly answer the three questions in order
- Don't skip: each question's answer determines whether to proceed to the next question

**Step 3**: Identify the task's domain
- Based on the decision path, determine which domain the task belongs to

**Step 4**: Select the corresponding MAS design strategy
- Each domain corresponds to different business architecture patterns (see Section 2.4 and Part Three)

### 2.3.4 Boundary Cases and Gray Zones

**Case 1: Tasks spanning multiple domains**

A research project often contains multiple sub-tasks belonging to different domains. For example:

South Africa class analysis project:
- Collect leftist organization articles → **Clear** (information exists, path clear, no judgment needed)
- Construct analytical framework → **Complex** (path unclear, requires human insight)
- Apply framework for in-depth analysis → **Complicated** (path clear, requires expert judgment)

**Handling method**: Decompose tasks, judge the domain for each sub-task separately, then design corresponding business architectures.

**Case 2: Domain changes with research progress**

During the research process, the same "large task" may belong to different domains at different stages:

Field research project:
- Early stage: Chaotic (data does not exist, requires field creation)
- Middle stage: Complex (data now exists, need to identify patterns)
- Late stage: Complicated (framework clarified, requires structured analysis)

This **domain evolution** is not a problem but the natural law of research (see Section 2.4).

**Case 3: Judgment is disputed**

Different people may have different judgments about the domain attribution of the same task. For example:

"Assess a nation's digital sovereignty":
- View A: Complicated (has clear indicators and scoring rules)
- View B: Complex (each country's situation is different; universal indicators may not apply; requires customized analysis)

**Handling method**:
- The dispute itself reveals the nature of the task: may require a two-stage design
  - First stage: assess using universal framework (Complicated)
  - Second stage: human review, identify special cases, adjust framework (Complex)
- This is precisely the application of "domain decomposition" thinking (see next section)

### 2.3.5 Limitations of the Decision Tree

The decision tree is a **heuristic tool**, not a mechanical rule:

1. **Simplifies complexity**: Real tasks may not strictly fall into the "center" of a domain
2. **Depends on judgment**: "Does information exist," "Is the path clear" themselves require judgment
3. **Dynamic nature**: Domain attribution may change as research progresses

But the value of the decision tree lies in:
- **Providing a systematic thinking starting point**, avoiding purely intuitive approaches
- **Revealing key distinguishing criteria**, giving discussions a common language
- **Guiding design choices**, connecting theoretical framework to practice

With the domain classification tool in hand, we can now explore the dynamic evolution of the research process—domain decomposition.

---
## 2.4 Domain Decomposition: The Evolutionary Path of Research

The Cynefin framework not only helps us classify current tasks but, more importantly, reveals a profound pattern in the research process: **research is a process of domain decomposition**.

### 2.4.1 The Essence of Decomposition

#### What is Domain Decomposition?

**Definition**: The process of **progressively transforming** high-uncertainty research questions into low-uncertainty problems.

**Specific meanings**:
- **Chaotic → Complex**: Establishing initial order by creating data
- **Complex → Complicated**: Making analysis paths explicit through theoretical framework construction
- **Complicated → Clear**: Making analysis programmable through standardization (less common)

#### Decomposition is Not Simplification

It's important to understand: **domain decomposition is not the same as simplifying research questions**.

- **Simplification** means losing complexity, reducing depth
- **Decomposition** means **adding structure**, **reducing uncertainty**, while maintaining (or even increasing) depth

Analogy:
- Simplification: Reducing a complex topographic map to a schematic diagram (losing information)
- Decomposition: Building a coordinate system and measurement standards for complex terrain (adding structure, making it analyzable)

#### Decomposition is Knowledge Accumulation

Each domain decomposition is accompanied by **knowledge increase**:

- **Chaotic → Complex**: Knowledge increase = creating firsthand data that didn't exist before
- **Complex → Complicated**: Knowledge increase = constructing an applicable theoretical framework
- **Complicated → Clear**: Knowledge increase = distilling reusable best practices

Research progress is this process of knowledge accumulation.

#### Why is Domain Decomposition Critical for MAS Design?

1. **Guides business architecture design**: Different domains require different MAS patterns and human-AI collaboration strategies
2. **Determines human intervention points**: Domain transitions typically require critical human intervention (e.g., from Complex to Complicated)
3. **Optimizes research efficiency**: Early decomposition to AI-dominant domains (Complicated/Clear) frees up human energy
4. **Ensures research quality**: Applying appropriate methods in appropriate domains, avoiding "premature simplification" or "refusal to decompose"

Understanding domain decomposition is understanding **the natural evolutionary laws of the research process**.

### 2.4.2 Four Decomposition Stages

Let's examine in detail the four key transition stages from Chaotic all the way to Clear. For each stage we'll analyze: **trigger conditions**, **decomposition mechanism**, **decomposition results**, **MAS design strategy**, and **real-world cases**.

---

#### Stage 1: Chaotic → Complex (Establishing Initial Order)

**Trigger Conditions:**

A task is in the Chaotic state, meaning:
- The research field **lacks an existing knowledge foundation**
- Critical information **does not exist** in literature, archives, or public materials
- Causal relationships are completely unclear
- Research cannot progress through searching and analyzing existing materials

**Decomposition Mechanism:**

**Core: Human action creates data**

- **Critical human role**:
  - Conducting fieldwork (on-site interviews, participant observation, relationship building)
  - In-depth interviews (creating oral history materials)
  - Archival excavation (making previously unstudied historical materials accessible)

- **Creating new data**:
  - Generating firsthand materials that **did not exist** before
  - Transforming tacit knowledge (in people's minds, in practice) into explicit materials

- **AI assistance boundaries**:
  - AI **cannot lead** data creation (information is not on the internet)
  - AI can only handle **Clear subtasks**: transcribing interview recordings, organizing field notes into structured documents, preliminary coding

**Decomposition Results:**

When the following conditions are met, a task moves from Chaotic into Complex:

✓ Accumulated **sufficient quantity** of firsthand data (how much is "sufficient" depends on the research question)
✓ Beginning to see **preliminary patterns and associations**
✓ Can pose **theoretical questions** (from "don't know what to ask" to "know what to ask")
✓ Decision-making mode shifts from **Act-Sense-Respond** (act first, ask later) to **Probe-Sense-Respond** (can begin purposeful probing)

**MAS Design Strategy:**

- **Principle: Human absolutely dominant, AI minimally assistive**
- **Don't do**:
  - Don't try to have AI lead data creation
  - Don't assume web search can replace fieldwork
  - Don't structure prematurely (forcing classification when patterns haven't emerged)

- **Should do**:
  - Focus on tool support for **data recording and management**
  - Design AI-assisted **Clear subtasks**:
    - Automatic audio transcription
    - Formatting and organizing field notes
    - Preliminary thematic tagging (human review)
  - Maintain **process flexibility**, don't preset fixed stages

**Real Case: Rongjiang Village Super Research**

**Characteristics of Chaotic state**:
- **Core question**: "How does digital technology truly support rural revitalization?"
- **Information gaps**:
  - Village Super is a new phenomenon, no in-depth academic research
  - Key mechanisms not public: Actual monthly traffic data? Where does traffic come from? How does the county operate the self-media matrix? How does traffic convert to economic benefits? How do villages participate?
  - Existing materials too superficial: news reports, promotional materials, no deep analysis
- **Unclear causality**:
  - No obvious GDP change
  - Tourism revenue increased, but distribution mechanism unknown
  - Traffic conversion path unclear

**Act (action creates data)**:
- On-site research in Rongjiang County
- Interviews: grassroots officials, villagers, self-media operators, merchants
- Observation: Village Super venue, e-commerce operations, village changes
- Document collection: internal materials, operational data

**Sense (sensing through action)**:
- Identifying **key variables** during research:
  - Traffic source structure (short video platforms, mainstream media, self-media)
  - Conversion mechanisms (e-commerce, tourism, branding)
  - County-level coordination vs. village-level autonomy
- Preliminary patterns emerging: "traffic economy" + "cultural subjectivity"

**Result: Entering Complex domain**
- Abundant firsthand data obtained
- Can begin exploring theoretical frameworks (how to understand this phenomenon)
- Next step: Construct analytical framework (Complex → Complicated)

---

#### Stage 2: Complex → Complicated (Theoretical Framework Establishment)

**Trigger Conditions:**

A task is in the Complex state, meaning:
- **Have sufficient materials and data** (from Chaotic stage or literature collection)
- But **analysis path unclear**: don't know what theoretical perspective to use
- Need theoretical framework to "see" patterns
- Generic frameworks don't apply, need to construct customized framework

**Decomposition Mechanism:**

**Core: Human insight constructs framework**

- **Critical human role**:
  - **Deep reading**: Immersing in materials, reading repeatedly
  - **Dialogue and exchange**: Discussing with experts, hearing different perspectives
  - **Theoretical exploration**: Trying different theoretical tools, seeing which "fits"
  - **Identifying emergent patterns**: Seeing key contradictions, core variables, causal mechanisms
  - **Framework clarification**: Transforming insights into **operational analytical frameworks**

- **Framework components**:
  - Core concepts and categories
  - Analytical dimensions (e.g., dimensions of class analysis: ownership of means of production, exploitation relations, political power)
  - Key question list
  - (Possibly) indicators and evaluation criteria

- **AI assistance boundaries**:
  - AI can do **preliminary research** (collect materials, organize literature)
  - AI **cannot replace** humans in creative framework construction
  - This is the **irreplaceable core human value** in the Complex domain

**Decomposition Results:**

When the following conditions are met, a task moves from Complex into Complicated:

✓ Determined **applicable theoretical framework**
✓ Analysis path becomes **clear**: know what information to collect, how to analyze
✓ Can define **specific analytical dimensions and indicators**
✓ Decision-making mode shifts from **Probe-Sense-Respond** (exploration) to **Sense-Analyze-Respond** (applying framework analysis)

**Key transformation**:
- Before: "Don't know how to analyze this pile of materials"
- After: "Use XX framework, analyze from XX dimensions"

**MAS Design Strategy:**

**Core pattern: "Complex-to-Complicated Transformation" (domain transition pattern)**

```
[AI: Preliminary Research] → [Human: Framework Construction] → [AI: Structured Analysis]
      (Complex domain)              (Insight intervention)            (Complicated domain)
```

**Phase A: AI-assisted preliminary research (Complex-AI)**
- Collect relevant materials (literature, news, reports)
- Preliminary organization by topic
- Generate overview, help humans quickly understand the big picture
- **Output**: Comprehensive material package (Markdown reports + JSON summaries)

**Phase B: Human intervention to construct framework (Complex-Human)** ← **Critical point of domain decomposition**
- Read materials
- Exchange with experts
- Form insights
- **Decide theoretical framework** (this is creative work, AI cannot replace)
- **Output**: Clearly articulated theoretical framework document

**Phase C: AI executes structured analysis (Complicated-AI)**
- Based on human-determined framework
- Re-collect targeted data (around framework's core concepts)
- Apply framework for in-depth analysis
- Generate structured report
- **Output**: Framework-based in-depth analysis report

**Design points**:
1. **Complete decoupling**: Phase A and Phase C don't wait for humans, humans aren't rushed
2. **Clear interfaces**: Human output (theoretical framework) must be explicitly articulable and documentable
3. **Flexible timing**: Humans can spend days, weeks thinking, doesn't affect system design
4. **Irreversible decomposition**: Once framework determined, subsequent analysis stays in Complicated, doesn't return to Complex

**Real Case: South Africa Class Analysis**

**Characteristics of Complex state**:
- **Question**: "How to understand South Africa's class structure and contradictions?"
- **Information exists**: Leftist organizations published extensive analysis articles, academic research, historical materials
- **Dilemma**:
  - Cannot simply apply generic class analysis framework (South Africa has special history: apartheid, colonial legacy)
  - Need theoretical perspective to grasp key points
  - Theoretical framework cannot be predetermined

**Phase A: Preliminary Research (Complex-AI)**
- AI collects:
  - Leftist organizations (e.g., NUMSA) conjunctural analysis
  - Academic literature: South African political economy research
  - Historical materials: apartheid history, post-apartheid transition
  - News reports: current social contradictions
- AI organizes: categorized by theme (economy, politics, race, labor)
- AI generates overview: help humans quickly understand

**Phase B: Human insight (Complex-Human)** ← **Domain decomposition point**
- **Deep reading**: Researcher reads materials
- **Key insights**:
  - Race issue is not just "cultural" but **economic foundation**
  - Land ownership highly concentrated in white hands (historical legacy)
  - Economic structure exhibits **neo-colonialism** characteristics (external dependency)
  - Race and class are **intertwined** (cannot be analyzed separately)
- **Exchange with experts**: Discuss with scholars familiar with South Africa
- **Framework determined**: "Neo-colonialism and racial capitalism" perspective
  - Core dimensions: land ownership, economic dependency, race-class intersection, political power
- **Output**: Theoretical framework document (2-3 pages, clearly articulated)

**Phase C: Structured Analysis (Complicated-AI)**
- Based on "neo-colonialism" framework, AI analyzes in depth:
  - **Land ownership structure**: statistical data, policy analysis
  - **Economic dependency relations**: export structure, foreign capital control
  - **Race-class intersection**: income distribution, employment structure
  - **Political power distribution**: ANC policies, elite composition
- AI generates structured report:
  - Detailed analysis of each dimension
  - Data and material citations for support
  - Conforms to academic writing standards

**Result**:
- Completed profound class analysis
- Grasped South Africa's **specificity** (not applying generic framework)
- Framework itself may be a **theoretical contribution**

**Why is this transition so critical?**

Complex → Complicated transition is the **most critical intellectual leap** in research:
- From "chaos" to "order"
- From "don't know how to look" to "know how to analyze"
- From "AI can't help" to "AI can assist extensively"

This transition **must be completed by humans**, but **MAS can maximize assistance**:
- Early stage: AI collects materials, saves human time
- Later stage: AI executes analysis, amplifies human insight's effect

---

#### Stage 3: Complicated → Clear (Standardization and Automation)

**Trigger Conditions:**

A task is in the Complicated state, and:
- Analysis framework is already **mature and stable**
- After multiple repeated applications, analysis steps can be **standardized**
- No longer requires expert-level judgment (or judgment points reduced to very few)
- Task has **high repeatability** (e.g., need to evaluate 50+ countries, analyze 100+ cases)

**Important prerequisite**: This step **is not always necessary**.

Many research tasks remain in the Complicated domain sufficiently, don't need (and shouldn't) decompose to Clear.

**Decomposition Mechanism:**

**Core: Process standardization and rule-making**

- **Expert judgment → Explicit rules**:
  - Transform "places requiring judgment" into "if-then rules"
  - Distill "judgment standards" into "scoring rules"

- **Toolification**:
  - Develop reusable analysis tools/templates
  - Solidify analysis process into standard operating procedures (SOP)

- **Best practice establishment**:
  - Converge from "multiple good practices" to "single best practice"

**Decomposition Results:**

When the following conditions are met, a task moves from Complicated into Clear:

✓ Analysis becomes **executing standard process**, almost no judgment needed
✓ Can be **highly automated**
✓ Decision-making mode shifts from **Sense-Analyze-Respond** (analysis) to **Sense-Categorize-Respond** (classification and rule application)
✓ Human role reduced to **quality spot-checking**

**MAS Design Strategy:**

- **Full automation execution**:
  - AI completely dominant, from data collection to result output
  - Humans define task goals and acceptance criteria, don't participate in execution

- **Batch processing**:
  - Fully leverage standardization, process large numbers of cases in parallel
  - Example: Simultaneously evaluate 50 countries, each country using same process

- **Quality spot-checking**:
  - Human role becomes "supervisor": spot-check samples, confirm AI execution meets standards
  - Only exceptional situations require human intervention

**Cautions: When should you NOT decompose to Clear?**

1. **Task repeatability not high**:
   - If only need to do 1-2 times, standardization cost not worth it

2. **Significant contextual differences**:
   - If each case is very different, forcing standardization loses quality
   - Example: Each country's political system differs greatly, can't use completely identical rules to evaluate

3. **Preserve necessary judgment**:
   - Some "expert judgment" is quality assurance, shouldn't be eliminated
   - Over-standardization → rigidity

**Case: Potential Evolution of DSI Evaluation**

**Current state: Complicated**
- Has 16 clear indicators
- Each indicator has scoring criteria
- But scoring still requires judgment:
  - "Does a country implement data localization?" requires understanding policy texts
  - Some indicators have gray areas
  - Different countries differ greatly, need flexible standard application

**If repeated 50+ times, might partially decompose to Clear**:
- **Some indicators might be standardized**:
  - "Is there dedicated data protection law?" → Simple yes/no rule
  - "Is there data breach notification requirement?" → Find specific legal provisions
- **Some indicators still need to stay in Complicated**:
  - "Government regulatory intensity on tech companies" → Requires comprehensive judgment
  - "Actual enforcement of digital sovereignty policies" → Requires understanding political context

**Result**: Hybrid mode
- Clear part: AI fully automated
- Complicated part: AI-assisted, human review

This **hybrid mode** is very common in practice: different subtasks within a system are in different domains.

---

### 2.4.3 Common Patterns of Decomposition Failure (Anti-Patterns)

Understanding the correct path of domain decomposition is equally important as understanding **patterns of decomposition failure**. These anti-patterns frequently appear in practice, leading to decreased research quality or inefficiency.

#### Anti-Pattern 1: Premature Simplification

**Manifestations**:
- Forcing **Complicated methods** in the **Complex domain**
- Applying generic frameworks when theoretical framework not yet clear
- Starting structured analysis when patterns haven't emerged

**Specific examples**:

**Case A: Abuse of generic frameworks**
- **Problem**: Need to analyze political-economic structures of 10 different countries
- **Premature simplification**: Directly use same generic class analysis framework to analyze all countries
- **Consequences**:
  - Ignores each country's specificity (e.g., South Africa's race-class intersection)
  - Analysis superficial, can't grasp core contradictions
  - "Looks systematic," actually stays on surface

**Case B: Premature structuring of field research**
- **Problem**: Conducting Rongjiang field research
- **Premature simplification**: Determine all questions in "interview outline" before research begins, strictly execute
- **Consequences**:
  - Misses unexpected discoveries (key clues emerging during interviews)
  - Cannot adjust flexibly (discovered certain direction more important, but outline already set)

**Root causes**:
- **Anxiety**: Uncertainty is uncomfortable, hope to "settle down" quickly
- **Efficiency illusion**: Think standardization = efficiency, ignore that "wrong standardization" is actually inefficient
- **Misunderstanding of AI capabilities**: Think "AI can analyze," rush to have AI intervene, ignore prerequisite human insight

**Avoidance methods**:
1. **Identify true state**: Honestly assess whether task is really in Complicated (framework clear), or still in Complex (needs exploration)
2. **Patiently wait for emergence**: Give Complex domain sufficient time, don't rush to "converge"
3. **Probe tentatively**: First try preliminary framework on small scale, adjust based on results, rather than large-scale application
4. **Preserve flexibility**: Even with preliminary framework, allow adjustment and evolution

**Judgment criterion**: "Do I truly understand the core of this problem?"
- If answer is "not yet," then still in Complex, don't rush to decompose

---

#### Anti-Pattern 2: Refusal to Decompose (Complexity Fetish)

**Manifestations**:
- Can decompose to **Complicated**, but insist on staying in **Complex**
- Each time "rediscover" framework, don't solidify knowledge
- Over-pursue "each case unique," refuse standardization

**Specific examples**:

**Case A: Repeated "discovery"**
- **Problem**: After analyzing 5 similar countries, discover they have similar political-economic patterns
- **Refusal to decompose**: When analyzing 6th country, still start from zero, don't apply already-formed framework
- **Consequences**:
  - Inefficient: Each time "reinvent the wheel"
  - Knowledge cannot accumulate: Insights from 5 studies not solidified
  - Difficult to compare: Each study uses different perspective, cannot systematically compare

**Case B: Over-customization**
- **Problem**: Do strategy consulting for each client, discover many common patterns
- **Refusal to decompose**: Insist "each client different," refuse to develop generic analysis template
- **Consequences**:
  - Cannot scale: Each project is entirely new work
  - Team knowledge difficult to transfer: New members cannot quickly get up to speed
  - Quality unstable: Depends on individual flashes of inspiration

**Root causes**:
- **Misunderstanding of "standardization"**: Think standardization = superficial, ignore that "good standardization" is solidification of depth
- **"Complexity fetish"**: Think "complex = profound," unwilling to admit some parts actually can be systematized
- **Rejection of AI**: Unwilling to let AI intervene, think only humans can do "real research"

**Avoidance methods**:
1. **Identify stable patterns**: When multiple studies discover similar patterns, consider framework-izing
2. **Distinguish core from routine**:
   - Core parts (need creativity): Keep in Complex
   - Routine parts (can be systematized): Decompose to Complicated
3. **Standardization ≠ rigidity**: Good framework is "guideline-flexible tool," not "rigid rules"
4. **Knowledge reuse**: Transform insights into transmittable, reusable analysis tools

**Judgment criterion**: "Can the core of this task be explicitly articulated?"
- If "yes," then should decompose, solidify knowledge
- If "no," then keep in Complex

---

#### Anti-Pattern 3: Over-Standardization

**Manifestations**:
- Over-decomposing **Complicated** to **Clear**
- Eliminating all expert judgment, becoming mechanical rules
- System rigidified, cannot handle edge cases

**Specific examples**:

**Case A: Rigidification of scoring system**
- **Problem**: Evaluating national digital sovereignty, originally requires expert judgment
- **Over-standardization**: Transform all scoring into mechanical rules:
  - "If has data protection law → 5 points"
  - "If not → 0 points"
- **Consequences**:
  - Cannot handle gray areas: Law exists but not enforced? Law name different but substance same?
  - Lost flexibility: Special situations cannot be specially handled
  - Superficially objective, actually distorted

**Case B: Templatization of academic writing**
- **Problem**: Generate research reports
- **Over-standardization**: Developed extremely detailed writing template, structure of every paragraph, every sentence fixed
- **Consequences**:
  - All reports "read the same"
  - Lost expressive flexibility: Some content awkward to express with template
  - Innovation suppressed: Cannot adjust expression based on content

**Root causes**:
- **Automation impulse**: Hope everything can be fully automated, ignore that some judgments are necessary
- **Efficiency supremacy**: To increase speed, sacrifice quality
- **Misjudgment of AI capabilities**: Think "AI should completely replace humans"

**Avoidance methods**:
1. **Preserve key judgment points**: Identify where "expert judgment" is quality assurance, cannot be eliminated
2. **Gradient design**: Allow system to have "flexibility": rules + exception mechanism
3. **Quality priority**: When efficiency conflicts with quality, choose quality
4. **Regular review**: Check whether standardization has led to quality decline

**Judgment criterion**: "After eliminating this judgment point, will important quality be lost?"
- If "yes," then shouldn't decompose to Clear
- Stay in Complicated, allow AI assistance but human review

---

#### Anti-Pattern 4: Ignoring Chaotic (Skipping Fieldwork)

**Manifestations**:
- When **Chaotic domain work** (creating data) needed, try to substitute with **Complex methods**
- Analyze with secondary materials, when actually need firsthand research
- Think "search online" can solve all problems

**Specific examples**:

**Case A: Substituting web search for field research**
- **Problem**: Research Rongjiang Village Super's traffic conversion mechanism
- **Ignoring Chaotic**: Don't go on-site, only search news reports and academic articles
- **Consequences**:
  - Key information simply doesn't exist in public materials (e.g., how county operates self-media matrix)
  - Analysis built on weak information foundation
  - Conclusions superficial, cannot touch core mechanisms

**Case B: Substituting literature review for original interviews**
- **Problem**: Research internal decision-making mechanism of an organization
- **Ignoring Chaotic**: Only read research literature about the organization, don't conduct interviews
- **Consequences**:
  - Literature may be outdated, inaccurate, or lack internal perspective
  - Cannot obtain "tacit knowledge" (undocumented practices)
  - Research quality limited by quality of existing research

**Root causes**:
- **Convenience preference**: Web search much easier than field research
- **Misjudgment of "information existence"**: Think "should have materials," actually don't
- **Exaggeration of AI capabilities**: Think "AI can search everything"

**Avoidance methods**:
1. **Honestly assess information existence**:
   - Does the needed information really exist?
   - Are public materials of sufficient quality and depth?
2. **Budget field work**:
   - If judge Chaotic work needed, must budget time and resources
   - Don't expect AI can "skip" this step
3. **Phase planning**:
   - Chaotic stage: Human-led, creating data
   - Complex stage: Integrate data, construct framework
   - Complicated stage: AI can extensively intervene

**Judgment criterion**: "Does this information really exist somewhere?"
- If "uncertain" or "possibly doesn't exist," then need Chaotic work
- Don't use Complex methods (search + analysis) to solve Chaotic problems (data creation)

---

### 2.4.4 Strategic Significance of Domain Decomposition

Through understanding the correct decomposition path and common anti-patterns, we gain a **strategic framework for research process design**:

1. **Plan research path**:
   - Clarify which domain current task is in
   - Plan decomposition path: which domains need to go through?
   - Design trigger conditions and mechanisms for domain transitions

2. **Optimize human-AI collaboration**:
   - In Chaotic and Complex: Human-led
   - In Complicated: Human-AI collaboration, AI can assist extensively
   - In Clear: AI-led

3. **Balance quality and efficiency**:
   - Don't decompose prematurely (lose quality)
   - Don't refuse to decompose (lose efficiency)
   - Find appropriate balance point

4. **Accumulate reusable knowledge**:
   - Solidify Complex insights into Complicated frameworks
   - Distill Complicated experience into Clear processes (cautiously)
   - Build organizational knowledge assets

**Core insight**:

> Research progress is essentially **a process of domain decomposition**. Understanding this process is understanding the intrinsic laws of knowledge production. Designing research MAS is designing a **system that supports and accelerates domain decomposition**.

---

## Summary: Establishing the Conceptual Framework

In Part 2, we established a conceptual framework for understanding and designing research MAS:

**2.1 Business Architecture Concept**:
- Distinguished "technical architecture" (How) and "business architecture" (What & Why)
- Clarified that business architecture focuses on the logical structure of research processes, determined by the nature of research questions

**2.2 Reinterpreting the Cynefin Framework**:
- Redefined "system" = research process, "action" = research activities
- Projected four domains onto research context: Clear (routine processing), Complicated (structured analysis), Complex (emergent construction), Chaotic (creative data generation)
- Established "information existence" as key distinguishing criterion

**2.3 Domain Classification Decision Tree**:
- Provided three-question decision tree: information existence → path clarity → expert judgment necessity
- Made domain classification shift from "intuitive judgment" to "systematic method"

**2.4 Domain Decomposition Theory**:
- Revealed research evolution pattern: Chaotic → Complex → Complicated → Clear
- Analyzed mechanisms, strategies, and cases of four decomposition stages
- Identified four anti-patterns of decomposition failure

**Value of the framework**:

This conceptual framework provides for research MAS business architecture design:
1. **Analytical tools**: Judge task nature
2. **Design guidance**: Choose appropriate process structure
3. **Strategic framework**: Plan research evolution path
4. **Quality assurance**: Avoid common design mistakes

In Part 3 (Exemplars as Patterns), we will transform this conceptual framework into **concrete design patterns**, demonstrating how to design MAS business architecture in different domains.

---

**(End of Part 2)**
# Part 3: Exemplars as Patterns

This section presents four exemplars, each corresponding to a domain in the Cynefin framework. These exemplars are not isolated case studies but reusable **patterns**—problem-solution pairs that recur in the design of research-oriented multi-agent systems. Each exemplar follows the standard structure of pattern language: context, problem, business architecture, MAS design, human-AI collaboration, concrete example, key design principles, variants, and domain decomposition relationships.

These exemplars emerge from real research practices, spanning domains such as digital sovereignty assessment, area studies, and fieldwork research. Together, they demonstrate how to design appropriate business architectures and MAS implementations based on the nature of research questions.

---

## 3.1 Clear Domain Exemplar: Batch Retrieval of Archival Files

### Context

Researchers need to acquire large volumes of structured or semi-structured documents from public sources as research materials. These documents exist in standard formats at accessible network resources, such as digital archives, academic journal databases, and government information websites. The location and structure of files are known, and the retrieval process requires no complex judgment, though manual operation would be extremely time-consuming due to sheer volume.

Typical scenarios include: downloading all PDF files from a historical journal, batch retrieving government gazettes, collecting historical articles from news websites, and gathering public reports from specific institutions.

### Problem

**Core Challenge**: Massive repetitive work consumes researchers' time that should be devoted to higher-value analytical activities.

**Specific Manifestations**:
- File counts may reach hundreds or thousands, requiring hours or days of manual downloading
- Need for standardized file naming and directory organization for subsequent retrieval
- May require simple format conversions (e.g., HTML to Markdown, image OCR)
- Minor technical barriers exist (e.g., handling pagination, login authentication)

**Why This is a Clear Domain Problem**:
- **Information Existence**: Files already exist at specific locations; locations are determinable
- **Clear Causality**: Visit URL → Download file → Store at designated location; steps are explicit
- **No Expert Judgment Needed**: No content evaluation, quality discrimination, or judgment required
- **Process Standardization**: The entire process can be written as a definite algorithm

### Business Architecture

```
Single-Stage Pipeline:

[Download & Organization]
    ↓
Input: URL list + Naming rules
    ↓
Processing:
  - Iterate through URLs
  - Download files
  - Name according to rules
  - Organize directory structure
    ↓
Output: Organized file collection
```

**Architectural Characteristics**:
- **Single Responsibility**: Only handles retrieval and organization, no content analysis
- **Linear Process**: Sequential or parallel execution, no complex branching
- **Deterministic**: Given same input, produces same output
- **No Human-AI Collaboration Points**: Fully automated execution

### MAS Design

**Design Choices**:
- **Agent Count**: Usually only 1 agent needed; MAS architecture may not even be necessary—a single script suffices
- **Parallelism**: Download files in parallel (optional, depends on network and server constraints)
- **Tool Dependencies**: Network request libraries (e.g., requests), file system operations
- **Execution Mode**: Batch processing

**Implementation Levels**:
- **Simplest**: Claude Code directly writes and executes Python script
- **Slightly Complex**: If multi-round debugging or login authentication needed, define a simple agent with AgentForge
- **No Complex MAS Needed**: No multi-agent collaboration, no complex state management

**Error Handling**:
- Network failure retry mechanism
- Record downloaded files, support resumption from breakpoints
- Log recording for checking omissions

### Human-AI Collaboration Points/Patterns

**Design Phase (Human-Led)**:
- Define target URL list (or URL generation rules)
- Determine file naming conventions
- Specify storage location and directory structure
- Set parallelism and rate limiting (avoid being blocked)

**Execution Phase (AI Fully Automated)**:
- No human intervention needed
- System automatically downloads, names, and organizes files
- Notifies human upon completion

**Validation Phase (Human Spot-Check)**:
- Check if file count matches expectations
- Spot-check several files to confirm content correctness
- Verify naming and organization meet specifications

**Collaboration Mode**: This is the simplest collaboration mode—human defines task, AI executes, human validates. No iteration and feedback loop.

### Concrete Example

**Case: Downloading News on China Historical Journals**

**Background**: News on China is a weekly focusing on China affairs, with all past issues stored as PDFs on the website following a fixed URL pattern. Researchers need these journals as material for analyzing media discourse evolution.

**Execution**:
1. **Human Definition**:
   - URL pattern: `https://example.com/issues/2020/week-{week}.pdf`
   - Time range: 2020-01 to 2024-10
   - Naming rule: `NoC_{year}_{week}.pdf`
   - Storage location: `./data/news-on-china/`

2. **AI Execution**:
   - Generate URL list (approximately 250 files)
   - Parallel download (10 concurrent connections)
   - Name and store according to rules
   - Generate download log

3. **Results**:
   - Time consumed: approximately 15 minutes
   - Human time saved: manual download would require approximately 3 hours
   - File organization: automatically organized by year into directories, convenient for subsequent analysis

**Key Value**: Researchers are liberated from mechanical labor and can immediately begin reading and analyzing journal content.

### Key Design Principles

1. **Clarity First**: Before execution begins, completely clarify URL list, naming rules, and storage structure. Vague definitions lead to multiple adjustments.

2. **Recoverability**: Implement resumption-from-breakpoint mechanism to avoid starting over due to network interruptions. Record list of downloaded files.

3. **Rate Control**: Respect target website's service capacity, set reasonable concurrency and request intervals, avoid being identified as malicious crawler.

4. **Integrity Verification**: After download, check if file size and format are normal, record any failed URLs for manual handling.

5. **Flexible Tool Selection**: Don't introduce complex architecture for simple tasks. If Claude Code's single session can complete it, no need to deploy AgentForge.

6. **Document Naming**: Generate a README or inventory file recording download time, source, and naming rules for long-term data traceability.

### Variants

**Variant 1a: Login Authentication Required**
- Add authentication step: save cookies or use API token
- Security consideration: credentials should not be hardcoded in scripts

**Variant 1b: Anti-Crawler Mechanisms Required**
- Add User-Agent spoofing
- Use proxy IP pools
- Add random delays to simulate human behavior

**Variant 1c: Incremental Update Mode**
- Check locally existing files
- Only download new or updated files
- Suitable for periodically updated data sources

**Variant 1d: Format Conversion Required**
- Auto-convert format after download (PDF→text, HTML→Markdown)
- This may move part of task into Complicated domain (if conversion requires judgment)

### Domain Decomposition Relationship

**Decomposition Source**: Clear domain tasks are usually **auxiliary subtasks** decomposed from higher domains.

**Typical Decomposition Paths**:
- **Chaotic → Clear**: Fieldwork (Chaotic) requires organizing large volumes of recordings → transcription task (Clear)
- **Complex → Clear**: After theoretical framework discovery (Complex), need to collect relevant literature → literature download (Clear)
- **Complicated → Clear**: Indicator assessment (Complicated) requires specific data sources → data acquisition (Clear)

**Identification Markers**: When you find yourself saying "I need all X, then I can do Y," acquiring all X is usually a Clear domain task.

**Decomposition Effect**: After automating Clear subtasks, researchers can focus on higher-domain core work. This is the most direct manifestation of efficiency improvement from domain decomposition.

---

## 3.2 Complicated Domain Exemplar: Indicator-Based Evaluation System

### Context

Researchers need to conduct systematic, structured evaluation of one or multiple research subjects. Evaluation is based on a predetermined framework containing multiple dimensions and specific indicators. Each indicator has clear data requirements and scoring standards, but applying these standards requires professional judgment and interpretation of information.

This evaluation is not simple data entry but requires understanding text semantics, comparing different sources, weighing evidence strength, and making well-founded judgments. However, the evaluation framework itself is stable, not emergent during the evaluation process.

Typical scenarios include: national digital sovereignty assessment, corporate social responsibility rating, policy impact analysis, literature quality evaluation, etc.

### Problem

**Core Challenge**: Under a clear analytical framework, collecting, interpreting, and scoring large amounts of information at an expert level is both analytically demanding and extremely time-consuming.

**Specific Manifestations**:
- Each indicator requires consulting dozens or hundreds of information sources (government websites, news reports, academic literature, legal texts, etc.)
- Requires judgment of information: Is this information credible? Does it support or oppose a certain score?
- Requires synthesizing multiple pieces of evidence for scoring: not simple "yes" or "no," but degree judgment
- Single evaluation subject may involve hundreds of specific questions, manual completion requires weeks
- If evaluating multiple subjects, need to maintain consistency in scoring standards

**Why This is a Complicated Domain Problem**:
- **Information Exists but Requires Interpretation**: Information exists on the internet but requires expert capability to understand and evaluate
- **Causality Clear but Requires Analysis**: "Country has Law A and enforces it well" → "Scores high in privacy protection dimension"—path is clear but requires analysis
- **Requires Expert Judgment**: What counts as "well enforced"? How to synthesize multiple pieces of evidence? Requires expert-like judgment
- **Framework Predetermined**: Evaluation dimensions and indicator system are pre-designed, not emergent during evaluation

**Distinction from Clear**: If evaluation is only "Does Law A exist?" (yes/no), that's Clear; but "How well is Law A executed?" requires synthesizing evidence for judgment—that's Complicated.

### Business Architecture

```
Three-Stage Pipeline:

[Stage 1: Data Collection]
    ↓
Input: Indicator definitions + Evaluation subject
    ↓
Process:
  - For each indicator, generate refined question list
  - For each question, search and collect relevant information
  - Parallelism strategy: Parallelize by indicator (indicators are independent)
    ↓
Output: Structured data (JSON) - Information set organized by indicator
    ↓
    ↓
[Stage 2: Analysis & Scoring]
    ↓
Input: Stage 1 structured data + Scoring rules
    ↓
Process:
  - For each indicator, analyze collected information
  - Apply scoring standards, provide scores and rationale
  - Parallelism strategy: Parallelize by indicator (indicator scoring is independent)
    ↓
Output: Structured data with scores (JSON)
    ↓
    ↓
[Stage 3: Report Generation]
    ↓
Input: Stage 2 scoring data + Report template
    ↓
Process:
  - Integrate all indicator results
  - Generate comprehensive report
  - Serial execution: Requires global perspective
    ↓
Output: Final research report (Markdown/PDF)
```

**Architectural Characteristics**:
- **Three-Stage Decoupling**: Each stage has clear input/output, connected through structured data contracts
- **Supports Parallelism**: Identifies parallelizable dimensions (by indicator), but doesn't mandate parallel execution
- **Knowledge Externalization**: Indicator definitions and scoring rules stored as knowledge base in references/ directory
- **Analysis-Report Separation**: Scoring is analytical (Complicated), report generation is structured (approaching Clear)

### MAS Design

**Overall Design**:
- **Agent Blueprint Count**: 3 (Research Agent, Analysis Agent, Report Writer)
- **Execution Instance Count**: Dynamically scales based on parallelism requirements
- **Data Flow**: Through strictly defined data contracts via JSON schema
- **Knowledge Base**: references/ directory stores indicator definitions, scoring standards, quality specifications

#### Stage 1: Data Collection

**Agent Type**: Research Agent

**Responsibilities**:
- Receive indicator definition and refined question list
- For each question, search relevant information (search engines, specific websites, databases)
- Collect, read, extract key information
- Output structured JSON (according to predefined schema)

**Parallelism Strategy**:
- **Parallelize by Indicator**: 16 indicators can be processed simultaneously by 16 agent instances
- **Single Subject Evaluation**: Although evaluating only one country, indicator collection doesn't interfere with each other
- **Resource Considerations**: Actual parallelism depends on computing resources and API limits

**Input Example**:
```json
{
  "indicator": "Data Localization",
  "questions": [
    "Does the country have data localization laws?",
    "What types of data are required to be stored locally?",
    "Are there exceptions for certain sectors?",
    ...
  ],
  "sources": ["government websites", "legal databases", "news"]
}
```

**Output Example**:
```json
{
  "indicator": "Data Localization",
  "findings": [
    {
      "question": "Does the country have data localization laws?",
      "answer": "Yes, the Data Protection Act 2021 requires...",
      "sources": ["url1", "url2"],
      "confidence": "high"
    },
    ...
  ]
}
```

#### Stage 2: Analysis & Scoring

**Agent Type**: Analysis Agent

**Responsibilities**:
- Receive collected data for an indicator
- Read externalized scoring rules (references/scoring_rubric.md)
- Synthesize evidence, apply rules, provide score (e.g., 1-5 points)
- Provide scoring rationale and key evidence citations

**Parallelism Strategy**:
- **Parallelize by Indicator**: Scoring for each indicator is mutually independent
- **Expert Simulation**: Each agent acts like an expert focused on a specific dimension

**Key Capabilities**:
- **Evidence Weighing**: If information from different sources conflicts, need to judge credibility
- **Degree Judgment**: Not binary judgment, but "to what extent"
- **Rule Application**: Apply abstract rules to specific situations

**Input**: Stage 1 findings JSON + scoring rule document

**Output Example**:
```json
{
  "indicator": "Data Localization",
  "score": 4,
  "max_score": 5,
  "rationale": "The country has comprehensive data localization laws...",
  "key_evidence": ["Data Protection Act 2021", "enforcement cases"],
  "limitations": "Enforcement in smaller companies is unclear"
}
```

#### Stage 3: Report Generation

**Agent Type**: Report Writer

**Responsibilities**:
- Receive scoring data for all indicators
- Read report quality specifications (references/report_standard.md)
- Write comprehensive evaluation report
- Include: total score, dimension scores, key findings, comparative analysis, policy recommendations

**Execution Mode**:
- **Serial Execution**: Requires integrating all indicators, forming global perspective
- **One-Time Generation**: No need to parallelize by parts

**Report Structure**:
1. Executive Summary (total score, core conclusions)
2. Detailed analysis by dimension
3. Strengths and weaknesses
4. Policy recommendations
5. Appendices (scoring details, data sources)

### Human-AI Collaboration Points/Patterns

**Design Phase (Human-Led)**:
- **Define Evaluation Framework**: Determine dimensions, indicators, weights
- **Formulate Scoring Rules**: Clarify scoring standards for each indicator (e.g., what 1-5 points represent)
- **Design Data Schema**: Specify structure of data at each stage
- **Write Quality Specifications**: Define what reports should look like

**Execution Phase (AI Fully Automated)**:
- All three stages executed entirely by AI
- No human intervention needed (unless errors occur)
- Execution time: single subject evaluation may take several hours (depending on indicator count and parallelism)

**Review Phase (Human Critical)**:
- **Validate Reasonableness**: Spot-check scoring for several indicators to see if sensible
- **Check Evidence**: Whether cited sources are relevant and credible
- **Assess Consistency**: If evaluating multiple subjects, whether standards are applied consistently
- **Adjust Rules**: If scoring found unreasonable, modify scoring rules rather than manually changing scores

**Iteration Mode**:
- First evaluation may expose issues in scoring rules
- After human revises rules, can rerun evaluation (or just rerun stages 2-3)
- Gradually refine evaluation system

### Concrete Example

**Case: DSI (Digital Sovereignty Index) Assessment**

**Background**: Need to evaluate a country's performance in digital sovereignty to understand its autonomy, control, and governance capacity in digital space.

**Evaluation Framework**:
- **4 Dimensions**: Data Sovereignty, Technology Sovereignty, Economic Sovereignty, Governance Sovereignty
- **16 Indicators**: 4 indicators per dimension
- **15-20 Refined Questions per Indicator**: Approximately 250-300 questions total
- **Scoring**: 1-5 points per indicator, total 80 points

**Execution Details**:

**Stage 1 (Data Collection)**:
- Launch 16 Research Agent instances (parallelize by indicator)
- Each agent responsible for collecting information for one indicator
- Access thousands of web pages (government websites, legal databases, news, academic literature)
- Time consumed: approximately 2-3 hours (parallel), would need 30-40 hours if serial

**Stage 2 (Analysis & Scoring)**:
- Launch 16 Analysis Agent instances
- Read externalized scoring standard document (references/dsi_rubric.md)
- Score each indicator and provide detailed rationale
- Time consumed: approximately 1-2 hours

**Stage 3 (Report Generation)**:
- Single Report Writer
- Integrate 16 indicator scores
- Generate 80-page comprehensive evaluation report (Markdown format)
- Time consumed: approximately 30 minutes

**Total Time**: approximately 4-6 hours (AI automated)
**Human Investment**:
- Design phase: approximately 2 weeks (define framework, scoring standards)
- Review phase: approximately 4-8 hours (read report, spot-check evidence)

**Efficiency Improvement**: If done entirely manually, single country evaluation requires approximately 2-3 weeks. AI shortens cycle to 1-2 days (most time is human review).

**Key Value**:
- **Scalability**: Once designed, can quickly evaluate multiple countries while maintaining consistent standards
- **Depth**: AI can consult far more sources than manual work, discovering overlooked information
- **Transparency**: All scoring has clear rationale and sources, traceable

### Key Design Principles

1. **Knowledge Externalization, Process Internalization**: Externalize "what to know" (indicator definitions, scoring rules) as documents, internalize "how to do" (collection, analysis processes) in Agent Blueprints. This way, modifying knowledge doesn't require changing code.

2. **Data Contract Strictness**: Stages are connected through JSON schema; schema must be strictly defined. Ambiguous data structures lead to integration difficulties between stages.

3. **Quality Specification Embedding**: Don't assume AI automatically produces high-quality output; write quality standards explicitly into agent's system prompt and references.

4. **Support Parallelism, Don't Mandate Parallelism**: Identify parallelizable dimensions (e.g., by indicator), but flexibly adjust actual execution based on resource situation. "Supports parallelism" means architecture allows parallelism, not that all agents must run simultaneously.

5. **Single-Subject Depth-First**: When DSI evaluates a single country, although there's only one subject, indicator level can be parallelized. Don't confuse "multi-subject parallelism" with "intra-subject parallelism."

6. **Clear Human-AI Boundaries**: Humans responsible for defining "what is good evaluation," AI responsible for executing evaluation. Don't let AI participate in framework design, also don't let humans manually do extensive scoring.

7. **Explainability First**: Each score must have rationale and sources, convenient for human review and questioning. Black-box scoring is unacceptable.

### Variants

**Variant 2a: Adaptive Question Generation**

Sometimes, refined questions should not be fixed but should be dynamically generated based on evaluation subject's characteristics.

**Four-Stage Pipeline**:
```
[Overview] → [Question Formulation] → [Data Collection] → [Analysis] → [Report]
```

**Additional Stages: Overview + Question Formulation**:
1. **Overview**: Conduct coarse-grained research on evaluation subject, understand basic characteristics
2. **Question Formulation**: Based on Overview results, generate customized refined question list

**Example**:
- Nepal's economy relies on agriculture, focus questions on rice industry digitalization
- Ghana's economy relies on cocoa exports, focus questions on cocoa industry chain

**Still Complicated**:
- Question generation is rule-guided (pattern matching based on Overview results)
- Doesn't require human insight intervention
- Process is deterministic: given Overview results, question generation has clear logic

**Distinction from Complex**: If question generation requires "flash of insight" theoretical insight, that enters Complex domain. But if it's just "if country X, then question type Y," this remains Complicated.

### Domain Decomposition Relationship

**Decomposition Source**: Complicated tasks usually decompose from Complex domain.

**Typical Path: Complex → Complicated**:

**Example: South Africa Class Analysis**
1. **Complex Stage**: Don't know what theoretical framework to use for analyzing South Africa (theoretical framework undetermined)
2. **Human Insight**: Determine "neo-colonialism intersecting with race" as analytical framework
3. **Decompose to Complicated**: Based on this framework, define specific analytical dimensions and indicators (land ownership, economic dependency, political power distribution, etc.)
4. **Complicated Execution**: AI conducts structured analysis based on clear framework

**Decomposition Marker**: When analytical framework changes from "needs exploration" to "already determined," task decomposes from Complex to Complicated.

**Further Decomposition: Complicated → Clear (Rare)**:

If evaluation system is highly mature, scoring judgment may be further standardized into mechanical rules.

**Example: Potential Evolution of DSI**
- **Current**: Scoring requires judgment (e.g., degree of "well executed")
- **Hypothetical**: After evaluating 50+ countries, may discover scoring patterns for certain indicators are highly regular
- **Standardization**: Solidify these patterns into explicit rules (e.g., "has law + 3+ enforcement cases = 4 points")
- **Result**: These indicator parts decompose to Clear domain (simple rules suffice)

**Note**: Most Complicated tasks don't need decomposition to Clear; over-standardization may lose necessary flexibility. Only when task is highly repetitive and pattern is stable is decomposition to Clear worthwhile.

---

## 3.3 Complex Domain Exemplar: Theoretical Framework Discovery vs. Editorial Judgment

Complex domain research tasks share a common characteristic: **required patterns or frameworks cannot be predetermined but emerge from exploration**. However, within this domain exist two different subtypes with drastically different MAS design strategies.

- **Exemplar 3a (Theoretical Framework Discovery)**: Complex problems can be **decomposed** into Complicated problems through human insight
- **Exemplar 3b (Editorial Judgment)**: Complex judgment cannot be decomposed, requires **decoupling** rather than automation

---

### Exemplar 3a: Theoretical Framework Discovery Research

#### Context

Researchers face a specific research subject (e.g., a country, social phenomenon, historical event) and need to construct an applicable theoretical framework to analyze it. Generic theoretical frameworks cannot be directly applied because the research subject's key characteristics and contradictions are not obvious and must be identified through exploration. The selection and construction of the theoretical framework itself is the core challenge of research.

This situation is common in area studies, comparative political economy, historical sociology, and other fields. The uniqueness of research subjects demands unique analytical perspectives, and these perspectives don't exist beforehand but require researcher insight.

#### Problem

**Core Challenge**: In the situation of not knowing "what framework to use," how to systematically explore and understand research subjects, ultimately forming insightful theoretical frameworks.

**Specific Manifestations**:
- Key contradictions and causal mechanisms of research subject are not obvious
- Existing theories cannot be directly applied (or application results in shallow analysis)
- Requires extensive reading and thinking to form theoretical perspective
- Once theoretical framework is determined, subsequent analysis path becomes clear
- Framework construction relies on researcher's "flash of insight" or in-depth dialogue with experts

**Why This is a Complex Domain Problem**:
- **Causality Only Visible After the Fact**: Before determining framework, don't know which factors are important; after determining framework, causal relationships become clear
- **Pattern Emergence**: Theoretical framework emerges from repeated reading of materials, cannot be preset
- **Requires Human Insight**: AI can organize materials but cannot replace creative insight of "seeing key contradictions"
- **Exploratory**: Requires Probe (collect materials) → Sense (identify patterns) → Respond (construct framework)

**Distinction from Complicated**:
- Complicated: Framework known, applying framework requires analysis
- Complex: Framework unknown, finding framework requires insight

#### Business Architecture

```
Mixed Human-AI Pipeline - Domain Transformation Pattern:

[Stage 1: Preliminary Research]
(Complex-AI)
    ↓
Input: Research subject definition
    ↓
Process:
  - Collect standardized information (basic national conditions, historical background)
  - Collect specific types of materials (e.g., leftist organization analysis, academic literature)
  - No judgment, only organize and present
    ↓
Output: Comprehensive material set (Markdown reports + JSON summaries)
    ↓
    ↓ (Decoupling point)
    ↓
[Human Insight Intervention]
(Complex-Human)
    ↓
Process:
  - Read AI-organized materials
  - Communicate with experts
  - Form theoretical insight
  - **Determine applicable theoretical framework**
    ↓
Output: Explicitly articulated theoretical framework document
    ↓
    ↓ 【Domain Decomposition Point: Complex → Complicated】
    ↓
[Stage 2: Framework-Guided In-Depth Analysis]
(Complicated-AI)
    ↓
Input: Human-determined theoretical framework
    ↓
Process:
  - Based on framework's key concepts, re-collect targeted data
  - Apply framework for structured analysis
  - Dig deeper along directions guided by framework
    ↓
Output: Structured analysis report
    ↓
    ↓
[Stage 3: Research Report Writing]
(Complicated-AI)
    ↓
Input: In-depth analysis results + Report specifications
    ↓
Output: Final research report
```

**Key Architectural Characteristics**:

1. **Domain Transformation**: Entire process is a Complex→Complicated transformation process; transformation point is human insight intervention
2. **Complete Decoupling**: After AI Stage 1 completes, humans can freely allocate time for reading and thinking, no time pressure
3. **Irreversible Decomposition**: Once theoretical framework is determined, subsequent analysis enters Complicated domain, doesn't return to Complex
4. **Clear Interface**: Human output (theoretical framework) must be explicitly documentable, becoming input for Stage 2

#### MAS Design

##### Stage 1: Conjunctural Overview (Complex-AI)

**Objective**: Provide sufficiently rich materials for humans to identify patterns and construct framework.

**Agent Type**: Preliminary Research Agent

**Collection Content** (using South Africa as example):
1. **Basic National Conditions**:
   - Population structure, economic data, political system
   - Timeline of major historical events
   - Geopolitical position

2. **Specific Angle Materials** (based on research interests):
   - Political analysis articles by leftist organizations
   - Relevant research from academia
   - Reports from mainstream and alternative media
   - Government official documents and policies

3. **Relevant Thematic Literature**:
   - Comparative research (cases of similar countries)
   - Theoretical literature (potentially applicable theoretical schools)

**Output Format**:
- Structured Markdown reports (convenient for reading)
- JSON summaries (convenient for subsequent processing)
- Organized by theme, not simple listing

**AI's Role**:
- **Information Collector**: Broadly search and collect
- **Organizer**: Classify and organize materials
- **Presenter**: Present in manner convenient for human reading
- **No Judgment**: Don't try to propose theoretical framework (AI not good at this)

##### Human Insight Intervention Point (Complex-Human) - Key to Domain Decomposition

This is the **core turning point** of the entire process.

**Human Work**:
1. **Deep Reading**: Read AI-organized materials, not skimming but deep understanding
2. **Dialogue & Thinking**: Communicate with domain experts, repeatedly think about connections between materials
3. **Identify Contradictions**: See deep contradictions and causal mechanisms beneath surface phenomena
4. **Framework Decision**: Decide what theoretical perspective to use for analysis

**Output**: Theoretical framework document, containing:
- Core concept definitions (e.g., "neo-colonialism," "racial capitalism")
- Key variable identification (e.g., land ownership, economic dependency)
- Analytical path guidance (which aspects should be examined)
- Expected causal mechanisms (hypothesized explanatory logic)

**Why This Cannot Be Automated**:
- **Emergent Nature of Insight**: Theoretical framework is "seen" from materials, not calculated
- **Creative Nature of Judgment**: Requires evaluating "whether this framework captures the essence"
- **Non-Delegable Responsibility**: Choice of theoretical perspective determines research value; this is researcher's core responsibility

**Importance of Time Decoupling**:
- Humans may need days or weeks to read and think
- Should not have pressure of AI "waiting" for humans
- Humans also should not feel rushed by AI

##### Stage 2: Framework-Guided Analysis (Complicated-AI)

**Objective**: Conduct in-depth, structured analysis based on human-determined theoretical framework.

**Agent Type**: Framework-Guided Analysis Agent

**Input**:
- Human-determined theoretical framework document
- Stage 1 collected materials (reusable)

**Analysis Process**:
1. **Targeted Re-Collection**: Based on framework's key concepts, search for more specific information
2. **Structured Analysis**: Systematically analyze along dimensions guided by framework
3. **Evidence Integration**: Synthesize multiple pieces of evidence to support or question framework's expectations

**Why This is Complicated**:
- Analysis path already clear (determined by framework)
- Requires expert-level analytical capability but not insight
- AI can play "framework-based expert analyst" role

**Output**: Structured analysis report, containing:
- Detailed analysis of each key variable
- Evidence support for causal mechanisms
- Possible counterexamples and complexities
- Insights from framework application

#### Human-AI Collaboration Points/Patterns

**Collaboration Mode: Serial Division of Labor**

```
AI (Material Preparation) → Human (Insight & Framework) → AI (In-Depth Analysis) → Human (Review & Refinement)
```

**Key Characteristics**:
1. **Complete Decoupling**: Each stage completely independent, connected through explicit document interfaces
2. **Asynchronous Collaboration**: No real-time interaction, humans can autonomously arrange time
3. **Utilize Domain Transformation**: Leverage human insight to decompose Complex into Complicated
4. **Irreversibility**: Once framework determined, don't easily return to Complex (unless framework proven inapplicable)

**Comparison with Traditional Research Process**:
- **Traditional**: Manual material collection→manual reading→manual analysis→manual writing (all manual)
- **MAS-Assisted**: AI collection→human insight→AI analysis→human review (human-AI division of labor)
- **Efficiency Improvement**: Humans focus on most valuable insight phase, AI handles information-intensive work

#### Concrete Example

**Case: South Africa Class Analysis**

**Research Question**: How to understand South Africa's class structure and contradictions?

**Complex State Characteristics**:
- Cannot directly apply standard Marxist class analysis (South Africa's racial issues intertwine with class)
- Also cannot only look at race (economic structure is foundation)
- Need an analytical framework integrating race and class, but this framework needs construction

**Stage 1: Preliminary Research (AI Execution)**

AI collects and organizes:
1. **Leftist Organization Analysis**:
   - NUMSA (union) political position documents
   - South African Communist Party's class analysis
   - Papers by radical leftist scholars

2. **Historical Background**:
   - Economic foundation of Apartheid system
   - Economic transformation post-1994
   - Historical evolution of land ownership

3. **Contemporary Economic Structure**:
   - Ownership structure of mining and finance industries
   - Effects of Black Economic Empowerment (BEE) policies
   - Racial and class distribution in labor market

4. **Academic Literature**:
   - Theory on "racial capitalism"
   - Postcolonial analysis
   - Comparative research (postcolonial countries like Brazil, India)

**Output**: Approximately 150 pages of material organization (Markdown format), organized by theme.

**Stage 2: Human Insight Intervention**

Researcher insight after reading materials:
- **Key Finding**: South Africa's class problem cannot be discussed separately from race, but race itself is a manifestation of class relations
- **Theoretical Positioning**: Adopt "neo-colonialism" perspective, viewing South Africa as a postcolonial country in semi-peripheral position in global capitalism system
- **Core Contradiction**: Exploitation relationship between white capital (domestic + transnational) and Black labor, solidified through racialized land ownership and economic structure
- **Analytical Framework**: Three key dimensions
  1. Racialized structure of land ownership
  2. Economic dependency on external forces (mineral exports, financial dependence)
  3. Separation of political and economic power (Blacks hold political power, but economic power remains in white hands)

**Framework Documentation**:
Researcher writes a 10-page theoretical framework document (framework_south_africa.md), clarifying above concepts, variables, and analytical paths.

**Stage 3: Framework-Guided In-Depth Analysis (AI Execution)**

Based on "neo-colonialism" framework, AI conducts targeted analysis:

1. **Land Ownership Analysis**:
   - Collect land reform policies and implementation data
   - Analyze ownership of large farms and mining land
   - Examine relationship between land concentration and race

2. **Economic Dependency Analysis**:
   - Analyze export structure (mineral proportion)
   - Examine degree of foreign capital control
   - Study financial sector's transnational connections

3. **Power Structure Analysis**:
   - Economic background of political elite
   - Beneficiary analysis of BEE policies
   - Relationship network between capital and regime

**Output**: 80-page in-depth analysis report, clearly unfolding along theoretical framework.

**Stage 4: Research Report Writing and Human Review**

AI writes research report based on analysis results, human reviews and refines. Final formation of a South Africa class analysis with theoretical depth.

**Key Value**:
- **Theoretical Innovation**: Constructed class analysis framework applicable to South Africa, not applying generic theory
- **Depth**: Analysis captures South Africa's particularity (race and class intertwining)
- **Efficiency**: Humans focus on most valuable insight phase, AI handles large information work

#### Key Design Principles

1. **Identify Insight Requirement Points**: Clarify where in process human creative insight is needed, don't try to let AI replace it. Theoretical framework construction is typical insight requirement point.

2. **Complete Decoupling, Time Freedom**: Don't let AI "wait" for human input, also don't let humans feel rushed. Key to decoupling is clear interfaces and documented handoffs.

3. **Interface Clarity**: Human output (theoretical framework) must be clearly articulated and documented, becoming reliable input for next stage. Vague "feelings" cannot be transmitted to AI.

4. **Utilize Domain Transformation**: Leverage human insight to decompose Complex problems into Complicated problems. This is key to efficiency improvement: once decomposed, AI can dominate subsequent work.

5. **Decomposition Irreversibility**: Once theoretical framework determined, don't easily return to Complex for re-exploration (unless framework proven fundamentally inapplicable). Trust value of human insight, deepen based on framework rather than repeatedly wavering.

6. **Material Richness**: Stage 1 materials must be sufficiently rich and multi-angled, providing adequate foundation for human insight. Thin materials difficult to stimulate insight.

7. **Framework Iterability**: Although decomposition is irreversible, allow gradual refinement of framework. Preliminary framework→trial analysis→adjust framework→in-depth analysis, this is acceptable.

#### Variants

**Variant 3a-1: Multi-Round Iterative**
- Not one-time framework determination, but preliminary framework→trial analysis→adjust framework→in-depth analysis
- Suitable for highly complex research subjects where theoretical framework needs to be tested and refined in practice

**Variant 3a-2: Comparative Case**
- Simultaneously research multiple subjects (e.g., multiple countries), seeking common theoretical framework
- Need to repeatedly compare between cases, framework emerges from comparison

**Variant 3a-3: Framework Competition**
- Try multiple theoretical frameworks, compare their explanatory power
- Human decides which framework is most applicable

#### Domain Decomposition Relationship

**Entry**:
- From Chaotic entry: If previously conducted fieldwork, created primary data, now need theoretical framework to analyze
- Direct Complex: If already have sufficient materials (e.g., literature), but need framework to understand

**Decomposition: Complex → Complicated**
- **Turning Point**: Human insight determines theoretical framework
- **Mechanism**: Transform "don't know how to view" into "view from this perspective"
- **Effect**: Subsequent analysis path clear, AI can dominate

**Stabilization**:
- Once framework determined, usually doesn't return to Complex
- Unless framework proven fundamentally inapplicable, needs complete overhaul

**Possible Further Decomposition: Complicated → Clear (Rare)**
- If theoretical framework highly mature, analysis process may standardize
- But theoretical research rarely reaches this step, because each case has uniqueness

---

### Exemplar 3b: Editorial Judgment Tasks

#### Context

Researchers or knowledge workers need to select, organize, and curate content from large amounts of information, a process relying on value judgment, aesthetic standards, narrative coherence, or editorial intuition. Selection criteria cannot be fully formalized, requiring identification of implicit connections, balancing multiple dimensions, and forming coherent wholes.

This situation is common in: selecting key literature in literature reviews, content curation for news journals, content design for courses or exhibitions, research case selection, etc.

#### Problem

**Core Challenge**: Judging "what deserves selection" and "how to organize" cannot be fully clarified, involves complex pattern recognition and tacit knowledge.

**Specific Manifestations**:
- Selection criteria are partly explicit, partly tacit (e.g., "interesting," "important," "balanced")
- Requires identifying implicit connections (e.g., multiple news items actually telling same story)
- Requires balancing multiple dimensions (e.g., type balance, positive-negative balance, depth-breadth balance)
- Involves narrative and coherence (e.g., "what story does this journal issue tell")
- AI easily misses context and overall sense

**Why This is a Complex Domain Problem**:
- **Emergent Nature of Pattern Recognition**: What is "same event," what is "related but different" requires holistic understanding
- **Multi-Dimensionality of Judgment**: Simultaneously consider multiple difficult-to-quantify criteria
- **Context Dependence**: Judgment depends on larger context (e.g., overall news environment of the week, reader expectations)
- **Tacit Knowledge**: Editor "feels" this news is important, but may be difficult to explicitly articulate why

**Distinction from Complicated**:
- Complicated: Criteria clear, applying criteria requires analysis
- Complex: Criteria partly tacit, application involves overall sense and pattern recognition

**Key Distinction from Exemplar 3a**:
- 3a's Complex judgment can be **decomposed** into Complicated through human insight (path clear after determining framework)
- 3b's Complex judgment **cannot be decomposed**, each time requires human judgment, won't become automatable Complicated

#### Business Architecture

```
Decoupled Two-Stage Pipeline:

[Stage 1: Candidate Generation] (Optional)
(Complicated-AI)
    ↓
Input: Information sources
    ↓
Process:
  - Collect all candidates (e.g., all news this week)
  - Simple classification and sorting
  - Optional: Provide recommendation list (but don't make final decision)
    ↓
Output: Candidate list
    ↓
    ↓ (Decoupling point)
    ↓
[Human Curation] (Complex-Human)
    ↓
Process:
  - Read candidates (or read directly from sources, not dependent on Stage 1)
  - Identify implicit connections and patterns
  - Balance multiple dimensions
  - Make selection and organization decisions
    ↓
Output: News leads list - Simple title + URL list
    ↓
    ↓ 【Domain Boundary: Complex part doesn't decompose, but decouples】
    ↓
[Stage 2: Deep Production]
(Complicated-AI)
    ↓
Input: Human-determined leads list
    ↓
Process:
  - **Completely independent**, doesn't care how leads were produced
  - Conduct in-depth research on each lead
  - Write high-quality content
    ↓
Output: Final product (e.g., news journal, literature review)
```

**Key Architectural Characteristics**:

1. **Complete Decoupling**: Two stages completely independent, Stage 2 doesn't depend on Stage 1's existence
2. **Interface Minimization**: Human output extremely simple (a list suffices), reduces cognitive burden
3. **Absolute Human Decision Authority**: Selection and organization entirely completed by humans, AI doesn't participate
4. **Each Does Their Part**: AI does information processing (Complicated), humans do curation (Complex)
5. **Don't Pursue Decomposition**: Acknowledge certain Complex judgments cannot be automated, don't force it

#### MAS Design

##### Stage 1: Candidate Generation (Complicated-AI, Optional)

**Objective**: Reduce human information overload, provide preliminarily organized candidate list.

**Agent Type**: Candidate Generation Agent

**Note**: **This stage is optional, non-core**. Humans can choose to:
- Use AI-generated candidate list
- Skip entirely, read directly from sources
- Use simple RSS subscription tools

**If Using AI Assistance, What to Do**:
1. Collect all news from news sources this week (e.g., 100-200 items)
2. Simple classification (politics, economy, society, technology, etc.)
3. Sort by objective criteria (e.g., media coverage, event importance)
4. Provide recommendation list (e.g., "these 30 may be worth attention")

**AI Should Not Do**:
- Don't try to make final selection (select 10-12 items)
- Don't try to identify "same event" (AI very difficult to accurately judge)
- Don't try to balance types and positive-negative (this is editorial judgment)

**Output**: Candidate list (Markdown or JSON) with simple metadata.

##### Human Curation (Complex-Human) - Non-Decomposable Core

This is the **core value point** of the entire process, also **irreplaceable human judgment**.

**Human Work**:
1. **Reading & Browsing**: Read candidate news (or read directly from sources), form overall impression
2. **Identify Connections**: See which news items are actually different angles of same event
3. **Judge Importance**: Based on domain understanding, judge which news is truly important
4. **Balance**: Ensure type balance (not all politics), positive-negative balance (not all bad news), depth-breadth balance
5. **Narrative**: Imagine "what story does this journal issue tell"

**Output**: **News Leads List**

This is an extremely simple output, for example:
```markdown
# This Week's News Leads (2024-11-06)

1. Fourth Plenum Resolution Released: Economic Reform and Tech Autonomy
   - URL: https://...

2. Local Debt Restructuring Plan Announced
   - URL: https://...

3. China-US Tech Dialogue Resumes
   - URL: https://...

...

10. Rongjiang Village Super Selected as UN Case
    - URL: https://...
```

**Why This Cannot Be Automated**:

**Example: Difficulty of Identifying "Same Event"**
- Fourth Plenum has multiple angle reports:
  - Personnel adjustments
  - Economic reform policies
  - Technology strategy
  - Foreign relations impacts
- AI might treat these as 4 independent news items
- Human editor sees: these are different facets of same theme, should merge into one, telling "panorama of Fourth Plenum"

**Example: Narrative Coherence**
- Want to merge "local debt" and "real estate market" two news items
- They're not same event, but have intrinsic connection
- After merging can tell story of "China's economic structural adjustment"
- This kind of connection identification requires editorial insight, AI difficult to accurately judge

**Example: Value Judgment of Importance**
- Some news has high coverage but may not be important (e.g., entertainment news)
- Some news has low coverage but very important for understanding China (e.g., grassroots governance innovation)
- Judging "why important" requires values and domain understanding

**Example: Aesthetics of Balance**
- This journal issue shouldn't be all political news, need social and cultural
- Shouldn't be all bad news, need positive developments
- This sense of balance is editorial aesthetics, difficult to formalize

##### Stage 2: Deep Production (Complicated-AI)

**Objective**: Based on human-determined leads, conduct in-depth research and content production.

**Agent Type**: Deep Research & Writing Agent

**Key Characteristic**: **Completely independent, doesn't care how leads were produced**

This stage doesn't need to know:
- Whether leads were manually selected by humans or AI-assisted
- Why these leads were chosen
- What other candidates were excluded

It only needs to know: humans want me to conduct in-depth research on these 10 leads.

**Processing for Each Lead**:

**7-Angle Comprehensive Research**:
1. **Event Full Picture**: What happened, timeline, key participants
2. **Media Coverage**: How mainstream and international media report
3. **Expert Commentary**: Views of scholars and analysts
4. **Historical Background**: Event's causes and historical context
5. **Professional Knowledge**: Knowledge from relevant fields (e.g., law, economics, technology)
6. **Geopolitics**: International relations and geopolitical impacts
7. **Impact Analysis**: Short-term and long-term impacts

**Output**:
- Each news item: 80-character concise summary + detailed background materials
- Integrate into email journal format

**Why This is Complicated**:
- Research path clear (7 angles)
- Requires synthesizing information and judgment, but framework explicit
- AI can play "in-depth research expert" role

#### Human-AI Collaboration Points/Patterns

**Collaboration Mode: Core Decoupling**

```
AI (Candidate Organization, Optional) → Human (Curation Judgment) → AI (Deep Production)
     ↓                                    ↓                             ↓
  Auxiliary Task                     Core Value Point            Information-Intensive Work
  (Can have or not)                (Human Absolute Dominance)          (AI Excels)
```

**Comparison with Exemplar 3a**:

| Dimension | 3a (Theoretical Framework Discovery) | 3b (Editorial Judgment) |
|-----------|-------------------------------------|-------------------------|
| **Human Judgment Nature** | Determine theoretical framework | Select and organize content |
| **Judgment Persistence** | Once determined, reusable | Each time requires re-judgment |
| **Domain Decomposition** | Complex→Complicated | Doesn't decompose, remains Complex |
| **AI Subsequent Role** | Dominates analysis based on framework | Only does production, doesn't participate in judgment |
| **Automation Prospect** | Can automate after framework determined | Curation always requires humans |

**Key Insight**:
- **3a is "One Insight, Multiple Applications"**: Once theoretical framework determined, can guide large amounts of subsequent work
- **3b is "Each Time Requires Judgment"**: Selecting news each week requires re-judgment, cannot solidify into rules

#### Concrete Example

**Case: News on China Weekly Production**

**Background**: News on China is a weekly focusing on China current affairs, selecting 10-12 items from large amounts of news each week for in-depth research and refined presentation.

**Challenge**:
- 100-200 related news items each week
- Need to select most noteworthy 10-12 items
- These news items should:
  - Cover different types (politics, economy, society, technology, culture)
  - Balance positive-negative
  - Tell coherent "this week in China" story

**Stage 1: Candidate Generation (AI-Assisted, Optional)**

AI collects all related news this week:
- China mainstream media news
- International media reports about China
- Analysis from think tanks and academic institutions
- Approximately 150 news items total

AI simply classifies and sorts, provides candidate list.

**Stage 2: Human Curation (Core)**

Editor reads candidate list (or browses news sources directly), makes judgments:

**Example 1: Identifying "Same Event"**
- Candidate list contains:
  - "Central Economic Work Conference Convenes"
  - "Real Estate Policy Adjustment"
  - "Local Debt Resolution Plan"
  - "Consumer Stimulus Policy"
- Editor judges: these are all same theme—economic policy adjustment, should merge into one news lead: "New Developments in China Economic Policy"

**Example 2: Related but Different News**
- "Chip Manufacturing Breakthrough" and "Semiconductor Export Control Escalation"
- Not same event, but have intrinsic connection
- Editor decides: place in adjacent positions, tell story of "tech autonomy and geopolitical competition"

**Example 3: Importance Judgment**
- "Celebrity Marriage" has very high coverage
- "Grassroots Democracy Election Pilot" has low coverage
- Editor judges: latter more important for understanding China, select latter

**Example 4: Balance Consideration**
- Already selected 3 political news items
- Although still have important political news, need balance
- Select one cultural news item: "Forbidden City Digitalization Project"

**Output**: 10 news leads list (simple title + URL)

**Stage 3: Deep Production (AI Execution)**

AI receives 10 leads, conducts in-depth research on each:

**Example: For "New Developments in China Economic Policy"**
- Research 7 angles:
  1. Event full picture: integrate economic work conference, real estate, local debt, consumer policies
  2. Media coverage: mainstream and international media interpretations
  3. Expert commentary: economists' views
  4. Historical background: economic policy context over past few years
  5. Professional knowledge: relevant theories in macroeconomics
  6. Geopolitics: impacts of global economic environment
  7. Impact analysis: impacts on enterprises and citizens

- Write 80-character summary:
  > "Central Economic Work Conference released multiple signals, from real estate policy adjustment to local debt resolution to consumer stimulus, showing policy shift from risk prevention to stable growth. Experts believe this is comprehensive measure responding to external pressure and insufficient internal demand, but whether it can effectively boost economy remains to be observed in execution strength and market confidence."

- Attach detailed background materials (3-5 paragraphs)

**Integration**: Integrate 10 news items into one complete email journal issue, send to subscribers.

**Key Value**:
- **Editorial Quality**: Human curation ensures selections are insightful and coherent
- **Depth**: AI in-depth research ensures each news item has sufficient background
- **Efficiency**: Humans focus on curation of 10 items (approximately 2 hours), AI handles in-depth research on 10 items (if manual would need approximately 20 hours)

#### Key Design Principles

1. **Acknowledge AI Limitations**: Some judgments AI just doesn't do well (e.g., identifying "same event," narrative coherence), don't force it. Acknowledging limitations more important than creating illusions.

2. **Decouple Rather Than Semi-Automate**: Don't try to let AI "assist" human judgment (e.g., AI recommends, human fine-tunes). This creates cognitive burden. Should completely separate: AI handles pre- and post- Complicated parts, humans independently complete middle Complex judgment.

3. **Interface Minimization**: Human output should be as simple as possible. A list (title + URL) is enough, don't require humans to write complex specification documents.

4. **Leverage Respective Strengths**:
   - AI strengths: information processing capability, in-depth research, structured expression
   - Human strengths: pattern recognition, value judgment, narrative sense, overall grasp

5. **Don't Pursue Decomposition**: Accept that certain Complex judgments cannot be automated, won't decompose to Complicated. This differs from Exemplar 3a; 3a's insight can solidify into framework, 3b's judgment is new each time.

6. **Maintain Judgment Independence**: Stage 2 should not be influenced by "what AI recommended." If Stage 1 AI recommendations influence human judgment, better to skip Stage 1.

7. **Quality from Human Curation**: Final product quality critically depends on quality of human curation. AI's in-depth research is amplifier but cannot compensate for inadequate curation.

#### Variants

**Variant 3b-1: Literature Review Curation**
- From hundreds of related literature pieces, select 20-30 key literature items
- Need to identify: which are foundational, which represent different schools, which are latest advances
- Human curation: select literature list
- AI execution: in-depth reading and summarization of each literature item

**Variant 3b-2: Case Study Selection**
- Determine case selection criteria for research
- Need to balance: typicality, diversity, feasibility
- Human curation: determine case list
- AI execution: background research on each case

**Variant 3b-3: Course or Exhibition Content Design**
- Select and organize content from large amounts of materials
- Need to consider: narrative logic, difficulty progression, time allocation
- Human curation: determine content structure
- AI execution: prepare detailed materials for each part

**Variant 3b-4: Research Agenda Setting**
- From numerous possible research questions, select most worthy of investigation
- Need to judge: importance, feasibility, originality
- Human curation: determine research question list
- AI execution: literature review and feasibility analysis for each question

#### Domain Decomposition Relationship

**Doesn't Decompose**: This type of Complex judgment remains long-term in Complex domain.

**Why Cannot Decompose**:
- Judgment criteria partly tacit, cannot be fully formalized
- Each judgment depends on new context
- No "once and for all" rules or frameworks exist

**Isolation Strategy**: Through decoupling, let AI handle surrounding Complicated tasks.

**Form Stable Human-AI Symbiosis**:
```
Complicated (AI) → Complex (Human) → Complicated (AI)
   ↓                  ↓                   ↓
 Information         Curation            Deep
 Organization        Judgment         Production
 (Automatable)    (Not Automatable)  (Automatable)
```

**Comparison with 3a**:
- **3a**: Complex → (Human Insight) → Complicated (Decomposition successful, AI dominates subsequent)
- **3b**: Complicated → (Human Judgment) → Complicated (Doesn't decompose, human continues participating)

**Accept Reality**: Not all Complex problems can decompose. Accepting this and designing appropriate decoupling patterns is wiser than forcing automation.

**Long-Term Outlook**: Even if AI capabilities improve, this type of curation judgment may still require humans. Because it involves not "calculating more accurately" but "what deserves attention"—this is value judgment, not computation problem.

---

## 3.4 Chaotic Domain Exemplar: Creative Fieldwork Research

### Context

Researchers face a research subject or phenomenon lacking existing literature and data. Existing secondary materials are severely insufficient or low quality, unable to support in-depth research. The research question itself may not be sufficiently clear, causal relationships unclear. Researchers must create previously non-existent data through field intervention—going deep into the scene, communicating with people, observing practices, collecting primary materials.

This is research's "chaotic" state: no ready-made information to rely on, must establish order through action. Theoretical questions gradually clarify during research process, research direction adjusts based on field discoveries.

Typical scenarios include: emerging social phenomenon research (e.g., "Village Super" phenomenon), unexplored historical archive excavation, oral history of marginalized groups, field evaluation of experimental policies, etc.

### Problem

**Core Challenge**: In situations where information basically doesn't exist and causal relationships are unclear, how to establish knowledge foundation through creative action.

**Specific Manifestations**:
- **Information Doesn't Exist**: Key information not recorded in literature, internet, or archives, only exists in field participants' minds or in ongoing practices
- **Causal Mechanisms Unclear**: Don't know "why it's like this," not even sure "what happened"
- **Question Itself Vague**: Research question gradually clarifies during research process, not preset
- **Highly Context-Dependent**: Each field site is unique, cannot apply standard methods
- **Emergent**: Key discoveries often unexpected, from chance conversations or observations in field

**Why This is a Chaotic Domain Problem**:
- **Information Doesn't Exist**: This is signature characteristic of Chaotic domain, fundamental distinction from other three domains (information exists)
- **Causal Relationships Indiscernible**: At start of fieldwork, don't know which factors important, which relationships exist
- **Must Act**: Cannot obtain information through analysis (Complicated) or exploring existing materials (Complex), must create data through action
- **Decision Mode: Act-Sense-Respond**: Act→sense in action→adjust action based on sensing

**Meaning of "Creating Data" in Research Context**:
- **Act Not Intervening in Research Subject**: Not changing research subject itself (though fieldwork has some influence)
- **Act is Creative Information Collection**: Through interviews, observation, participation, making tacit knowledge explicit, transforming unrecorded experience into analyzable data
- **Data from Nothing to Something**: Previously no analyzable materials existed, created through fieldwork

### Business Architecture

```
Human-Led Chaotic Process - Domain Decomposition Sequence:

[Fieldwork] (Chaotic-Human)
    ↓
Input: Preliminary research question + Opportunity to enter field
    ↓
Process:
  - Field interviews (in-depth interviews, informal conversations)
  - Participant observation (participate in activities, observe practices)
  - Document collection (field documents, photos, recordings)
  - Relationship building (gain trust, establish networks)
  - **Create previously non-existent data**
  - Act-Sense-Respond: adjust direction in action
    ↓
Output: Primary data (interview recordings, field notes, photos, collected documents)
    ↓
    ↓
[Data Organization] (Clear-AI, Auxiliary)
    ↓
Process:
  - Transcribe interview recordings → text (Clear task)
  - Organize field notes → structured documents (Clear/Complicated)
  - Photo and document classification → archives (Clear)
    ↓
Output: Organized dataset
    ↓
    ↓
[Iterative Meaning-Making] (Complex-Human)
    ↓
Process:
  - Repeatedly read field materials
  - Identify emergent patterns and themes
  - Distill preliminary theoretical framework
  - Decide whether to supplement fieldwork
    ↓
Output: Theoretical framework / Research findings
    ↓
    ↓
【Domain Decomposition: Chaotic → Complex → (Possibly) Complicated】
    ↓
[Subsequent Analysis] (Complicated-AI, Possible)
    ↓
Process:
  - Based on established theoretical framework, conduct structured analysis
  - May supplement secondary materials (literature, statistical data)
  - Write research report
    ↓
Output: Research results (papers, reports, policy recommendations)
```

**Architectural Characteristics**:

1. **Absolute Human Dominance**: Core fieldwork and meaning-making completed by humans, AI only participates in auxiliary phases
2. **Iteration & Emergence**: Not linear process, but multiple rounds of iteration, direction adjusts during process
3. **Domain Decomposition Path**: Chaotic (fieldwork)→Complex (meaning-making)→Complicated (structured analysis)
4. **Centrality of Data Creation**: Value of entire process lies in creating previously non-existent knowledge foundation

### MAS Design

**Overall Principle**: **AI Minimal Assistance, Human Absolute Dominance**

In Chaotic domain, AI's role is extremely limited. Not designing complex MAS, but identifying which mechanical subtasks can be automated, thereby freeing human time to focus on fieldwork.

#### Dominant: Human Fieldwork (Chaotic-Human)

**Core Activities**:

1. **In-Depth Interviews**:
   - Conduct semi-structured or unstructured interviews with key informants
   - Adjust questions based on field responses
   - Build trust, obtain deep information

2. **Participant Observation**:
   - Participate in field activities, observe practices
   - Record details and contexts
   - Understand explicit rules and implicit norms

3. **Document Collection**:
   - Collect field documents (e.g., meeting minutes, promotional materials, internal documents)
   - Photograph records (places, activities, objects)
   - Audio recordings (interviews, meetings, activities)

4. **Relationship Building**:
   - Build relationships with gatekeepers
   - Expand information networks
   - Obtain permission for deep access

5. **Field Judgment & Adjustment**:
   - Based on field discoveries, adjust research focus
   - Identify unexpected important clues
   - Decide which directions to deepen, which to abandon

**Why This Cannot Be Delegated to AI**:
- **Information Not on Internet**: AI cannot access field
- **Requires Interpersonal Interaction**: Building trust, interpreting non-verbal information, flexible follow-up questions
- **Emergence**: Key discoveries come from field accidents, AI cannot "learn in accidents"
- **Ethical Responsibility**: Fieldwork involves relationships with people, researchers need to bear ethical responsibility

#### Auxiliary: AI Handles Clear/Complicated Subtasks

Although AI cannot dominate Chaotic domain work, can handle surrounding mechanical tasks.

**Task 1: Transcribe Interview Recordings (Clear)**
- **Input**: Interview recording files (audio)
- **Processing**: Use speech-to-text tools (e.g., Whisper)
- **Output**: Text transcripts
- **Human Role**: Review and correct transcription errors, especially technical terms and local accents

**Task 2: Organize Field Notes (Clear/Complicated)**
- **Input**: Researcher's scattered notes (may be handwritten, fragmented)
- **Processing**: AI helps organize into structured documents
  - Classify by date, theme, informant
  - Extract keywords and theme tags
  - Generate table of contents and index
- **Output**: Organized field notes database

**Task 3: Preliminary Theme Coding (Complicated)**
- **Input**: Transcripts and field notes
- **Processing**: AI conducts preliminary theme coding
  - Identify recurring themes
  - Count keyword frequencies
  - Mark relevant passages
- **Note**: This is only auxiliary; real coding and theory construction require humans
- **Output**: Data with preliminary coding

**Task 4: Supplementary Literature Review (Complicated)**
- **Input**: Key concepts identified in fieldwork
- **Processing**: AI searches relevant academic literature
- **Output**: Literature review, helping researchers understand position of field discoveries in academic dialogue

**Task 5: Timeline and Event Organization (Complicated)**
- **Input**: Events and times mentioned in interviews
- **Processing**: AI organizes into timeline
- **Output**: Visualized event timeline, helping researchers understand historical context

**AI Should Not Do**:
- **Cannot Replace Data Collection**: Core information doesn't exist on internet
- **Cannot Replace Theory Construction**: Patterns not yet emerged, AI cannot see connections researchers see
- **Cannot Identify Causal Relationships**: Because causal relationships gradually clarify during fieldwork
- **Cannot Decide Research Direction**: Requires field judgment and flexible adjustment

### Human-AI Collaboration Points/Patterns

**Collaboration Mode: Human-Led + Mechanical Task Outsourcing**

```
Human (Fieldwork) → AI (Transcription/Organization) → Human (Meaning-Making) → AI (Structured Analysis, Possible) → Human (Writing)
    ↓                   ↓                               ↓                           ↓                              ↓
  Create Data      Auxiliary Task                  Identify Patterns          Apply Framework              Final Presentation
  (95% Human)      (Automatable)                   (Human)                    (Partially Automatable)      (Human-Led)
```

**Human Time Allocation** (Approximate):
- Fieldwork: 70%
- Meaning-making: 20%
- Writing: 10%

**Time AI Saves**:
- Transcription (if manual needs 10 hours → AI: 1 hour)
- Organize notes (if manual needs 5 hours → AI: 30 minutes)
- Preliminary coding (if manual needs 8 hours → AI: 1 hour)

**Key Insight**: AI's value in Chaotic domain **is not dominating work but saving time on mechanical tasks, letting researchers have more time to focus on field and thinking**.

### Concrete Example

**Case: Rongjiang Village Super Research**

**Research Question**: How do digital technologies assist rural revitalization? Guizhou Rongjiang County's "Village Super" phenomenon is a compelling case.

#### Chaotic State Characteristics

**Why This is Chaotic**:

1. **Information Basically Doesn't Exist**:
   - Village Super is emerging phenomenon from 2023-2024, almost no academic research
   - News reports only have surface descriptions ("Village Super became popular," "driving tourism")
   - Key information (e.g., how traffic converts, how county operates, how villages participate) not in public materials

2. **Causal Mechanisms Unclear**:
   - **Surface Phenomenon**: GDP shows no significant change, tourism revenue increased
   - **Questions**:
     - How much traffic actually? From where?
     - How does traffic convert to economic income?
     - How is income distributed? (County, village, individual)
     - How do villages participate in creating and converting traffic?
     - How sustainable?

3. **Existing Materials Too Superficial**:
   - Secondary materials can only provide surface information
   - Deep understanding requires going to field

4. **Must Act**: Field research is only way to obtain key information

#### Fieldwork (Chaotic-Human)

**Enter Field**:
Researcher goes to Rongjiang County for field research, duration 2 weeks.

**Interview Subjects**:
1. **County Government Officials**:
   - Propaganda Department: how does self-media matrix operate?
   - Cultural Tourism Bureau: tourism revenue data and distribution mechanism?
   - Rural Revitalization Office: Village Super's positioning in rural revitalization strategy?

2. **Grassroots Cadres**:
   - Township Party Secretary: how is Village Super organized? How do villagers participate?
   - Village Party Secretary: village's income and distribution?

3. **Villagers**:
   - Player participants: what's the motivation? Any income?
   - Small vendors: how's business? How much income increased?
   - Guesthouse operators: customer flow changes?

4. **Self-Media People**:
   - County-supported self-media: how to create content? Revenue sources?
   - Independent self-media: how to discover and report Village Super?

5. **Tourists**:
   - Why come? What did they see? What did they consume?

**Participant Observation**:
- Watch Village Super matches, observe field atmosphere
- Visit villages, observe tourism facilities
- Follow self-media filming, observe content creation process

**Key Discoveries** (Emerged in field):

**Discovery 1: Multi-Layered Structure of Traffic Sources**
- Not single source, but:
  - County-level self-media matrix (official support)
  - Mainstream media coverage (CCTV, etc.)
  - Independent self-media discovery (Douyin, Kuaishou)
  - Tourist spontaneous spread
- **Unexpected**: County has specialized team operating self-media matrix, not reported in news

**Discovery 2: Multiple Paths of Traffic Conversion**
- Not just tourism, but also:
  - Agricultural product e-commerce (brand effect from Village Super)
  - Cultural products (Village Super merchandise)
  - Event sponsorship (corporate naming)
- **Unexpected**: Largest revenue not on-site tourism but online agricultural product sales

**Discovery 3: Differentiated Participation of Villages**
- Not homogeneous, but:
  - Some villages focus on event organization (participation)
  - Some villages focus on tourism reception (guesthouses, restaurants)
  - Some villages focus on product sales (agricultural products, cultural products)
- **Unexpected**: Division of labor and competition between villages forms an ecosystem

**Discovery 4: Sustainability Challenges**
- Traffic has cyclicality (large difference between in-season and off-season)
- Income distribution unequal (some villagers benefit, some marginalized)
- Relies on external attention (what if heat fades?)

**Adjust Research Focus**:
- **Initial Question**: How do digital technologies assist rural revitalization? (Too broad)
- **Adjusted Question**: Operating mechanism and sustainability of traffic economy in rural areas? (More specific)

#### AI Auxiliary Tasks (Clear/Complicated)

**Interview Transcription**:
- Researcher conducted 20+ interviews, approximately 30 hours of recordings
- AI transcription (using Whisper): approximately 2 hours
- Human review and correction (especially local accents and technical terms): approximately 5 hours
- **Time Saved**: If manual transcription would need approximately 100 hours

**Field Notes Organization**:
- Researcher's field notes scattered (handwritten + electronic)
- AI organizes into structured documents:
  - Classify by interview subject
  - Theme tags (traffic sources, income distribution, villager participation, etc.)
  - Generate index
- **Time Saved**: approximately 3 hours

**Preliminary Theme Coding**:
- AI analyzes transcripts, identifies recurring themes:
  - "Self-media" (high frequency)
  - "Income distribution" (key contradiction)
  - "Sustainability" (widespread concern)
- This helps researcher quickly locate key passages

**Supplementary Literature Review**:
- AI searches academic literature on keywords like "traffic economy," "rural revitalization," "short videos and rural areas"
- Helps researcher position field discoveries in academic dialogue

#### Meaning-Making (Complex-Human)

Researcher repeatedly reads field materials, gradually forms theoretical framework:

**Theoretical Framework: Rural Adaptation Model of Traffic Economy**

Core Concepts:
1. **Traffic Production**: Content creation (official + grassroots)
2. **Traffic Conversion**: Multiple paths (tourism + e-commerce + sponsorship)
3. **Ecosystem**: Multi-level participation of county-township-village-individual
4. **Sustainability**: From relying on heat to building brand

Key Variables:
- Traffic source diversity
- Conversion path richness
- Income distribution fairness
- Villager participation degree

**Domain Decomposition: Chaotic → Complex**

Markers:
- ✓ Accumulated sufficient primary data (20+ interviews, 2 weeks observation)
- ✓ Beginning to see patterns (traffic's multi-layered structure, conversion's multiplicity)
- ✓ Can pose theoretical questions (operating mechanism of traffic economy)
- ✓ Enter Probe-Sense-Respond mode (can "probe" based on framework rather than just "act")

#### Subsequent Analysis (Complicated-AI, Possible)

Based on established theoretical framework, can conduct structured analysis:

**Possible Analysis Tasks** (partially automatable):
1. **Quantitative Analysis**:
   - Collect traffic data (self-media views, tourist numbers)
   - Analyze revenue data (e-commerce sales, tourism revenue)
   - Evaluate participation degree of each village

2. **Comparative Research**:
   - Search similar cases (traffic economy practices in other places)
   - Compare similarities and differences, distill patterns

3. **Policy Recommendations**:
   - Based on discoveries, propose policy recommendations for sustainable development

**Why These Can Be Partially Automated**:
- Analysis framework already clear (traffic production-conversion-sustainability)
- Data collection path explicit (though needs return to field or supplement secondary data)
- AI can conduct structured analysis based on framework

#### Research Results

**Paper**: "Rural Adaptation of Traffic Economy: Fieldwork-Based Research on Rongjiang Village Super"
- Theoretical Contribution: Propose "Multiple Conversion Model of Traffic Economy"
- Empirical Contribution: Reveal operating mechanism of Rongjiang Village Super
- Policy Significance: Provide referenceable experience for other regions

**Key Value**:
- **Establishing Knowledge Foundation**: Previously no in-depth knowledge about Village Super existed, now exists
- **Theoretical Innovation**: Not applying existing theory but distilling new theory from field
- **Practical Significance**: Helps understand new paths for rural revitalization

### Key Design Principles

1. **Accept Human-Centrality**: In Chaotic domain, don't try to let AI dominate. Humans are absolute protagonists, AI is supporting role.

2. **Identify Auxiliary Tasks**: Although AI cannot dominate, can handle mechanical tasks (transcription, organization, preliminary coding). Identify these tasks, free human time.

3. **Maintain Flexibility**: Don't preset fixed processes. Fieldwork is emergent, plans need to adjust based on field discoveries. MAS design should support flexibility, not impose processes.

4. **Record Emergent Process**: Data creation process itself is part of research results. Record "why adjusted this way," "what was discovered unexpectedly."

5. **Plan Domain Decomposition**: Think about how to gradually decompose from Chaotic to Complex and Complicated. One goal of fieldwork is establishing sufficient order to make subsequent analysis possible.

6. **Ethics First**: Fieldwork involves relationships with people, must respect informants' rights and privacy. AI can assist, but ethical responsibility cannot be delegated.

7. **Quality Over Efficiency**: In Chaotic domain, don't overly pursue efficiency. Deep fieldwork requires time; rushing leads to low information quality.

### Variants

**Variant 4a: Archive Excavation Research**
- **Context**: Excavate unexplored historical archives
- **Chaotic Characteristic**: Archive content unorganized, don't know what exists
- **Act**: Go to archive, read volume by volume, identify valuable materials
- **AI Assistance**: OCR recognition, text organization, preliminary classification
- **Domain Decomposition**: After archive organization, can conduct historical analysis (Complex/Complicated)

**Variant 4b: Oral History Research**
- **Context**: Record personal experiences about to disappear (e.g., veteran memories)
- **Chaotic Characteristic**: Knowledge in elders' minds, disappears forever if not interviewed
- **Act**: In-depth interviews, build trust, stimulate memories
- **AI Assistance**: Transcription, timeline organization, connection with historical events
- **Domain Decomposition**: After oral history accumulation, can reconstruct historical narrative (Complex)

**Variant 4c: Action Research**
- **Context**: Researcher participates in practice and observes (e.g., education reform pilot)
- **Chaotic Characteristic**: Practice is new, results unpredictable
- **Act**: Researcher as participant, acts while observing
- **AI Assistance**: Record analysis (e.g., student performance changes, teacher feedback)
- **Domain Decomposition**: After practice patterns gradually clear, can summarize experience (Complicated)

**Variant 4d: Emergency Event Research**
- **Context**: Rapid research on sudden events (e.g., natural disaster response)
- **Chaotic Characteristic**: Situation chaotic, information missing, need rapid action
- **Act**: Go to scene, interview, observe response process
- **AI Assistance**: Quickly organize information, generate timeline, support decision-making
- **Domain Decomposition**: After stabilization, can conduct systematic evaluation (Complicated)

### Domain Decomposition Relationship

#### Chaotic is Starting Point of Domain Decomposition

When research field lacks existing knowledge foundation, Chaotic is starting point:
```
Chaotic (Fieldwork, Create Data)
  ↓
  Through data accumulation, establish preliminary order
  ↓
Complex (Identify Patterns, Construct Theoretical Framework)
  ↓
  Through theoretical framework establishment, analysis path clear
  ↓
Complicated (Framework-Based Structured Analysis)
  ↓
  (Possibly) Through standardization, solidify best practices
  ↓
Clear (Standard Process, Rare)
```

#### Chaotic → Complex Transformation Markers

**Transformation Occurs When**:
- ✓ Accumulated sufficient primary data
- ✓ Beginning to see recurring patterns and connections
- ✓ Can pose theoretical questions (not "what happened" but "why like this")
- ✓ Enter Probe-Sense-Respond mode (can "probe" rather than just "act")

**Markers in Rongjiang Case**:
- 20+ interviews completed, field notes rich
- Identified patterns like "traffic's multi-layered sources," "conversion's multiple paths"
- Can ask: "How does traffic economy adapt to rural areas?"
- Can decide which interviews to supplement based on preliminary framework (Probe)

#### Value of Decomposition

**Why Decomposition Important**:
1. **Efficiency Improvement**: Once enter Complex/Complicated, AI can participate more
2. **Knowledge Accumulation**: From disorder to order, knowledge can be recorded and disseminated
3. **Theoretical Contribution**: Decomposition process itself produces theory (e.g., "traffic economy model")
4. **Subsequent Research**: Provide foundation for other researchers, they can start from Complicated, don't need to repeat fieldwork

**Multiplicity of Results**:
- **Data Itself**: Previously non-existent primary materials (interviews, notes, photos)
- **Theoretical Framework**: Analytical perspective distilled from materials
- **Research Conclusions**: Discoveries and insights based on analysis
- **Methodological Contribution**: Experience on how to research this type of phenomenon

#### Cost of Not Decomposing

**If Remain in Chaotic**:
- Researchers have rich field experience but difficult to systematically articulate
- Knowledge cannot be effectively disseminated (only "you must go to field to understand")
- Cannot guide subsequent research or policy

**Risk of Premature Decomposition**:
- Don't have sufficient field data yet, try to construct theory (Complex)
- Leads to shallow theory, cannot grasp phenomenon's complexity

**Correct Rhythm**:
- Fully immerse in Chaotic until patterns naturally emerge
- Don't rush to "draw conclusions," let data speak
- Once patterns stabilize, timely transition to Complex for theory construction

---

## Conclusion: Integrated Understanding of Four-Domain Exemplars

We have presented four exemplars, each corresponding to a domain in the Cynefin framework. These exemplars are not isolated but interconnected:

### Continuity of Domain Decomposition

Research processes often experience decomposition from high to low uncertainty:

```
Chaotic (Rongjiang Fieldwork)
  → Create primary data, establish preliminary order
  ↓
Complex (Identify Traffic Economy Patterns)
  → Construct theoretical framework, analysis path clear
  ↓
Complicated (Framework-Based Structured Analysis)
  → Standardized analysis (e.g., evaluate traffic economy in other regions)
  ↓
Clear (Data Collection and Organization)
  → Automate auxiliary tasks
```

### Gradient of Human-AI Collaboration

From Chaotic to Clear, AI's role ranges from minimal assistance to being able to dominate:

| Domain | AI Role | Human Role | Collaboration Mode |
|--------|---------|------------|-------------------|
| **Chaotic** | Minimal assistance (transcription, organization) | Absolute dominance (fieldwork) | Human-led + mechanical task outsourcing |
| **Complex** | Material preparation (3a) or production assistance (3b) | Insight & judgment | Complete decoupling + domain transformation |
| **Complicated** | Expert system (framework-based analysis) | Define framework, review quality | Serial division of labor |
| **Clear** | Fully automated execution | Define task, verify results | Define-execute-verify |

### Evolution of Business Architecture

As research deepens, business architecture evolves from extremely flexible to highly structured:

- **Chaotic**: Almost no fixed architecture, completely emergent
- **Complex**: Mixed human-AI pipeline, has decoupling points but maintains flexibility
- **Complicated**: Multi-stage pipeline, structured but supports parallelism
- **Clear**: Single-stage or simple pipeline, highly automated

### Core Design Wisdom

Through four exemplars, we distill core wisdom for research-oriented MAS design:

1. **Identify Domain Location**: Don't use wrong methods (e.g., forcing Complicated methods in Complex domain)
2. **Plan Decomposition Path**: Think about how to gradually decompose from high to low uncertainty
3. **Design Decoupling Points**: Where human insight is needed, completely decouple, don't semi-automate
4. **Knowledge Externalization**: Separate "what to know" from "how to do," facilitate iteration and reuse
5. **Respect Non-Decomposability**: Acknowledge certain Complex judgments (like editorial curation) cannot be automated, design symbiotic modes
6. **Leverage Respective Strengths**: AI does information processing, humans do insight and judgment

### From Exemplars to Practice

These four exemplars are **starting points, not endpoints**. Each researcher's problems are unique, need adjustment based on specific contexts:

- **Identify which domain your problem belongs to** (or spans multiple domains)
- **Find closest exemplar** as reference
- **Adjust business architecture based on specific context**
- **Practice, reflect, iterate**

Research-oriented MAS design is both an art and a science. These exemplars provide systematic guidance, but ultimate creation comes from your deep understanding of research questions and acute grasp of human-AI collaboration boundaries.

---

*The four exemplars presented in this section come from AgentForge project practices in digital sovereignty research, area studies, fieldwork research, and other fields. They are real, tested patterns and open, evolvable frameworks.*

*We look forward to more researchers contributing their practices as new exemplars, collectively enriching the pattern language of research-oriented multi-agent systems.*

---

---

# Appendices

## Appendix A: Four-Domain Quick Reference Table

| Domain | Information State | Causal Relationships | AI Role | Human Role | Decision Pattern | Typical Tasks | Exemplar |
|--------|------------------|---------------------|---------|------------|-----------------|--------------|----------|
| **Clear** | Structurally exists | Clear | Fully automated | Define tasks | Sense-Categorize-Respond | Downloads, transcription | Ex.1 |
| **Complicated** | Exists, needs interpretation | Clear but requires analysis | Expert system | Define framework | Sense-Analyze-Respond | Indicator assessment | Ex.2 |
| **Complex** | Exists, needs integration | Retrospectively identifiable | Assist material prep | Identify patterns | Probe-Sense-Respond | Theory construction, editorial judgment | Ex.3a/3b |
| **Chaotic** | Basically non-existent | Unidentifiable | Minimal assistance | Create data | Act-Sense-Respond | Fieldwork | Ex.4 |

### Typical Paths of Domain Decomposition

- **Chaotic → Complex**: Establish preliminary order through data creation
- **Complex → Complicated**: Establish theoretical framework through human insight
- **Complicated → Clear**: Solidify best practices through standardization (less common)

### Key Design Principles

1. **Identify the domain** where the task resides
2. **Plan decomposition paths** to progressively reduce uncertainty
3. **Design human intervention points** - timing and methods of human-AI collaboration
4. **Apply appropriate methods** in each domain - don't use Clear domain methods for Complex domain problems
5. **Leverage AI's strengths, respect human irreplaceability** - in Complex domain, human insight is indispensable

---

## Appendix B: References

### Cynefin Framework Literature

- Snowden, D. J., & Boone, M. E. (2007). "A Leader's Framework for Decision Making." *Harvard Business Review*, 85(11), 68-76.
- Snowden, D. J. (2002). "Complex Acts of Knowing: Paradox and Descriptive Self-Awareness." *Journal of Knowledge Management*, 6(2), 100-111.
- Kurtz, C. F., & Snowden, D. J. (2003). "The New Dynamics of Strategy: Sense-Making in a Complex and Complicated World." *IBM Systems Journal*, 42(3), 462-483.
- Snowden, D. J., & Rancati, A. (2021). *Managing Complexity (and Chaos) in Times of Crisis: A Field Guide for Decision Makers Inspired by the Cynefin Framework*. Publications de l'Université de Saint-Étienne.

### Pattern Language Literature

- Alexander, C., Ishikawa, S., & Silverstein, M. (1977). *A Pattern Language: Towns, Buildings, Construction*. Oxford University Press.
- Gamma, E., Helm, R., Johnson, R., & Vlissides, J. (1994). *Design Patterns: Elements of Reusable Object-Oriented Software*. Addison-Wesley.
- Fowler, M. (2002). *Patterns of Enterprise Application Architecture*. Addison-Wesley.

### Multi-Agent Systems Literature

- Wooldridge, M. (2009). *An Introduction to MultiAgent Systems* (2nd ed.). Wiley.
- Weiss, G. (Ed.). (2013). *Multiagent Systems* (2nd ed.). MIT Press.
- Stone, P., & Veloso, M. (2000). "Multiagent Systems: A Survey from a Machine Learning Perspective." *Autonomous Robots*, 8(3), 345-383.

### Knowledge Engineering and Large Language Models

- Xiong Jie (2024). "A Pattern Language for Knowledge Engineering with Large Language Models." *Internal Research Document*.
- Anthropic (2024). "Claude AI Documentation and Best Practices." https://www.anthropic.com/
- OpenAI (2023). "GPT-4 Technical Report." *arXiv preprint arXiv:2303.08774*.

### Research Methodology

- Creswell, J. W., & Creswell, J. D. (2017). *Research Design: Qualitative, Quantitative, and Mixed Methods Approaches* (5th ed.). SAGE Publications.
- Maxwell, J. A. (2012). *Qualitative Research Design: An Interactive Approach* (3rd ed.). SAGE Publications.
- Schön, D. A. (1983). *The Reflective Practitioner: How Professionals Think in Action*. Basic Books.

---

## Appendix C: Glossary

**Business Architecture (Research Process Architecture)**: The logical decomposition and process orchestration of research tasks, including stage division, task sequence, data flow, human-AI collaboration points, and knowledge transformation pathways. Distinct from technical architecture (which focuses on how to build), business architecture focuses on what to build and why.

**Technical Architecture**: The implementation mechanisms of MAS systems, including agent definition methods, communication protocols, data storage, parallel execution, etc. The declarative multi-agent architecture discussed in this paper (Prompt-Defined Agent, three-layer separation, file system data bus, etc.) belongs to the technical architecture level.

**Domain Decomposition**: The process of research evolving from high uncertainty to low uncertainty, typically following the path Chaotic → Complex → Complicated → Clear. Each decomposition adds structure and reduces uncertainty, representing knowledge accumulation and order establishment.

**Research-Oriented Multi-Agent Systems (Research MAS)**: Multi-agent systems whose boundary is the research process itself (not the research object), aimed at knowledge discovery and insight generation, primarily processing unstructured qualitative materials.

**Exemplar**: In pattern language, an exemplar is a complete, reusable design case including context, problem, solution, examples, design principles, and other elements. Unlike abstract design patterns, exemplars are concrete, validated practices.

**Human-AI Collaboration Point**: Specific moments and interfaces in MAS business architecture where human intelligence intervention is required. Different Cynefin domains have different human-AI collaboration patterns.

**Complex-to-Complicated Transformation Pattern**: A key design pattern in the Complex domain where human insight (such as constructing a theoretical framework) decomposes a Complex task into a Complicated task, enabling AI to lead subsequent structured analysis.

**Information Existence**: A key criterion for judging which Cynefin domain a research task belongs to. If information needed to complete the task basically doesn't exist, the task belongs to the Chaotic domain; if information exists but requires integrative understanding, it belongs to the Complex domain; if information exists and the analytical path is clear, it belongs to the Complicated or Clear domain.

---

## Author's Note

This paper is part of the AgentForge project, dedicated to exploring applications of declarative multi-agent systems in research. All exemplars in this paper come from real research practice:

- **DSI (Digital Sovereignty Index) Evaluation**: A research project systematically assessing digital sovereignty in BRICS countries
- **South Africa Class Analysis**: Research applying Marxist theory to analyze South Africa's social class structure
- **News on China**: A weekly China news publication for international audiences, requiring high-quality editorial curation
- **Rongjiang Village Super Research**: Fieldwork research on the Rongjiang "Village BA/Village Super" phenomenon and digital technology's role in rural revitalization in Guizhou

The accumulated experience from these real cases provides the pattern language proposed in this paper with a foundation of practical validation.

We welcome researchers and AI system designers from different disciplines to:
- Apply these exemplars to your research
- Contribute new exemplars and variants
- Critique and refine this framework
- Jointly explore the future of human-AI collaborative research

**Project Homepage**: https://github.com/[TBD]

**Contact**: [TBD]

---

**Document Version**: v1.0  
**Completion Date**: November 6, 2025  
**Word Count**: Approximately 30,000 words  
**Authors**: Xiong Jie and the AgentForge Team

---

*This document is licensed under [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).*

