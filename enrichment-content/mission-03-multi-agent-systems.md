# Mission 03: Multi-Agent Systems

**Codename:** Operation Symphony
**Duration:** ~45 minutes

## Mission Brief

This mission transforms a single agent into a multi-agent system: an orchestrated team of specialised agents that work together to handle complex hiring challenges. It's upgrading from a solo operator to commanding a specialised task force.

Like a symphony orchestra where each musician plays their part in perfect harmony, you add two critical specialists to the existing Hiring Agent:
- **Application Intake Agent** - processes resumes automatically
- **Interview Prep Agent** - creates comprehensive interview materials

These agents work together seamlessly under the main orchestrator.

## Learning Objectives

- When to use child agents vs connected agents
- How to design multi-agent architectures that scale
- Creating child agents for focused tasks
- Establishing communication patterns between agents
- Building the Application Intake Agent and Interview Prep Agent

## What Are Connected Agents?

In Copilot Studio, you can create multi-agent systems - networks of specialised agents that work together to handle complex workflows.

Think of it like a real-world organisation: instead of one person doing everything, you have specialists who excel at specific tasks and collaborate when needed.

### Why Multi-Agent Systems Matter

| Benefit | Description |
|---------|-------------|
| **Scalability** | Each agent can be developed, tested, and maintained independently by different teams |
| **Specialisation** | Agents can focus on what they do best - data processing, user interaction, decision-making |
| **Flexibility** | Mix and match agents, reuse across projects, evolve incrementally |
| **Maintainability** | Changes to one agent don't necessarily affect others, making updates safer |

### Real-World Example: Hiring Process

Multiple agents might work together with different responsibilities:
- **Resume intake** - document parsing and data extraction
- **Scoring** - evaluating resumes and matching to job requirements
- **Interview preparation** - deep reasoning about candidate fit
- **Candidate communication** - empathetic communication abilities

Rather than building one massive agent that handles all these skills, create specialised agents for each area and orchestrate them together.

## Child Agents vs Connected Agents: The Key Difference

Copilot Studio offers two ways to build multi-agent systems:

### Child Agents

Child agents are lightweight specialists that live within your main agent. Think of them as specialised teams within the same department.

**Key Technical Details:**
- Live within the parent agent with a single configuration page
- Tools and Knowledge stored at parent agent, configured to be "Available to" the child agent
- Share topics of their parent agent
- Don't need separate publishing - automatically available within parent agent
- Changes can be performed in the same shared workspace

**Use Child Agents When:**
- A single team manages the entire solution
- You want to logically organise tools and knowledge into sub-agents
- You don't need separate authentication or deployment for each agent
- The agents won't be published separately or used independently
- You don't need to reuse agents across multiple solutions

**Example:** An IT helpdesk agent with child agents for:
- Password reset procedures
- Hardware troubleshooting
- Software installation guides

### Connected Agents

Connected agents are full-fledged, independent agents that your main agent can collaborate with. Think of them as separate departments working together on a project.

**Key Technical Details:**
- Have their own topics and conversation flows
- Operate independently with own settings, logic, and deployment lifecycle
- Must be published before they can be added to and used by other agents
- Changes must be published before they can be used by calling agent

**Use Connected Agents When:**
- Multiple teams develop and maintain different agents independently
- Agents need their own settings, authentication, and deployment channels
- You want independent application lifecycle management (ALM) for each agent
- Agents should be reusable across multiple solutions

**Example:** A customer service system connecting to:
- A billing agent maintained by the finance team
- A technical support agent maintained by the product team
- A returns agent maintained by the operations team

**Pro Tip:** You can mix both approaches! Your main agent could connect to external agents from other teams while also having its own child agents for specialised internal tasks.

## Multi-Agent Architecture Patterns

| Pattern | Description | Best For |
|---------|-------------|----------|
| **Hub and Spoke** | A main orchestrator agent coordinates with multiple specialised agents. The orchestrator handles user interaction and delegates tasks | Complex workflows where one agent coordinates specialised tasks |
| **Pipeline** | Agents pass work sequentially from one to the next, each adding value before passing to the next stage | Linear processes like application processing (intake → screening → interview → decision) |
| **Collaborative** | Agents work together simultaneously on different aspects of the same problem, sharing context and results | Complex analysis requiring multiple perspectives or expertise areas |

You may even have a hybrid of two or more patterns.

## Agent Communication and Context Sharing

When agents work together, they need to share information effectively:

### Conversation History
- By default, when a main agent calls a child or connected agent, it can pass along the conversation history
- This gives the specialist agent full context about what the user has been discussing
- Can be disabled for security or performance - good defence against data leakage

### Explicit Instructions
Your main agent can give specific instructions to child or connected agents:
- Example: "Process this resume and summarise their skills for the Senior Developer role"

### Return Values
Agents can return structured information back to the calling agent, allowing the main agent to use that information in subsequent steps or share with other agents.

### Dataverse Integration
For complex scenarios, agents can share information through Dataverse or other data stores, allowing for persistent context sharing across multiple interactions.

## Application Intake Agent (Child Agent)

### Responsibilities
- Parse resume content from PDFs provided via interactive chat
- Extract structured data (name, skills, experience, education)
- Match candidates to open roles based on qualifications and cover letter
- Store candidate information in Dataverse for later processing
- Deduplicate applications using email address from resume

### Why Child Agent?
- Specialised for document processing and data extraction
- Doesn't need separate publishing
- Part of overall hiring solution managed by same team
- Focuses on specific trigger (new resume received)
- Invoked from the Hiring Agent

## Interview Prep Agent (Connected Agent)

### Responsibilities
- Create interview packs with company information, role requirements, and evaluation criteria
- Generate interview questions tailored to specific roles and candidate backgrounds
- Answer general questions about job roles and applications for stakeholder communication

### Why Connected Agent?
- Talent acquisition team might use it independently across multiple hiring processes
- Needs its own knowledge base of interview best practices and evaluation criteria
- Different hiring managers might customise its behaviour for their teams
- Could be reused for internal positions, not just external hiring

## Lab Highlights

### Hiring Agent Configuration
The central orchestrator gets configured with:
- **Instructions:** "You are the central orchestrator for the hiring process. You coordinate activities, provide summaries, and delegate work to specialized agents."
- **Generative AI orchestration:** Enabled
- **Content moderation:** Moderate
- **File uploads:** Enabled
- **Web/general knowledge:** Disabled (only use configured sources)

### Agent Flow for Resume Upload
Uses Agent Flows rather than Topics because this multi-step backend process requires:
- Deterministic execution
- Integration with external systems
- Structured automation for file processing, data validation, and database upserts
- No dependency on user interaction

**Flow Components:**
1. Input parameters: Resume (File), Message (Text), UserEmail (Text)
2. Create Resume record in Dataverse
3. Upload Resume PDF file
4. Return Resume Number to agent

### Tool Configuration Best Practices
- Use strict rules in descriptions: "STRICT RULE: Only call this tool when referenced in the form 'Resume Upload' and there are Attachments"
- Set "When this tool may be used" to "only when referenced by topics or agents" for child agent tools
- Use Power Fx formulas to extract file content and names from chat attachments

## Key Concepts Summary

1. **Single vs Multi-Agent:** One agent doing everything vs specialists collaborating
2. **Child vs Connected:** Same team/solution vs independent teams/publishing
3. **Architecture Patterns:** Hub-and-spoke, pipeline, or collaborative
4. **Context Sharing:** Conversation history, explicit instructions, return values, Dataverse
5. **Tool Isolation:** Use "only when referenced" to prevent tools leaking to wrong agents

## Skills Mastered

- Understanding when to use child agents vs connected agents
- Designing scalable multi-agent architectures
- Creating child agents for focused tasks
- Establishing communication patterns between agents
- Building specialised agents (Application Intake, Interview Prep)

---

*Source: Microsoft Agent Academy - Operative Curriculum, Mission 03*
