# Foundations: Introduction to Agents

---

## SECTION 1: SUMMARY

This section provides a condensed overview of the Introduction to Agents mission for quick reference.

### Mission Overview

**Codename:** Operation AI Agent Decode
**Duration:** ~30 minutes (intel only, no fieldwork)
**Level:** Recruit

### Key Objectives

- Understand what conversational AI is
- Learn how Large Language Models (LLMs) power chat experiences
- Understand Retrieval-Augmented Generation (RAG)
- Distinguish between conversational agents and autonomous agents
- See how agents in Copilot Studio leverage these concepts

### Core Concepts

#### What Is Conversational AI?

Any system that can understand, process, and respond to human language (text or speech) in a natural way. Examples include chatbots and virtual assistants. Most modern conversational AIs rely on Large Language Models (LLMs).

#### Large Language Models (LLMs)

| Concept | Description |
|---------|-------------|
| **Training Data** | Terabytes of text (web pages, books, articles) giving "world knowledge" |
| **Tokenization** | Text broken into smaller units; model predicts one token at a time |
| **Context Window** | Limit on how many tokens the model can "see" at once |
| **Prompting** | Your question/request sent to the LLM; better prompts = better responses |

**Key analogy:** An LLM is like "super-smart autocomplete" - extremely good at predicting the next best word in a sequence.

#### Retrieval-Augmented Generation (RAG)

RAG addresses LLM limitations (hallucination, outdated info) by letting the model "look up" fresh information:

1. **User Query** - User asks a question
2. **Retriever Step** - System queries knowledge sources (documents, APIs, SharePoint)
3. **Augmentation** - Retrieved data appended to the prompt
4. **Generation** - LLM generates response grounded in up-to-date data

### Conversational vs Autonomous Agents

| Aspect | Conversational Agents | Autonomous Agents |
|--------|----------------------|-------------------|
| **Interaction** | Requires two-way dialogue | No dialogue required |
| **Trigger** | Waits for user input | Kicks off from external triggers |
| **Operation** | Back-and-forth chat | Multi-step processes without human prompts |
| **Use cases** | Customer support, FAQs, Q&A | Automated workflows, background tasks |

**Key Difference:** Conversational agents wait for user input. Autonomous agents execute based on external triggers and perform actions without human interaction.

### Agents in Copilot Studio

| Feature | Description |
|---------|-------------|
| **Visual Agent Designer** | Drag and drop canvas to build, test, deploy |
| **Model Selection** | Choose from OpenAI, Anthropic, Custom Models |
| **Knowledge** | Out-of-the-box RAG with SharePoint, OneDrive, Dataverse |
| **Tools** | Hook into Power Automate flows, APIs, Dataverse |
| **Multi-Modal Support** | File uploads and speech conversations |
| **Publishing** | Deploy to M365 Copilot, websites, multiple channels |

### Key Takeaways

- **LLMs = The "Brain"** - Responsible for language understanding and generation
- **RAG = Real-Time Knowledge** - Bridges static LLM and ever-changing data sources
- **Conversational = Dialogue-based** - Back and forth interaction
- **Autonomous = Trigger-based** - No dialogue, performs actions independently

---

## SECTION 2: VERBATIM CONTENT

This section contains the original source material in its complete form.

---

### Recruit Curriculum Modules

Introduction to Agents

Copilot Studio Fundamentals

Create A Declarative Agent For Microsoft 365 Copilot

Creating A Solution

Using Prebuilt Agents

Create Agent From Conversation

Add New Topic With Trigger

Add Adaptive Cards

Add An Agent Flow

Add Event Triggers

Publish Your Agents

Understanding Licensing

Course Completion Badge Recruit

Operative
Commander (Coming Soon)

Special Ops (Coming Soon)

---

### 🚨 Mission 01: Introduction to Agents

🕵️‍♂️ CODENAME: OPERATION AI AGENT DECODE

⏱️ Operation Time Window: ~30 minutes – intel only, no fieldwork required

#### 🎥 Watch the Walkthrough

Introduction to Agents video thumbnail

#### 🎯 Mission Brief

Welcome, Recruit. Before we dive into building agents, you need a firm grasp of the AI concepts that power them. This mission will equip you with foundational knowledge of conversational AI, large language models (LLMs), retrieval-augmented generation (RAG), and the types of agents you can create in Copilot Studio.

#### 🔎 Objectives

In this mission, you'll learn:

- What conversational AI is
- How Large Language Models (LLMs) power chat experiences
- What Retrieval-Augmented Generation (RAG) brings to the table
- The distinction between conversational agents and autonomous agents
- How agents in Copilot Studio leverage these concepts

Let's dive in!

#### What Is Conversational AI?

Conversational AI refers to any system that can understand, process, and respond to human language (text or speech) in a way that feels natural. Think chatbots on websites that help you figure out where your order is or virtual personal assistants in your favorite apps. Under the hood, most modern conversational AIs rely on Large Language Models (LLMs).

#### Large Language Models (LLMs) 101

At the core of most conversational AI systems are Large Language Models, neural networks trained on massive amounts of text. These models learn the statistical patterns of language so they can generate coherent sentences, answer questions, brainstorm ideas or even create content. Key points to understand:

**Training Data:** LLMs ingest terabytes of text (web pages, books, poems, articles). This "world knowledge" lets them respond on many topics.

**Tokenization:** Text is broken into smaller units called tokens (words, subwords, or characters). The model predicts one token at a time.

**Context Window:** Each LLM has a limit on how many tokens it can "see" at once. Beyond that limit, prior tokens get shortened.

**Prompting:** You interact with an LLM by sending it a prompt (your question or request in a block of text). The better your prompt, the more focused and relevant the response from the LLM.

**Pro Tip:** A common analogy is that an LLM is like a "super-smart autocomplete." It doesn't truly understand meaning like a human brain, but it's extremely good at predicting the next best word (or phrase) in a sequence.

#### Retrieval-Augmented Generation (RAG)

When LLMs rely solely on static training data, they might hallucinate or become outdated. RAG addresses this by letting the model "look up" fresh information before composing an answer. At a high level, RAG works like this:

1. **User Query:** A user asks a question (e.g., "What's the latest on Contoso's quarterly earnings?").

2. **Retriever Step:** The system queries a knowledge source (documents, public websites, internal databases, SharePoint libraries, etc.) to find relevant information.

3. **Augmentation:** Retrieved data gets appended to or prepended before sending to the LLM.

4. **Generation:** The LLM ingests both the user's question and the retrieved context, then generates a response that's grounded in up-to-date data.

With RAG, your agent can call internal company wikis, APIs, or search an FAQ knowledge base—and return answers that aren't limited to the static data that the model is trained on.

#### Conversational vs. Autonomous Agents

In the context of Copilot Studio, the term agent can refer to multiple flavors of AI assistants. It's helpful to draw a line between:

**Conversational Agents:**

- Requires two-way dialogue (text or speech) to work.
- Persist context across multiple turns of a conversation.
- Can hook into external tools or APIs (e.g., call a Power Automate flow, send calendar invites, manipulate data in Dataverse).
- Ideal for customer support, FAQs, guided interactions or simple Q&A.
- Examples:
  - An agent in Microsoft Teams that answers HR policy questions.
  - An agent on a public website that answer questions about your products.

**Autonomous Agents:**

- Go beyond back-and-forth chat; they can kick off and take actions on behalf of the user.
- Use LLM reasoning loops (think "plan → act → observe → replan") to complete tasks.
- Can also hook into external tools or APIs (e.g., call a Power Automate flow, send calendar invites, manipulate data in Dataverse).
- Operate without constant human prompts. Once triggered, they can handle multi-step processes autonomously.
- Examples:
  - An agent that generates a travel itinerary, books flights, and emails confirmations as soon as you put in a travel request in your backend system.
  - A "Meeting Summarizer" agent that joins a Teams call, transcribes it in real time, and writes an executive summary to OneNote.

**Key Difference:** Conversational agents wait for user input and require back and forth dialogue to work. Autonomous agents can execute based on external triggers and perform actions without any human interaction.

#### Agents in Copilot Studio

Copilot Studio unifies both conversational and autonomous scenarios under one framework. Here's how Copilot Studio helps you build agents:

**Visual Agent Designer:** A drag and drop canvas to build, test and deploy your agents.

**Model (LLM) Selection:** Select from various AI models (OpenAI, Anthropic, Custom Models) to choose the best LLM for your agent scenario.

**Knowledge:** Use out-of-the-box integrations for SharePoint, OneDrive, Dataverse, etc, enabling RAG out of the box.

**Tools:** Hook into external tools or APIs to enable your agent to perform actions (e.g., call a Power Automate flow, send calendar invites, manipulate data in Dataverse)

**Multi-Modal Support:** Copilot studio agents support file uploads and speech conversations.

**Publishing & Distribution:** Once your agent is ready, you can publish it to Microsoft 365 Copilot, embed it on your website or choose from several other deployment channels.

#### 🎉 Mission Complete

You've now completed your introduction to agents and foundational AI concepts. You understand:

**LLMs = The "Brain" of Your Agent**
- Responsible for language understanding and generation.

**RAG = Real-Time Knowledge Integration**
- Bridges the gap between a static LLM and ever-changing data sources.
- Retrieves and injects relevant documents or records into the LLM prompt.

**Conversational vs. Autonomous**
- Conversational: Focus on back and forth dialogue
- Autonomous: No dialogue required, kicks off from external triggers and performs actions autonomously

Next up, you'll explore the fundamentals of Copilot Studio!

Stay sharp, Recruit - your AI journey is just beginning!

#### 📚 Tactical Resources

🔗 Copilot Studio Documentation Home

---

*Source: Microsoft Agent Academy - Recruit Curriculum, Mission 01: Introduction to Agents*
