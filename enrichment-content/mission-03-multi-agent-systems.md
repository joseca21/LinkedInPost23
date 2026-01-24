# Mission 03: Multi-Agent Systems

---

## SECTION 1: SUMMARY

This section provides a condensed overview of Mission 03 for quick reference.

### Mission Overview

**Codename:** Operation Symphony
**Duration:** ~45 minutes
**Level:** Operative

### Key Objectives

- Understand when to use child agents vs connected agents
- Design multi-agent architectures that scale
- Create child agents for focused tasks
- Establish communication patterns between agents
- Build the Application Intake Agent and Interview Prep Agent

### Core Concept

Multi-agent systems are networks of specialised agents that work together. Instead of one monolithic agent, you have specialists who excel at specific tasks and collaborate when needed.

### Why Multi-Agent Systems Matter

| Benefit | Description |
|---------|-------------|
| **Scalability** | Each agent developed, tested, maintained independently |
| **Specialisation** | Agents focus on what they do best |
| **Flexibility** | Mix and match, reuse across projects |
| **Maintainability** | Changes to one agent don't affect others |

### Child Agents vs Connected Agents

| Aspect | Child Agents | Connected Agents |
|--------|--------------|------------------|
| **Relationship** | Live within parent agent | Independent agents |
| **Publishing** | No separate publishing needed | Must be published separately |
| **Configuration** | Share parent's tools/knowledge | Own settings and lifecycle |
| **Use case** | Single team, same solution | Multiple teams, reusable |
| **ALM** | Shared workspace | Independent lifecycle |

### Architecture Patterns

| Pattern | Description | Best For |
|---------|-------------|----------|
| **Hub and Spoke** | Orchestrator coordinates specialists | Complex delegated workflows |
| **Pipeline** | Sequential handoff between agents | Linear processes (intake → decision) |
| **Collaborative** | Simultaneous work on same problem | Multi-perspective analysis |

### Agent Communication Methods

1. **Conversation history** - Pass context to specialist agents
2. **Explicit instructions** - Give specific task directions
3. **Return values** - Structured data back to caller
4. **Dataverse integration** - Persistent shared storage

### Hiring System Agents

| Agent | Type | Responsibilities |
|-------|------|------------------|
| **Hiring Agent** | Parent | Central orchestrator |
| **Application Intake** | Child | Parse resumes, extract data, store in Dataverse |
| **Interview Prep** | Connected | Create interview packs, generate questions |

### Key Lab Concepts

- Agent Flows for deterministic backend processes
- Tool isolation: "only when referenced by topics or agents"
- Strict rules in descriptions for guardrails
- Power Fx formulas for extracting file content

---

## SECTION 2: VERBATIM CONTENT

This section contains the original source material in its complete form.

---

### 🚨 Mission 03: Multi-Agent Systems

🕵️‍♂️ CODENAME: OPERATION SYMPHONY

⏱️ Operation Time Window: ~45 minutes

#### 🎯 Mission Brief

Welcome back, Agent. In Mission 01, you built your main Hiring Agent giving you a solid foundation for managing recruitment workflows. But one agent can only do so much.

Your assignment, should you choose to accept it, is Operation Symphony - transforming your single agent into a multi-agent system: an orchestrated team of specialized agents that work together to handle complex hiring challenges. Think of it as upgrading from a solo operator to commanding a specialized task force.

Like a symphony orchestra where each musician plays their part in perfect harmony, you'll add two critical specialists to your existing Hiring Agent: an Application Intake Agent to process resumes automatically, and an Interview Prep Agent to create comprehensive interview materials. These agents will work together seamlessly under your main orchestrator.

#### 🔎 Objectives

In this mission, you'll learn:

- When to use child agents vs connected agents
- How to design multi-agent architectures that scale
- Creating child agents for focused tasks
- Establishing communication patterns between agents
- Building the Application Intake Agent and Interview Prep Agent

#### 🧠 What are connected agents?

In Copilot Studio, you're not limited to building single, monolithic agents. You can create multi-agent systems - networks of specialized agents that work together to handle complex workflows.

Think of it like a real-world organization: instead of one person doing everything, you have specialists who excel at specific tasks and collaborate when needed.

**Why multi-agent systems matter**

- Scalability: Each agent can be developed, tested, and maintained independently by different teams.
- Specialization: Agents can focus on what they do best. Perhaps one for data processing, another for user interaction, another for decision-making.
- Flexibility: You can mix and match agents, reuse them across projects, and evolve your system incrementally.
- Maintainability: Changes to one agent don't necessarily affect others, making updates safer and easier.

**Real-world example: Hiring process**

Consider our hiring workflow - multiple agents might work together with the following responsibilities:

- Resume intake requires document parsing and data extraction skills
- Scoring involves evaluating candidate resumes and matching them to job requirements
- Interview preparation needs deep reasoning about candidate fit
- Candidate communication requires empathetic communication abilities

Rather than building one massive agent that tries to handle all these different skills, you can create specialized agents for each area and orchestrate them together.

#### 🔗 Child agents vs connected agents: The key difference

Copilot Studio offers two ways to build multi-agent systems, each with distinct use cases:

**↘️ Child agents**

Child agents are lightweight specialists that live within your main agent. Think of them as specialized teams within the same department.

Key technical details:

- Child agents live within the parent agent and have a single configuration page.
- Tools and Knowledge are stored at the parent agent, but configured to be "Available to" the child agent.
- Child agents share the topics of their parent agent. Topics can be referenced by the child agent instructions.
- Child agents don't need separate publishing - they're automatically available within their parent agent once created. This makes testing easier because changes to the parent and child agents can be performed in the same shared workspace.

Use child agents when:

- A single team manages the entire solution
- You want to logically organize tools and knowledge into sub-agents
- You don't need separate authentication or deployment for each agent
- The agents won't be published separately or used independently
- You don't need to reuse agents across multiple solutions

Example: An IT helpdesk agent with child agents for:

- Password reset procedures
- Hardware troubleshooting
- Software installation guides

**🔀 Connected agents**

Connected agents are full-fledged, independent agents that your main agent can collaborate with. Think of them as separate departments working together on a project.

Key technical details:

- Connected agents have their own topics and conversation flows. They operate independently with their own settings, logic, and deployment lifecycle.
- Connected agents must be published before they can be added to and used by other agents.
- During testing, changes to the connected agent must be published before they can be used by the calling agent.

Use connected agents when:

- Multiple teams develop and maintain different agents independently
- Agents need their own settings, authentication, and deployment channels
- You want to publish and maintain agents separately with independent application lifecycle management (ALM) for each agent
- Agents should be reusable across multiple solutions

Example: A customer service system that connects to:

- A separate billing agent maintained by the finance team
- A separate technical support agent maintained by the product team
- A separate returns agent maintained by the operations team

TIP: You can mix both approaches! For example, your main agent could connect to external agents from other teams while also having its own child agents for specialized internal tasks.

#### 🎯 Multi-agent architecture patterns

When designing multi-agent systems, several patterns emerge based on how agents interact:

| Pattern | Description | Best For |
|---------|-------------|----------|
| Hub and Spoke | A main orchestrator agent coordinates with multiple specialized agents. The orchestrator handles user interaction and delegates tasks to child or connected agents. | Complex workflows where one agent coordinates specialized tasks |
| Pipeline | Agents pass work sequentially from one to the next, each adding value before passing to the next stage. | Linear processes like application processing (intake -> screening -> interview -> decision) |
| Collaborative | Agents work together simultaneously on different aspects of the same problem, sharing context and results. | Complex analysis requiring multiple perspectives or expertise areas |

TIP: You may even have a hybrid of two or more of these patterns.

#### 💬 Agent communication and context sharing

When agents work together, they need to share information effectively. Here's how this works in Copilot Studio:

**Conversation history**

By default, when a main agent calls a child or connected agent, it can pass along the conversation history. This gives the specialist agent full context about what the user has been discussing.

You can disable this for security or performance reasons - for example, if the specialist agent only needs to complete a specific task without needing the full conversation context. This can be a good defense against data leakage.

**Explicit instructions**

Your main agent can give specific instructions to child or connected agents. For example: "Process this resume and summarize their skills for the Senior Developer role."

**Return values**

Agents can return structured information back to the calling agent, allowing the main agent to use that information in subsequent steps or share it with other agents.

**Dataverse integration**

For more complex scenarios, agents can share information through Dataverse or other data stores, allowing for persistent context sharing across multiple interactions.

#### ↘️ Child agent: Application Intake Agent

Let's start building our multi-agent hiring system. Our first specialist will be the Application Intake Agent - a child agent responsible for processing incoming resumes and candidate information.

**🤝Application Intake Agent responsibilities**

- Parse resume content from PDFs provided via interactive chat (In a future mission you'll learn how to process resumes autonomously).
- Extract structured data (name, skills, experience, education)
- Match candidates to open roles based on qualifications and cover letter
- Store candidate information in Dataverse for later processing
- Deduplicate applications to avoid creating the same candidate twice, match to existing records using the email address extracted from the resume.

**⭐ Why this should be a child agent**

The Application Intake Agent fits perfectly as a child agent because:

- It's specialized for document processing and data extraction
- It doesn't need separate publishing
- It's part of our overall hiring solution managed by the same team
- It focuses on a specific trigger (new resume received) and is invoked from the Hiring Agent.

#### 🔀 Connected agent: Interview Prep Agent

Our second specialist will be the Interview Prep Agent - a connected agent that helps create comprehensive interview materials and evaluates candidate responses.

**🤝 Interview Prep Agent responsibilities**

- Create interview packs with company information, role requirements, and evaluation criteria
- Generate interview questions tailored to specific roles and candidate backgrounds
- Answer general questions about the job roles and applications for stakeholder communication

**⭐ Why this should be a connected agent**

The Interview Prep Agent works better as a connected agent because:

- The talent acquisition team might want to use it independently across multiple hiring processes
- It needs its own knowledge base of interview best practices and evaluation criteria
- Different hiring managers might want to customize its behavior for their teams
- It could be reused for internal positions, not just external hiring

#### 🧪 Lab 3.1: Adding the Application Intake Agent

Ready to put theory into practice? Let's add our first child agent to your existing Hiring Agent.

**Prerequisites to complete this mission**

To complete this mission you need to:

- Have completed Mission 01 and have your Hiring Agent ready

**3.1.1 Solution setup**

1. Inside Copilot Studio, select the ellipsis (...) below Tools in the left hand navigation.
2. Select Solutions.
3. Locate your Operative solution, select the ellipsis (...) next to it, and choose Set preferred solution. Select Apply in the dialogue box that pops up. This will ensure that all your work will be added to this solution.

**3.1.2 Configure your Hiring Agent agent instructions**

1. Navigate to Copilot Studio. Ensure your environment is selected in the top right Environment Picker.
2. Open your Hiring Agent from Mission 01
3. Select Edit in the Instructions section of the Overview tab of the agent.
4. Copy and paste the following instructions in the instructions input:

"You are the central orchestrator for the hiring process. You coordinate activities, provide summaries, and delegate work to specialized agents."

5. Select Save
6. Select the Settings button in the top right of the screen
7. Review the page and ensure the following settings are applied:

| Setting | Value |
|---------|-------|
| Use generative AI orchestration for your agent's responses | Yes |
| Deep Reasoning | Off |
| Let other agents connect to and use this one | On |
| Continue using retired models | Off |
| Content Moderation | Moderate |
| Collect user reactions to agent messages | On |
| Use general knowledge | Off |
| Use information from the Web | Off |
| File uploads | On |
| Code Interpreter | Off |

8. Click Save
9. Click the X in the upper right hand corner to close out of the settings menu

**3.1.3 Add the Application Intake child agent**

1. Navigate to the Agents tab within your Hiring Agent (this is where you'll add specialist agents) and select Add.
2. Select New child agent.
3. Name your agent Application Intake Agent
4. Select The agent chooses - Based on description in the When will this be used? dropdown. These options are similar to the triggers that can be configured for topics.
5. Set the Description to be: "Processes incoming resumes and stores candidates in the system"
6. Expand Advanced, and set the Priority to be 10000. This will ensure that later the Interview Agent will be used to answer general questions before this one. A condition could be set here as well such as ensuring that there is at least one attachment.
7. Ensure that the toggle Web Search is set to Disabled. This is because we only want to use information provided by the parent agent.
8. Select Save

**3.1.4 Configure Resume Upload agent flow**

Agents can't perform any actions without being given tools or topics.

We're using Agent Flow tools rather than Topics for the Upload Resume step because this multi-step backend process requires deterministic execution and integration with external systems. While Topics are best for guiding the conversational dialog, Agent Flows provide the structured automation needed to reliably handle file processing, data validation, and database upserts (insert new or update existing) without depending on user interaction.

1. Locate the Tools section inside the Application Intake Agent page. Important: This isn't the Tools tab of the parent agent, but can be found if you scroll down underneath the child agent instructions.
2. Select + Add
3. Select + New tool
4. Select Agent flow. The Agent Flow designer will open, this is where we will add the upload resume logic.
5. Select the When an agent calls the flow node, and select + Add an input
6. Add inputs for each of the following Parameters listed in the table below. Select the appropriate input type as shown in the table and be sure to add both the name and the description. It's important to include the description because it will help the agent know what to fill in the input.

| Type | Name | Description |
|------|------|-------------|
| File | Resume | The Resume PDF file |
| Text | Message | Extract a cover letter style message from the context. The message must be less than 2000 characters. |
| Text | UserEmail | The email address that the Resume originated from. This will be the user uploading the resume in chat, or the from email address if received by email. |

7. Select the + icon below the when an agent calls the flow node and search for Dataverse add, then select the Add a new row action in the Microsoft Dataverse section

NOTE: You may be prompted to create a new connection to Dataverse after you add the action. Enter any name for the connection and click add to create that connection.

8. Name the node Create Resume, by selecting the Add a new row node, and replacing the tile as shown
9. Set the Table name to Resumes, then select Show all, to show all the parameters.
10. Set the following properties:

| Property | How to Set | Details / Expression |
|----------|------------|---------------------|
| Resume Title | Dynamic data (thunderbolt icon) | When an agent calls the flow → Resume name |
| Cover letter | Expression (fx icon) | if(greater(length(triggerBody()?['text']), 2000), substring(triggerBody()?['text'], 0, 2000), triggerBody()?['text']) |
| Source Email Address | Dynamic data (thunderbolt icon) | When an agent calls the flow → UserEmail |
| Upload Date | Expression (fx icon) | utcNow() |

11. Select the + icon below the Create Resume node, search for Dataverse upload and select the Upload a file or an image action.

Important: Be sure not to select the Upload a file or an image to the selected environment action.

12. Name the node to Upload Resume File
13. Set the following properties:

| Property | How to Set | Details |
|----------|------------|---------|
| Content name | Dynamic data (thunderbolt icon) | When an agent calls the flow → Resume name |
| Table name | Select | Resumes |
| Row ID | Dynamic data (thunderbolt icon) | Create Resume → See more → Resume |
| Column Name | Select | Resume PDF |
| Content | Dynamic data (thunderbolt icon) | When an agent calls the flow → Resume contentBytes |

14. Select the Respond to the agent node, and then select + Add an output. Create an output with the properties defined in the table below:

| Property | How to Set | Details |
|----------|------------|---------|
| Type | Select | Text |
| Name | Enter | ResumeNumber |
| Value | Dynamic data (thunderbolt icon) | Create Resume → See More → Resume Number |
| Description | Enter | The [ResumeNumber] of the Resume created |

15. Select Save draft on the top right
16. Select the Overview tab, Select Edit on the Details panel. Fill in the name and description as shown below and select Save

Flow name: Resume Upload
Description: Uploads a Resume when instructed

17. Select the Designer tab again, and select Publish.

**3.1.5 Connect the flow to your agent**

Now you'll connect the published flow to your Application Intake Agent.

1. Navigate back to the Hiring Agent and select the Agents tab. Open the Application Intake Agent, and then locate the Tools panel.
2. Select + Add
3. Select the Flow filter, and search for Resume Upload. Select the Resume Upload flow.
4. Select Add and configure.
5. Set the following parameters for the description and when the tool should be used:

| Parameter | Value |
|-----------|-------|
| Description | Uploads a Resume when instructed. STRICT RULE: Only call this tool when referenced in the form "Resume Upload" and there are Attachments |
| Additional details → When this tool may be used | only when referenced by topics or agents |

NOTE: This description tells the agent when it should call this tool. Notice the use of "strict rule" in the description. This gives a way to provide additional guardrails on when the tool should be used, in this case, only if there are attachments and the context of the conversation is a resume upload. Choosing when this tool can be used is important as well. Since we are building a multi-agent system and we have a child agent, we want to be sure this tool is ONLY called in the child agent, not the main agent. Setting the value to "only when referenced by topics or agents" ensures this.

6. Scroll down to the inputs section and select Add Input to add the following inputs:

| Parameter | Value |
|-----------|-------|
| Inputs → Add Input | contentBytes |
| Inputs → Add Input | name |

7. Now we need to set the properties of the inputs. We'll start with the contentBytes input which will store the actual resume file. Select Custom value from the Fill using dropdown next to the contentBytes input.

8. In the Value property, select the three dots (...) and select the Formula tab. Paste in the following formula which extracts the file from the chat and click the Insert button.

First(System.Activity.Attachments).Content

9. Now we'll configure the name input which will store the name of the resume file. This will be hard coded as well so select the Custom value option in the Fill using column.

10. Select the three dots (...) in the Value column and paste in the following formula which extracts the file name from the chat and click the Insert button.

First(System.Activity.Attachments).Name

11. Now we'll configure the Message input. We want to fill this one dynamically with AI so we'll leave the fill using as-is. Select the Customize button in the Value column so we can fill out additional details for how this should be filled.

12. Enter the following in the Description field for the input:

"Extract a cover letter style message from the context. Be sure to never prompt the user and create at least a minimal cover letter from the available context. STRICT RULE - the message must be less than 2000 characters."

---

*Source: Microsoft Agent Academy - Operative Curriculum, Mission 03*
