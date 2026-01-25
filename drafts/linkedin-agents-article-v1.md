# LinkedIn Article: Microsoft Agent Academy - First Iteration

---

Most HR and knowledge workers think building AI agents requires coding skills.

It doesn't.

I recently completed Microsoft's Agent Academy Recruit curriculum, which takes you from zero to deploying functional AI agents in Microsoft 365 without writing a single line of traditional code. Here's what the journey looks like, and why it matters for anyone in HR, operations, or business roles.

---

**The Recruit curriculum covers 13 missions, each building on the last:**

The training uses a clever "spy academy" theme where each module is a mission. It sounds gimmicky, but it keeps things engaging across what could otherwise be dry technical content.

**Mission 00: Course Setup** gets your environment ready. You'll set up a Microsoft 365 account, activate a Copilot Studio trial (free for 90 days), create a developer environment, and configure a SharePoint site with sample data. This takes about 30 minutes and establishes the foundation for everything that follows.

**Mission 01: Introduction to Agents** covers the fundamentals. You'll learn the difference between conversational agents (back-and-forth dialogue, think HR chatbots) and autonomous agents (trigger-based, think automated travel booking). The key concept here is Retrieval-Augmented Generation (RAG), which lets agents pull information from your organisation's documents rather than relying solely on the LLM's training data. This is what prevents hallucination and keeps answers grounded in your actual policies.

**Mission 02: Copilot Studio Fundamentals** introduces the four building blocks of every agent:
- Knowledge (where it looks up information)
- Tools (actions it can perform)
- Topics (how it recognises intent)
- Instructions (rules, tone, and boundaries)

Understanding these four elements is crucial. The AI orchestrator uses them together to listen for triggers, apply your rules, search your data sources, and execute tasks.

**Mission 03: Declarative Agents** teaches you to extend Microsoft 365 Copilot itself. You'll build an IT helpdesk agent using natural language, add AI prompts as tools, and publish it to both M365 Copilot and Teams. The entire process is conversational, you describe what you want, and Copilot builds it.

**Mission 04: Creating Solutions** covers the often-overlooked topic of packaging. Solutions are containers that hold all parts of your agents for proper lifecycle management. You'll create publishers, manage versions, and learn why keeping agents separate from the Default solution matters for deployment and collaboration.

**Mission 05: Pre-built Agents** shows how to deploy Microsoft's ready-made templates. The Safe Travels agent, for example, helps employees with business travel questions. These templates include functioning topics, triggers, and sample knowledge. Perfect for learning how agents are structured or getting something useful deployed quickly.

**Mission 06: Custom Agents from Conversation** is where things get practical. You'll build a full IT helpdesk agent using only natural language prompts, then ground it with enterprise knowledge sources like SharePoint, documents, and websites. The generative orchestration feature means the agent dynamically decides which sources to search based on user questions.

**Mission 07: Topics and Triggers** goes deeper into conversation design. You'll learn about trigger phrases (the words that activate specific functionality), conversation nodes (the steps the agent follows), and Power Fx expressions for dynamic logic. This mission includes connecting to SharePoint data using connectors to retrieve filtered device lists based on user requests.

The remaining missions cover **Adaptive Cards** for rich interactive forms, **Agent Flows** for backend automation, **Event Triggers** for autonomous execution, **Publishing** to production channels, and **Understanding Licensing** for Copilot Studio and M365.

---

**The practical pattern that emerges:**

1. Describe your agent's purpose in plain language
2. Add knowledge sources (SharePoint, documents, websites)
3. Define guardrails and tone in the instructions
4. Test with real questions using the Activity Map
5. Publish to Teams or M365 Copilot

What surprised me was how much you can accomplish without involving IT. The curriculum is designed for makers, not developers.

---

**Where this connects to the future of HR work**

While completing this training, I came across the concept of "vibe coding", a term popularised by Nate Jones describing how non-technical professionals can use AI conversational tools to generate code and automate tasks that previously required software engineers.

Chris Walsh, an HR director at Select Finishing (a manufacturing company with employees across seven plants), exemplifies this shift. Two years ago, he had no coding background. Today, he's building SQL databases and creating API links from their HRIS software with zero IT help.

"I still don't know how to code, but I'm writing code," Walsh explains.

Through vibe coding, his small HR team has automated data flows and reporting, freeing time for strategic work and enabling real-time workforce insights. Problems that would have required extensive IT consultation are now solved independently.

The parallel to Microsoft's Agent Academy is striking. Both represent the same underlying shift: AI is democratising technical capabilities. What required specialists yesterday can be done by domain experts today, if they're willing to learn the new tools.

For HR professionals specifically, this creates an interesting opportunity. The combination of deep process knowledge (onboarding, benefits, recruitment) with low-code AI tools (Copilot Studio, Power Platform) means HR teams can build agents tailored to their actual workflows, not generic solutions from vendors who don't understand the nuances.

The risk is staying on the sidelines. The opportunity is becoming the person who bridges HR expertise with AI capability.

---

**What's next: The Operative level**

I'll be auditing and reviewing the next level of Agent Academy in detail: the Operative curriculum.

This is where things get seriously interesting for HR and recruitment. The Operative track focuses on building a complete **Hiring Agent** system, a multi-agent architecture where specialised agents collaborate on recruitment tasks:

- **The Hiring Agent** serves as the central orchestrator, coordinating the entire process and storing data in Dataverse
- **The Application Intake Agent** automatically processes resumes, extracts structured candidate data, and matches applicants to open roles
- **The Interview Prep Agent** generates tailored interview questions and evaluation materials based on candidate backgrounds

The curriculum covers multi-agent communication patterns, agent flows for backend automation, and how to design systems where child agents handle specific tasks while connected agents collaborate across teams.

In short: it's building the kind of recruitment automation that currently requires enterprise software contracts or custom development.

More to come as I work through it.

---

Curious how others are approaching AI agents in HR contexts. If you've experimented with Copilot Studio or similar tools for people operations, what's worked?

#AgenticAI #CopilotStudio #HRTech #FutureOfWork #MicrosoftCopilot #AIinHR
