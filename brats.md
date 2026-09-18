# KATHA AI

## 1. Team Details

**Team Name / ID:** Team Brats

**Team Lead:** Mokshagna Reddy Enegula

**Team Members:**

<!--
One line per person, including the team lead. Role is optional.
Pick one, combine two, write your own, or leave it blank:
  Agent Whisperer (agents, prompts, LLMs)
  Backend Developer
  Frontend Developer
  UI/UX Designer
  Integrations Engineer (APIs, tools, connecting services)
  Data Engineer (data, databases, retrieval)
  Product & Pitch Lead (idea, presentation, demo)
  Cool Team Member (a bit of everything)
-->

- Sahithi Rakonda 
- Pisipati Ankur  

**Repo Link (Optional):** [Link, or N/A]

**Demo Link (Optional):** [Link, or N/A]

---

## 2. Problem Statement

<!-- Paste the full problem statement exactly as it was given to you. Don't shorten, fix, or reword anything. No character limit here. -->

Multi-Agent Narrative Framework

The Challenge

Build a multi-agent framework and a functional, user-friendly Interface (UI) that allows users to interact with, alter, and expand stories from any text-based media source. Participants must design and structure their multi-agent system to process input media dynamically and execute narrative transformations.
Core Requirements
Universal Text Ingestion: The framework must be capable of ingesting any arbitrary text-based source file or document (e.g., movie scripts, TV show transcripts, novel chapters, PDFs, or raw text uploads) to establish its source lore.

User Interface (UI): The system must feature a clean, intuitive UI that allows users to easily upload media text, select characters or timeline checkpoints, choose capabilities, and interact with or view generated outputs.

Supported Capabilities (Target at least one)

Perspective Shifting: View any scene or timeline strictly from the point of view of a specific character.
Narrative Divergence: Intervene at a specific plot point to trigger a "butterfly effect," generating alternate, logically consistent plot trajectories and endings.
World Expansion: Generate tonally accurate prequel or sequel plots based on the uploaded baseline text.
Character Spin-offs: Produce a dedicated, standalone story focusing on a specific secondary or fan-favorite character.
Interactive Character Interviews: Chat directly with a character at a specific point in the story, where the agent responds strictly according to that character's personality and knowledge up to that exact moment.
Missing Scene Generation: Fill in narrative gaps by generating what occurred off-screen or between chapters.
Universe Crossovers: Ingest two distinct text sources and synthesize a cohesive crossover story that respects the rules of both worlds.
Examples of Expected Outputs

Upload a script PDF and view a major scene exclusively from a minor character's localized perspective via the UI.
Paste a novel chapter, change a key decision made by the protagonist, and watch the system output the restructured subsequent storyline.
Select a TV transcript and use the interactive chat interface to interrogate a character mid-timeline without breaking their universe logic or knowledge limits.
Brownie Points For:

Custom Capabilities: Thinking outside the box and implementing your own unique narrative capabilities beyond the ones listed above.
Exceptional UI/UX: Going beyond a basic interface to deliver a highly polished, immersive, and seamless user experience.



---

## 3. TL;DR

<!-- One line each. A judge should get your idea in 10 seconds. -->

**Problem:** Stories are locked into a single narrative, making it difficult to explore different perspectives, choices, and outcomes.

**Solution:** Katha AI turns a story into a structured narrative workspace with specialized agents for controlled story transformations.

**Who benefits:**  Readers and creators can explore new perspectives, choices, scenes, and timelines while preserving the source context.


---

## 4. Scope of the Project

**What are you building?**

Katha AI is an interactive narrative workspace that takes story text, extracts its characters, events, timeline and world rules, and lets users transform the story through specialized narrative capabilities. The POC demonstrates six core transformations plus a custom Tone Rewrite.

**How does it solve the problem statement?**

Instead of treating the source as plain text, Katha first builds structured narrative context. Each capability then uses that context with task-specific constraints to generate transformations while maintaining character, event, timeline and world consistency.

**Key features you're building for this hackathon:**

<!-- Up to 5 features. -->

- Automatic extraction of characters, events, timeline checkpoints and world rules
- Perspective shifting from a selected character's point of view
- Butterfly-effect divergence from a selected plot decision
- Timeline-aware multi-turn character interviews
- Missing scenes, prequels, sequels, spinoffs and custom tone rewriting

**What are you deliberately NOT doing? (Optional)**

The current POC does not implement Universe Crossover or persistent multi-user storage. Both are planned extensions requiring dual story contexts and persistent infrastructure.

---

## 5. Why an Agentic Approach?

<!-- This is an Agentic AI hackathon, so this is one of the most important answers in the file. Be specific. "It uses an LLM" is not an answer. -->

**What does your agent decide or do on its own?**

<!-- e.g. plans its steps, picks which tool to call, handles unexpected input, retries when something fails, hands work to another agent. -->

Katha AI dynamically selects the narrative workflow required by the user's request. It first extracts structured lore from the source, then assembles the relevant lore, source context and task-specific constraints for the selected capability. The resulting specialized agent generates the transformation, while Interview mode maintains state across turns.

**Why wouldn't a fixed script, if-else rules, or a simple chatbot be enough?**

The seven capabilities require fundamentally different reasoning constraints. Perspective Shift controls viewpoint and knowledge, Divergence preserves causal continuity after a changed decision, Interview freezes knowledge at a timeline point, and Tone Rewrite changes emotion without changing plot facts. A capability-based agent architecture lets each workflow apply its own rules while sharing the same story context.

---

## 6. Who It's For & What Changes

**Who or what is this for?**

<!-- Doesn't have to be end users. It could be people, a team, a business, developers, or an internal system or process. -->

Readers, writers, screenwriters, game creators and storytellers who want to actively explore fictional worlds.

**The world today, without your solution:**

<!-- What happens right now? Who struggles, and what does it cost them in time, money, effort, errors, or missed opportunities? -->

A finished story normally has one fixed sequence of events. Exploring it from another character's perspective, changing a decision, filling a missing scene or interviewing a character requires manual rewriting and continuity tracking. General LLMs can perform these tasks, but the user must repeatedly provide context and constraints.

**The world with your solution, fully built and scaled to production:**

<!-- Imagine your whole idea is built properly and used by everyone it's meant for. What's different? -->

A user provides a story once and Katha AI builds a reusable narrative knowledge base. Users can then explore different perspectives, decisions, characters and timelines through dedicated workflows, while agents retrieve the relevant source context and maintain narrative constraints.

**What your hackathon build actually delivers today:**

<!-- Of everything you proposed, which part have you built, and which part of the problem does that piece solve right now? A small piece that truly works is a great answer. -->

The POC is a single-process Streamlit application. Users paste story text, extract structured lore, select one of seven available capabilities, configure its parameters and receive streamed generation. Interview mode provides multi-turn interaction with a character whose knowledge is frozen to a selected timeline point.

**Before vs. After**

<!--
2 to 4 rows. Pick things that change: time, cost, effort, accuracy, scale, reach, manual work, risk.
Max 80 characters per cell. Replace the example row with your own.
-->

|      What Changes     |     Today                |   With Our Current Build     |    At Production Scale       |
|-----------------------|--------------------------|------------------------------|------------------------------|
| Story exploration     | Manual rewriting         | Capability-driven generation |Persistent story workspace    |
| Perspective	          |Rewrite scenes manually	 |Select character + scene	    |Lore-grounded viewpoint       |
|Alternate outcomes	    |Manually plan consequences|	Change a decision	          |Persistent branching timelines|
|Character interaction	|Generic conversation	     |Timeline-aware interview	    |Persistent character sessions |

---

## 7. Architecture & Agents

<!--
All the examples in this section describe ONE made-up project, a college helpdesk agent,
so you can see how the parts fit together. Aim for this level of detail, no more.
You don't need to list every library or every function.
-->

**How is your system put together?**

<!--
Example:
Students ask questions in a web chat. A Triage Agent sorts each message, an Answer Agent
replies using college policy documents, and anything needing a human becomes a helpdesk ticket.
-->

The current POC uses a lightweight Streamlit + Python architecture. Story text is sent to a Lore Extraction Agent using Groq's Llama model, which produces structured characters, events, timeline checkpoints and world rules. When the user selects a capability, the corresponding specialized prompt workflow combines that lore with source context and task constraints, then streams the generated result back through the UI.

The production architecture defined in our roadmap extends this foundation with document loaders, RAG/ChromaDB, LangGraph orchestration, persistent sessions and scalable APIs.

### 7.1 Agents

<!--
One line per agent. For each one, say what its job is, which model it uses and why that model
fits the job, and what it talks to (other agents, APIs, databases, services).

Example:
- **Triage Agent:** Reads each message and decides if it's a policy question, a complaint, or needs a human. Uses Llama 3.1 8B locally, since sorting is simple and student data stays on our machine. Talks to the Answer Agent and Web Chat.
- **Answer Agent:** Answers policy questions from college documents and files a ticket when approval is needed. Uses Claude Sonnet because it handles long policy text and reasons well about exceptions. Talks to College Docs Store and Helpdesk Ticket API.
-->

- **Lore Extraction Agent:** Converts raw story text into structured narrative knowledge including characters, roles, traits, events, timeline checkpoints, world rules and a summary. It uses Llama 3.3 70B through Groq because the POC prioritizes fast structured extraction.
- **Perspective Agent:** Rewrites a selected scene strictly through a chosen character's perspective, restricting narration to what that character can perceive, know or think.
- **Divergence Agent:** Changes one selected decision while preserving everything before the divergence and generating logically connected consequences afterward.
- **Interview Agent:** Simulates a selected character at a specific timeline checkpoint. It maintains multi-turn conversation while restricting the character from using future knowledge.
- **Missing Scene Agent:** Generates a scene between two established narrative points while maintaining continuity with the surrounding story.
- **Expansion Agent:** Generates a prequel or sequel while respecting the established world, character traits, timeline and narrative style.
- **Spinoff Agent:** Creates a standalone character-focused story based on the selected character's established personality and role.
- **Tone Agent:** Custom capability that changes the emotional register of a passage while keeping the underlying plot facts, events and outcomes unchanged.

### 7.2 Services, APIs, Databases & Memory

<!--
One line for everything that isn't an agent: databases, APIs, external services, tools,
and your interface (web app, bot, CLI). Say what it is, what it does, and who uses it.
Mention if it's mocked.

Example:
- **College Docs Store (Chroma vector database):** Holds fee, exam, and hostel policy PDFs. Used by the Answer Agent.
- **Helpdesk Ticket API (mocked):** Creates a ticket for the right college office. Used by the Answer Agent.
- **Web Chat (Streamlit):** Where students type questions and see answers. Talks to the Triage Agent.
-->

- **Streamlit UI:** Handles story input, capability selection, parameters, chat and streamed generation.
- **Groq API:** Provides Llama 3.3 70B for lore extraction and narrative generation.
- **Lore Extractor:** Converts source text into structured narrative context.
- **Agent Prompt Layer:** Builds capability-specific instructions and constraints.
- **Session State:** Stores the active story, extracted lore and interview history.
- **Vector Database:** Not used in the POC; planned for production-scale retrieval.
- **Persistent Database:** Not used in the POC; planned for production sessions and metadata.

**How does your system remember things (memory & state)?**

<!--
Example:
Each chat keeps its last 10 messages in session memory so follow-up questions make sense.
Tickets are saved in SQLite so students can check their status later.
-->

The POC uses Streamlit session state to retain the active source text, extracted lore, selected capability and Interview conversation. This keeps the experience stateful within the current session without requiring database infrastructure.

For production, the roadmap introduces persistent session storage and a vector knowledge base so stories can be reopened and relevant context retrieved without reprocessing the complete source.

**Diagram Link (Optional):** 
```
┌─────────────────────────────────────────────────────────────────────┐
│                          USER BROWSER                               │
│                                                                     │
│  ┌──────────────┐  ┌─────────────────┐  ┌───────────────────────┐   │
│  │  Upload Zone │  │ Capability UI   │  │  Output / Chat Panel  │   │
│  │  (PDF/TXT/   │  │ (Selector,      │  │  (SSE Streaming,      │   │
│  │   DOCX/Paste)│  │  Char/Timeline) │  │   Typewriter Effect)  │   │
│  └──────┬───────┘  └────────┬────────┘  └──────────┬────────────┘   │
│         │                   │                       │               │
│         └──────────── React + TypeScript ───────────┘               │
└──────────────────────────┬──────────────────────────────────────────┘
                           │ HTTPS / SSE
┌──────────────────────────▼──────────────────────────────────────────┐
│                      FASTAPI BACKEND                                │
│                                                                     │
│  ┌─────────────┐  ┌──────────────┐  ┌─────────────┐                 │
│  │ /ingest     │  │ /agent/run   │  │ /sessions   │                 │
│  │ router      │  │ router (SSE) │  │ router      │                 │
│  └──────┬──────┘  └──────┬───────┘  └──────┬──────┘                 │
│         │                │                 │                        │
│         ▼                ▼                 ▼                        │
│  ┌──────────────────────────────────────────────────────────────┐   │
│  │                  INGESTION PIPELINE                          │   │
│  │                                                              │   │
│  │  Raw File → Loader → Chunker → Embedder → ChromaDB           │   │
│  │                         │                                    │   │
│  │                    Lore Extractor (LLM)                      │   │
│  │                         │                                    │   │
│  │                    Lore JSON Store (SQLite)                  │   │
│  └──────────────────────────────────────────────────────────────┘   │
│                                                                     │
│  ┌──────────────────────────────────────────────────────────────┐   │
│  │               LANGGRAPH MULTI-AGENT GRAPH                    │   │
│  │                                                              │   │
│  │   ┌─────────┐     ┌──────────────┐     ┌─────────────────┐   │   │
│  │   │ Router  │────▶│ LoreContext  │────▶│  Agent Node    │   │   │
│  │   │  Node   │     │ Node (RAG)   │     │  (specialized)  │   │   │
│  │   └─────────┘     └──────────────┘     └────────┬────────┘   │   │
│  │                                                  │           │   │
│  │                                                  ▼           │   │
│  │                                         ┌────────────────┐   │   │
│  │                                         │   LLM (GPT-4o) │   │   │
│  │                                         │   Streaming    │   │   │
│  │                                         └────────────────┘   │   │
│  └──────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────┘
         │                │                     │
         ▼                ▼                     ▼
   ┌──────────┐    ┌────────────┐       ┌──────────────┐
   │ ChromaDB │    │   Redis    │       │  SQLite /    │
   │ (vector  │    │ (session   │       │  PostgreSQL  │
   │  store)  │    │  state)    │       │  (metadata)  │
   └──────────┘    └────────────┘       └──────────────┘
         │
         ▼
   ┌──────────────┐
   │ OpenAI API   │
   │ (Embeddings  │
   │  + GPT-4o)   │
   └──────────────┘
```

### 7.3 Example Walkthrough

<!--
Take ONE realistic input and show how it moves through your system: which agent picks it up,
what gets passed on, which tools or databases are used, and what comes out at the end.
Up to 8 steps. If the flow branches, use 3a / 3b.

Example:
**Example input:** A student types "Can I pay my semester fee late? I'm waiting on my scholarship."

1. [Web Chat] Sends the message and the student's ID to the Triage Agent.
2. [Triage Agent] Classifies it as a fee-policy question and passes it to the Answer Agent.
3. [Answer Agent] Finds the late-fee policy (uses: College Docs Store) and sees scholarship cases need approval.
4. [Answer Agent] Explains the policy and files an approval request (uses: Helpdesk Ticket API).
5. [Web Chat] Shows the student the answer and their ticket number.

**Final output:** A clear answer quoting the late-fee policy, plus a ticket raised with the accounts office.
-->

**Example input:** A user pastes a novel chapter and selects: Capability: Perspective Shift Character: Antagonist  Request: "Show this scene entirely from the antagonist's perspective."

1. Story Input — Streamlit receives the source text.
2. Lore Extraction — Llama extracts characters, traits, events, timeline and world rules.
3. Capability Selection — The user selects Perspective Shift.
4. Context Assembly — The workflow combines the relevant lore with the source scene.
5. Constraint Application — The agent is instructed to use only the selected character's perspective and knowledge.
6. Generation — Llama generates the transformed scene through Groq.
7. Streaming — The response is streamed directly into the interface.
8. Interaction — The user can return to the workspace and run another transformation.

**Final output:** The same narrative scene retold exclusively through the antagonist's perspective while preserving established story context.

**Anything special about how your workflow runs? (Optional)**

<!--
An algorithm you use, how agents decide what to do next, routing logic, loops, agents working
in parallel, scoring, self-checks. Anything you want us to notice.

Example:
The Triage Agent gives a confidence score with every decision. Below 0.7, the message skips the
Answer Agent and goes straight to a human, so students never get a confident wrong answer.
-->

Katha AI is capability-driven rather than prompt-only. Every transformation has its own constraints. For example, Divergence preserves events before the selected decision, Tone Rewrite preserves plot facts, and Interview prevents the character from accessing events beyond the selected timeline checkpoint.

---

## 8. Tech Stack

<!-- Write N/A for any row that doesn't apply. Models are already listed per agent in 7.1. Max 60 characters per cell. -->

| Layer | Technology |
|---|---|
| **Frontend UI** | React + TypeScript + TailwindCSS + shadcn/ui |
| **Backend API** | Python FastAPI |
| **Agent Orchestration** | LangGraph (multi-agent graph) |
| **LLM Provider** | OpenAI GPT-4o (or Azure OpenAI) |
| **Embeddings & Vector Store** | OpenAI text-embedding-3-small + ChromaDB |
| **Document Ingestion** | LangChain document loaders (PDF, TXT, DOCX) |
| **State Management** | Redis (session state) |
| **Database** | SQLite (dev) / PostgreSQL (prod) for session metadata |
| **Streaming** | Server-Sent Events (SSE) |
| **Containerization** | Docker + Docker Compose |

---

## 9. What to Expect From Our Current Build

<!--
Be honest. Unfinished, faked, or hard-coded parts are completely normal at a hackathon.
Telling us means we judge what you actually built, and that works in your favour.
Max 120 characters per bullet.
-->

**Working:**

- Story-text ingestion through direct text input
- Automated lore extraction
- Character, event, timeline and world-rule display
- Six core narrative capabilities
- Custom Tone Rewrite capability
- Streaming AI generation
- Multi-turn Character Interview

**Partly working, mocked, or hard-coded:**

- Context is supplied directly to the model rather than retrieved through a vector database.
- Session state exists only for the active Streamlit session.
- The POC is optimized for demonstration rather than persistent production workloads.

**Not working or not built yet:**

- Universe Crossover
- Persistent multi-user story sessions
- Production database/vector infrastructure
- Full production API/frontend separation
-Scalable deployment architecture

**What we'd most like to be judged on:**

The core innovation demonstrated by our POC: turning static story text into structured narrative context and using specialized capability workflows to let users systematically explore, alter and expand that story through one interactive interface.

---

## 10. Future Scope

<!-- 2 or 3 things you're NOT building yet but plan to. If you clear the checkpoint, you may be asked to build one of them, so keep them concrete and doable. -->

### Idea 1

**Name:** Persistent Story Knowledge Base

**What it is:** Store source chunks and extracted lore in a persistent knowledge base.

**Why it matters:** Enables large stories, reusable projects and reliable retrieval across sessions.

**How we'd build it:** Add document loaders, semantic chunking, embeddings, ChromaDB and persistent lore storage.

**Done when:** A user can reopen a story and generate transformations without reprocessing the entire source.

### Idea 2

**Name:** Branching Narrative Timeline

**What it is:** Allow users to create, name and revisit alternate story branches after changing decisions

**Why it matters:** Converts one-time divergence generation into a persistent interactive story tree.

**How we'd build it:** Store each branch with its parent event, altered decision, generated events and resulting narrative state.

**Done when:** Users can navigate multiple alternate timelines from the same original story.

### Idea 3 (Optional)

**Name:** Cross-Universe Narrative Engine

**What it is:** Ingest two independent stories and generate a crossover that respects both universes.

**Why it matters:** Extends Katha AI from single-source transformation to multi-universe narrative reasoning.

**How we'd build it:** Maintain separate lore contexts for each source and introduce a dedicated Crossover Agent that reconciles characters, world rules and timelines.

**Done when:** A generated crossover consistently incorporates the established rules and characters of both source worlds.

---

## 11. Additional Notes (Optional)

<!-- Anything else you'd like us to know. -->

Katha AI is built around a simple idea: a finished story does not have to remain a fixed narrative.

The POC demonstrates the complete interaction loop:

Story → Lore → Capability → Constraints → Agent → Transformation → Interaction

Rather than building a generic chatbot that simply responds to prompts, Katha AI structures the source material first and then applies capability-specific narrative reasoning.

The current POC intentionally keeps the infrastructure lightweight so the core experience can be demonstrated quickly. Its architecture is designed to scale into persistent RAG, branching timelines, production APIs and multi-universe reasoning.
