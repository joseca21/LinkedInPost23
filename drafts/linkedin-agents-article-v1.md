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

**A different perspective: What if candidates built their own agents?**

While exploring Microsoft's Agent Academy, I came across a compelling idea from Nate Jones that flips the script entirely.

The premise is simple but uncomfortable: You see a role on LinkedIn posted three hours ago. It already has 400 applicants. Most people react by trying to optimise their way through the noise, tweaking resume keywords to beat the ATS (Applicant Tracking System).

Jones argues this is optimising for the wrong thing. You're optimising for a robot whose only job is to filter people out. Recruiters spend an average of six seconds scanning a resume. They're looking for "No," not "Yes."

**The alternative: Build a Personal Search Engine**

Instead of pushing a static wall of text at someone who doesn't have time to read it, Jones proposes building an interactive interface, a "Digital Twin" of your professional brain.

Picture this: A hiring manager lands on your portfolio site. Instead of scrolling through bullet points, they're greeted by a chat window. They can ask specific questions relevant to their needs: "Have you ever led a team through a crisis?" "How do you approach stakeholder management?" The interface answers for them, citing your actual experience from performance reviews, project notes, and past work.

The technology behind this is RAG (Retrieval-Augmented Generation), the same concept covered in the Agent Academy curriculum. You upload your documents (old CVs, performance reviews, project notes, even messy working documents that show how you think), and the AI retrieves relevant information to answer queries. Crucially, it provides citations, proving it's not hallucinating but pulling from your actual history.

**Vibe Coding makes this accessible**

Here's where it connects back to low-code tools. Jones introduces "Vibe Coding", the idea that building applications is no longer about syntax (knowing where the semicolon goes) but about vision (knowing what you want the app to do).

Using AI builders like Lovable, you can describe what you want in plain English: "Create a portfolio site. Dark theme. Resume on the left, chatbot on the right. Connect to Supabase for documents." The AI generates the code, layout, and database connection. What used to take weeks of engineering time can now be done in a weekend.

**The Pattern Interrupt**

The strategy isn't to upload this to an ATS and hope. When you reach out to a hiring manager, you don't say "Here is my CV." You say: "I know you're busy. I built an AI interface trained on my background so you can query my experience directly. Ask it exactly what you're looking for to see if I'm a match."

Why this works:
- **Differentiation**: You're the only person doing this
- **Proof of Work**: The medium is the message. By sending an AI app, you prove you understand modern tools. You aren't claiming to be capable; you're demonstrating it
- **Control**: You control the narrative. The AI answers with the tone and focus you designed

Jones argues that the CV is a dying format. We're moving to a world of "Proof of Work." Words are cheap, anyone can use ChatGPT to write a perfect cover letter. Building is perceived as hard. By building this, you signal you're in the top 1% of candidates who take initiative.

The parallel to Agent Academy is striking: both represent the same underlying shift. What required specialists yesterday can be done by motivated individuals today, if they're willing to learn the new tools.

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
