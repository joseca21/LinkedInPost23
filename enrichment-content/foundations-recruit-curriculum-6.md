# Foundations: Create a Custom Agent Using Natural Language

---

## SECTION 1: SUMMARY

This section provides a condensed overview of the Custom Agent creation mission for quick reference.

### Mission Overview

**Codename:** Operation Agent Forge
**Duration:** ~75 minutes
**Level:** Recruit

### Key Objectives

- Understand what custom agents are and how they differ from pre-built templates
- Create agents using natural language prompts with Copilot
- Ground agents with enterprise knowledge sources (SharePoint, documents, websites)
- Learn about generative orchestration and dynamic data sourcing
- Build and test a fully functional IT helpdesk agent

### What is a Custom Agent?

A custom agent is a chatbot or virtual assistant you create in Copilot Studio for specific tasks:

- **You decide the purpose** - vacation requests, order status, IT help
- **You define the conversation** - what agent says and how it responds
- **You ground it with your data** - connect to enterprise data sources
- **You connect it to systems** - connectors, flows, REST APIs, MCP servers

### What Can a Custom Agent Do?

- Ask users for information (names, dates, preferences)
- Save information to databases or tables
- Look up data and answer questions
- Work autonomously without direct user interaction
- Trigger actions (sending emails, creating records)

### Why Use Custom Agents?

| Benefit | Description |
|---------|-------------|
| **Saves time** | Automates repetitive tasks |
| **Better UX** | Friendly, guided experience for users |
| **Tailored** | Fits your specific business needs |

### Writing Good Prompts

**Tips:**
- Be clear and specific - say exactly what you want
- Think like the user - what will they say? What should agent reply?
- Include examples - give sample interactions

**Good Prompt Example:**
```
I want to build an agent that helps users submit a vacation request.
When a user says they want time off, the agent should ask for their name,
start date, end date, and manager's name. Once provided, save it to a
SharePoint list called 'Vacation Requests' and post to a Teams channel.
```

### Generative Orchestration

How agents dynamically answer questions:
1. **Understands** the question using AI
2. **Asks** users for missing information
3. **Selects** most relevant knowledge sources
4. **Searches** those sources for answers
5. **Generates** natural, helpful response

### Knowledge Source Types

| Source | Description | Use Case |
|--------|-------------|----------|
| **Public websites** | Searches via Bing | FAQs, product details |
| **Documents** | Uploaded PDFs, Word files (stored in Dataverse) | Internal guides, manuals, policies |
| **SharePoint** | Folders/files via Microsoft Graph Search | Team docs, HR policies, project files |
| **Dataverse** | Structured data from tables/rows | Customer info, enterprise data |
| **Real-time connectors** | Live data from Salesforce, ServiceNow, Dynamics 365, etc. | Up-to-date responses without data duplication |
| **Azure AI Search** | Semantic/vector search over large document sets | Complex data, citations, large collections |

### Improving Agent Responses

1. **Refine instructions** - Use clear, specific language
2. **Check tone** - Match audience (friendly, professional, supportive)
3. **Update knowledge sources** - Add links, documents, keep content current
4. **Use Topics and Triggers** - Handle specific tasks precisely
5. **Test with real questions** - Adjust based on results
6. **Review and iterate** - Collect feedback, watch for confusion

### Lab Summary

**6.1 Create Agent with Copilot:**
- Enter detailed prompt describing IT helpdesk agent
- Name agent "Contoso Helpdesk Agent"
- Refine instructions (prioritise urgent, acknowledge issues, bullet points)
- Add public website knowledge (support.microsoft.com)
- Add guardrail: don't answer HR questions
- Test with Activity Map to see knowledge source usage
- Create in preferred solution

**Key Prompt Elements:**
- Goal of the agent
- Context and expected tasks
- Format of responses
- Examples of topics to handle
- What NOT to answer

---

## SECTION 2: VERBATIM CONTENT

This section contains the original source material in its complete form.

---

### Recruit Curriculum Modules

Course Setup

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

### 🚨 Mission 06: Create a custom agent using natural language with Copilot and grounding it with your data

🕵️‍♂️ CODENAME: OPERATION AGENT FORGE

⏱️ Operation Time Window: ~75 minutes

#### 🎥 Watch the Walkthrough

Create custom agent video thumbnail

#### 🎯 Mission Brief

Welcome back, Agent Maker. This mission puts you in the command seat of the most powerful capability in Copilot Studio - creating a custom agent from scratch using only natural language… and supercharging it with your own data.

This isn't just another chatbot. You're building a knowledge empowered digital coworker - one that can reason, respond, and reference real enterprise info.

Your weapon of choice? Natural language. Your mission? Design, train, and test a fully customized helpdesk agent that answers IT questions using SharePoint, uploaded files, or company URLs.

Let's build your agent from the ground up.

#### 🔎 Objectives

In this mission, you'll learn:

- Understanding what custom agents are and how they differ from pre-built templates
- Creating agents using natural language prompts and conversational design with Copilot
- Grounding agents with enterprise knowledge sources including SharePoint, documents, and websites
- Learning about generative orchestration and how agents dynamically search and respond using multiple data sources
- Building and testing a fully functional IT helpdesk agent that can answer questions from your own data

#### 🤔 What is a custom agent?

A custom agent is a chatbot or virtual assistant that you create and design in Copilot Studio to help users with specific tasks or questions. It's called custom because:

- You decide the purpose - help users request vacation time, check order status, provide assistance with IT related questions.
- You define the conversation - what the agent says and how it should respond.
- You ground it with your own data - connect to your enterprise data through the built-in supported knowledge resources.
- You connect it to your own systems or applications - choose from connectors, flows, REST APIs and model context protocol servers.

NOTE: Think of it this way: you are building your own digital helper that can talk to users and complete tasks for them such as answering questions, collecting information required by a process, or connecting to your enterprise data.

#### 🤖 What can a custom agent do?

A custom agent can fulfill the following:

- Ask users for information such as names, dates, or preferences.
- Save that information to a database or table.
- Look up data based on the questions asked and answer them.
- Work autonomously without users directly interacting with the agent.
- Trigger actions either on-demand through direct user interaction or autonomously such as sending emails or creating records.

#### 👩🏻‍💻 Why use a custom agent?

- Saves time by automating repetitive tasks.
- Gives users a friendly, guided experience.
- Tailor it to your business or project needs.

**✨ Example**

You build a custom agent that helps employees request vacation leave.

It asks for their name, vacation dates, and their manager's name, then saves the information into the designated system that managed vacation requests, such as a SharePoint list.

Now, instead of navigating to the SharePoint list and creating a new item, employees simply chat with the agent instead.

#### 🗣️ Use natural language to create agents

Previously you learnt how to quickly build agents in Copilot Studio using prebuilt agent templates in Lesson 05 - Get started quickly with pre-built agents. In this lesson, we'll dive into the conversational creation experience with Copilot. Copilot Studio makes it easy to build agents by chatting with Copilot, just like having a conversation.

In Copilot Studio, you don't need to write code to create an agent. Instead, you describe what you want your agent to do in plain language, and Copilot helps you build it step by step through a chat-like experience.

#### 🌱 But I'm new to "describing what I want" - what do I do?

Describing in natural language to create a custom agent might be a new concept for you. Whenever you use Copilot across Microsoft products and services, you are using natural language in the form of a prompt.

A prompt is the message or instruction you give to an AI agent to tell it what you want it to do. Think of it as giving directions to an assistant. The clearer your instructions are, the easier it is for your assistant to understand and act on them.

**🪄 Why Prompts matter**

- They guide the agent's behavior.
- They help the agent understand what kind of conversation to have.
- A good prompt makes the agent more helpful and accurate.

**📝 Tips for writing a good prompt**

- Be clear and specific - say exactly what you want the agent to do.
- Think like the user - what will the user say? What should the agent reply?
- Include examples - if possible, give a sample interaction.

**✨ Example**

Let's say the HR team needs an agent to help with vacation requests.

The prompt could be:

"I want to build an agent that helps users submit a vacation request. When a user says they want to request time off, the agent should ask for their name, the start date of their vacation, the end date of their vacation, and their manager's name. Once the user provides this information, the agent should save it to a SharePoint list called 'Vacation Requests' and post a notification in a dedicated Microsoft Teams channel."

Why this prompt works:

- Clearly states the goal - submit a vacation request
- Describes the user interaction - what the user says and what the agent should ask
- Lists the required data - name, start date, end date, manager
- Mentions where the data goes - a SharePoint list called Vacation Requests

#### 🔮 OK, I've created my agent... how do I next ground it with knowledge?

In Copilot Studio, knowledge sources are places where your agent can find information to give better answers. When you add these sources, your agent can pull in your enterprise data from places like Power Platform, Dynamics 365, websites, and other systems or services your company uses.

These sources work together with AI to help your agent respond more accurately to user questions, this is achieved through what is known as generative orchestration.

#### 🌿 What is generative orchestration in the context of agents?

Generative orchestration means the agent uses AI to dynamically decide how to answer a question by combining its built-in language skills with information from your added knowledge sources.

When a user asks a question, the agent:

1. Understands the question using AI.
2. Can ask users for missing information by generating questions on the fly.
3. Selects the most relevant knowledge sources.
4. Searches those sources for answers.
5. Generates a natural, helpful response using the information it found.

#### 🏦 Why knowledge sources matter?

**Smarter answers** - when you add knowledge sources, your agent can give better, more accurate answers using real data from your organization.

**Less manual work** - you don't have to write every possible response. The agent can search through your added sources and respond automatically.

**Use trusted information** - your agent can pull answers from systems you already use such as Dataverse, SharePoint, or company websites so that users have reliable information from a source of truth.

**Works with generative AI** - knowledge sources and AI help your agent understand questions and respond naturally, even if the question wasn't pre-programmed or added as a starter prompt.

**Flexible and expandable** - you can add knowledge sources anytime during set up or at later point in time, your agent grows smarter as your needs change.

**✨ Example**

Imagine you build an agent to help employees with HR questions. You add your company's HR policy document and SharePoint site as knowledge sources.

When an employee asks, "How many vacation days am I entitled to?", the agent uses generative orchestration to search those sources and reply with the correct policy without you having to write that answer manually. This saves you time in having to account for every possible question an employee may ask regarding their entitlements.

#### Types of knowledge sources that can be added

**Public websites**

- What it does: Searches specific websites (like your company's site) using Bing.
- Why it's useful: Great for pulling in public-facing info like FAQs or product details.

**Documents**

- What it does: Uses documents that you upload directly to your agent, such as PDFs or Word files. These uploaded files are stored securely in Dataverse.
- Why it's useful: Enables your agent to answer questions based on internal guides, manuals or policies.

**SharePoint**

- What it does: Connects to SharePoint folders or files using Microsoft Graph Search.
- Why it's useful: Ideal for accessing team documents, HR policies, or project files stored in SharePoint.

**Dataverse**

- What it does: Uses structured data from your Dataverse environment tables and rows, and can apply synonyms and glossary definitions for tables and columns for improving agent responses.
- Why it's useful: When you need to look up enterprise data stored in Dataverse such as customer information.

**Real-time knowledge with connectors**

- What it does: Lets your agent access live data from other enterprise systems such as Salesforce, ServiceNow, Dynamics 365, AzureSQL, Databricks, and more during a conversation, using the user's own permissions.
- Why it's useful: It provides up to date, secure, and accurate responses without storing or duplicating data, making your agent smarter and safer.

**Azure AI Search**

- What it does: Allows your agent to search through large sets of documents stored in Azure using semantic and vector search to understand user questions.
- Why it's useful: Delivers accurate, trustworthy answers from complex data sources, supports citations, and scales well for large document collections with secure access controls.

#### 🔒 Note on security

**Knowledge source authentication**

Some sources such as SharePoint and Dataverse require user authentication. This means the agent will only reference data in its response that the user is allowed to see. Whereas other sources may have additional configuration required for the agent to connect to it such as Azure AI Search which requires an Azure account and specifying an authentication type.

#### Improving your agent's responses in Copilot Studio

After your agent is provisioned from the conversational creation experience, you'll want to test your agent against the instructions Copilot generated from your prompt. Improving your agent's responses in Copilot Studio is all about making sure it understands your goals clearly and has the right information to work with.

**Refine the agent instructions** - this is where you tell your agent how it should behave. Use clear, specific language.

For example:

✅ "Act like a friendly customer support agent who explains things simply."

❌ "Be helpful." (Too vague)

**Check the tone and language** - make sure the agent's tone matches your audience.

You can set it to be:

- Friendly and casual.
- Professional and concise.
- Supportive and patient.

**Add or update knowledge sources** - if your agent needs to answer questions about a topic, make sure it has access to the right information.

- Add links to websites, documents, or FAQs.
- Keep the content up to date.
- Use clear, well-structured information.

**Use Topics and Triggers** - If your agent needs to handle specific tasks or conversations, you can create topics with trigger phrases. This helps guide the conversation more precisely. We'll learn more about this in the following lesson.

**Test with real questions** - try asking your agent the kinds of questions users might ask.

If the answers aren't great:

- Adjust the system instructions.
- Add more examples or knowledge.
- Rephrase your questions to see how it responds.

**Review and iterate** - improving an agent is an ongoing process!

After publishing:

- Collect feedback from users.
- Watch for common questions or confusion.
- Keep refining the agent's setup.

#### 🧪 Lab 06: Create a custom agent in Copilot Studio

We're now going to learn how to create a custom agent that can chat over your data

**✨ Use case**

We'll use the same use case from Lesson 03 - Create a declarative agent for Microsoft 365 Copilot

As an employee

I want to get quick and accurate help from the IT helpdesk agent for issues like device problems, network troubleshooting, printer setup

So that I can stay productive and resolve technical issues without delays

Let's begin!

**✨ Prerequisites**

**SharePoint site**

We'll be using the Contoso IT SharePoint site from Lesson 00 - Course Setup - Step 3: Create new SharePoint site.

If you have not set up the Contoso IT SharePoint site, please head back to Lesson 00 - Course Setup - Step 3: Create new SharePoint site.

**Solution**

We'll be using the Contoso Helpdesk Agent solution from Lesson 04 - Creating a Solution for your agent.

If you have not set up the Contoso Agent solution, please head back to Lesson 04 - Creating a Solution for your agent.

#### 6.1 Use natural language to create an agent with Copilot

**Copilot questions may differ across sessions**

The Copilot conversational creation experience can vary each time where the provided questions for guidance may be slightly different than previously.

1. Navigate to the Home page of Copilot Studio and in the field, enter the following prompt which describes the IT help desk agent. The prompt includes the goal of the agent, the context, the expected tasks and format of the agent's response.

```
You are an IT help desk agent. Your goal is to assist users with their IT issues. You can access information from our company's knowledge base at https://support.microsoft.com/en-us. Your responses should be polite and helpful. If a user reports a slow computer, ask about the age of the device, current software versions, and if they've recently installed any new programs. If a user is experiencing trouble logging into their email, guide them through password reset procedures. You should be concise and informative, using step-by-step instructions with bullet points when appropriate.
```

2. The conversational creation experience with Copilot will next load. You'll see Copilot is in progress of responding to you.

3. Copilot confirms the agent has been set up with the instructions provided, and is asking for confirmation on the name of the agent. We'll ask Copilot to name our agent as:

```
Contoso Helpdesk Agent
```

4. Copilot performs the request and we'll see that the name of the agent has been updated in the agent pane. Copilot next asks us to refine the instructions. It's asking how we should respond to particular issues and we'll request that it acknowledges the issue, provide examples of topics to answer, and format the response as bullet points.

Copy and paste the following, and submit the request to Copilot:

```
Prioritize urgent requests. Examples of IT issues or scenarios to help with: device problems, network connectivity, log in issues. When troubleshooting, first acknowledge their issue and respond with empathy, then provide step by step guidance using bullet points and ask if they require further assistance.
```

5. The instructions of the agent will be updated after Copilot has received the request. Notice how on the right hand side pane, that starter prompts have now appeared. These were formed based on our instructions.

6. Next, Copilot is asking for public websites to ground the agent's knowledge.

Copy and paste the following, and submit the request to Copilot:

```
https://support.microsoft.com
```

7. The public website will be added as a knowledge source. Copilot is asking if additional knowledge sources are to be added. We don't need to add additional public websites.

Copy and paste the following, and submit the request to Copilot:

```
Proceed with setup
```

8. Copilot confirms the setup of our Contoso Helpdesk Agent is complete but we'll add one more modification, we're going to request that our agent does not answer HR related questions. This lets our agent know that it should not answer HR related questions asked by users.

Copy and paste the following, and submit the request to Copilot:

```
Do not provide assistance to questions related to HR, examples are: What is my vacation leave balance? How many sick days do I have? What's the URL to our payroll portal?
```

9. The instructions will be updated to not provide assistance with questions related to HR. We don't need to make further updates, our agent is ready to be created.

10. Before we create our agent, let's do a couple of things.

First, select the Configure tab to view the agent details defined from our conversation with Copilot. This is where you'll see the Name, Description, Instructions, Knowledge and Suggested/Starter prompts.

11. Secondly, let's test our agent. Copy and paste the following, and submit the question to our agent:

```
How can I check the warranty status of my Surface?
```

12. The response to the question will then display where the answers are in the format of a step-by-step guide using bullet points. Great, our agent works! 🙌🏻

13. Lastly, we'll double check the solution that our agent will be created in, is the solution we created and selected as the preferred solution in Lesson 04 - Create a new solution.

Select the ellipsis icon (...) and select Update Advanced Settings.

14. The Advanced Settings modal will appear and we can see our solution created from earlier is selected by default. This is due to selecting our solution as the preferred solution in Lesson 04 - Create a new solution.

Select Cancel.

15. Let's now create our custom agent! Select Create.

16. Copilot Studio will begin provisioning our agent.

17. Once our agent has been provisioned, we can see the details of the agent reflect what we requested during our Copilot conversational creation experience. Scroll down to review the agent where you'll see the name, description, instructions, the knowledge sources and the suggested prompts. The orchestration mode is enabled by default and the default model is used for the response model of the agent.

18. Let's now test our newly created agent. In the Test pane on the right hand side, select the Activity Map icon.

19. Enter the following question in the Test pane:

```
How do I find my Windows 11 product key?
```

20. The Activity map will then load which shows us in real-time what path the agent is processing. In this scenario, our agent has understood the question and searches the knowledge sources. Currently we have one source which is the public website we added earlier using Copilot, which is what the agent is reviewing.

21. Our agent then responds with answers that are outlined as bullet points, as defined in the instructions. The response has references to the web pages that the agent formed its response from. This enables users to verify the source of the answer.

22. You can also review the response and its sources by scrolling down the Knowledge modal in the Activity map.

Congratulations! You've built your first custom agent with Copilot in Copilot Studio 🙌🏻

---

*Source: Microsoft Agent Academy - Recruit Curriculum, Mission 06: Create a Custom Agent Using Natural Language*
