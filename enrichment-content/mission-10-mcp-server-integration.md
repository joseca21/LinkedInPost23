# Mission 10: Integrate with MCP Servers

## Summary

**Mission Overview:**
Mission 10 (Operation MCP Rendezvous) teaches how to integrate external MCP (Model Context Protocol) servers with Copilot Studio agents to extend their capabilities beyond built-in features. The mission duration is approximately 45 minutes and builds upon Mission 09. Transforms agents from isolated systems to connected platforms that can interact with Microsoft 365 and external services through standardized protocols.

**Core Objectives:**
- Understanding and working with the Model Context Protocol (MCP) standard
- Using Agent 365 to integrate MCP servers with Copilot Studio agents
- Connecting Copilot Studio agents to MCP servers
- Leveraging MCP server capabilities within agents for real-world actions

**What is MCP (Model Context Protocol)?**

MCP is an open standard that enables AI assistants to securely connect to external data sources and tools.

**The USB-C Analogy:**
Think of MCP as the USB-C of AI integration:
- **Before USB-C:** Every device had its own proprietary connector (different charger cables)
- **Before MCP:** Connecting AI agents to external systems required custom integrations for each service
- **MCP Solution:** Provides a universal "plug-and-play" protocol - one standard works across different AI platforms and data sources

**Four Key Benefits of MCP:**

1. **Universal connectivity:** One standard protocol works across different AI platforms and data sources
2. **Secure access:** Built-in authentication and permission controls protect your data
3. **Extensibility:** Easily add new capabilities to agents without rewriting core logic
4. **Interoperability:** MCP servers can work with multiple AI assistants and applications

**What is Agent 365?**

Microsoft's comprehensive platform for managing and extending AI agents at enterprise scale.

Core capabilities:
- Gives each AI agent its own **Microsoft Entra Agent ID** for identity, lifecycle, and access management
- Provides infrastructure to safely connect agents to business systems through MCP servers
- **Think of Agent 365 as:** Enterprise control plane for AI agents - handles security, governance, and observability while enabling agents to interact with Microsoft 365 and business applications through standardized MCP tooling servers

**How Agent 365 Serves Different Roles:**

| Role | What Agent 365 Provides |
|------|-------------------------|
| IT Administrators | Monitor agent activity, enforce policies, manage threats through Microsoft 365 admin center |
| Security Teams | Apply enterprise-grade controls for identity, authentication, and compliance with Microsoft Purview and Defender integration |
| Developers | Build and extend agents using unified SDKs, pre-built MCP servers, and frameworks in Copilot Studio or Azure AI Foundry |
| Business Decision Makers | Deploy agents securely and measure impact on productivity and business outcomes |
| Information Workers | Collaborate with agents seamlessly to amplify productivity |

**Agent 365 Tooling Servers for MCP Integration:**

**Pre-built MCP Servers for Microsoft 365 and Business Applications:**

| MCP Server | Capabilities |
|------------|--------------|
| Outlook Calendar | Create, update, and manage calendar events |
| Outlook Mail | Send, read, and search emails |
| Teams | Create chats, post messages, and manage channels |
| SharePoint & OneDrive | Upload files, manage lists, and search documents |
| Word | Create and edit documents, add comments |
| Dataverse & Dynamics 365 | Perform CRUD operations on business data |
| User Profile | Access user information, managers, and direct reports |
| Copilot Search | Chat with Microsoft 365 Copilot and ground responses with files |

**Enterprise Security and Governance:**

1. **Centralized control:** Manage all MCP servers through Microsoft 365 admin center - allow or block servers organization-wide
2. **Scoped permissions:** Agents only access resources they need based on Microsoft Entra scopes
3. **Full observability:** Monitor and audit all tool calls using Microsoft Defender Advanced Hunting
4. **Policy enforcement:** Apply DLP, MIP, rate limits, and security scans at runtime
5. **Threat protection:** Detect and remediate attacks targeting agents with Microsoft Defender integration

**Custom MCP Server Creation:**

- **MCP Management Server:** API-first tool for creating custom MCP servers
- **Power Platform connectors:** Connect to 1,500+ connectors (ServiceNow, JIRA, etc.)
- **API integration:** Microsoft Graph APIs, REST APIs, and Dataverse custom APIs
- **Publishing:** Publish and certify custom servers for your organization
- **ISV enablement:** Enable ISVs to build and publish certified servers

**Developer Experience:**

- Available in both **Copilot Studio (low-code)** and **Azure AI Foundry (pro-code)**
- Built into Agent 365 SDK for seamless integration
- Visual Studio Code integration for creating and testing custom MCP servers
- Consistent, standardized interfaces across all tooling servers

**Why This Matters for Your Agents:**

Agent 365 transforms MCP from open standard into enterprise-ready platform. Agents get:

1. **Deterministic, auditable actions:** Every tool call tracked and governed
2. **Production-grade reliability:** All MCP servers undergo rigorous testing for accuracy, latency, and reliability
3. **Security by default:** Enterprise controls built-in, not bolted on
4. **Rapid development:** Pre-built servers for common scenarios, easy customization for specialized needs
5. **Unified management:** One control plane for all agents, regardless of where they're built

**Mission Focus:**

While Agent 365 offers comprehensive platform for agent management, governance, and custom MCP server development, this mission focuses specifically on **using pre-built MCP servers in Copilot Studio**.

Learn to:
- Connect agent to ready-made tooling servers (Outlook Calendar, Teams)
- Enable real actions in Microsoft 365 applications
- WITHOUT building custom integrations

*Think of this as:* Learning to use the tools already in the toolbox before building your own.

**Lab Exercise: Add MCP Servers to Arrange Interview Prep-Meeting**

**CRITICAL PREREQUISITE: Frontier Preview Program**
Must be part of Frontier preview program to get early access to Microsoft Agent 365. Frontier connects directly with Microsoft's latest AI innovations. Subject to existing preview terms of customer agreements. Features still in development - availability and capabilities may change.

**Lab Prerequisites (Tenant Configuration Required):**

1. **Manager configured:** Have manager configured for your user in M365 Admin Center
2. **Calendar appointment:** Have appointment on calendar in upcoming 24 hours (for testing "Get my meetings for today")
3. **Extra user:** Have extra user created on tenant to invite for interview prep-meeting
4. **Mailbox provisioned:** For extra user, mailbox needs to be provisioned
5. **Working hours:** Good to set working days/hours for extra user

**Key Distinction: MCP Servers vs Connector Tools**

*MCP Servers:* Add one tool per MCP server - single tool handles multiple actions
*Connector Tools:* Require adding a tool for every connector action

This ability to add single tool handling multiple actions makes MCP Servers much easier to work with.

**Lab 10.1 - Add Microsoft 365 User Profile MCP Server:**

*Configuration Steps:*
1. Open Interview Agent in Copilot Studio
2. Select Tools in top navigation
3. Select "Add a tool"
4. Filter by "Model Context Protocol"
5. Select "Microsoft 365 User Profile MCP server"
6. Create new connection (select your account in popup)
7. Select "Add and configure"
8. Review MCP tools that are part of MCP server (scroll down on tool overview page)

*Testing Process:*
1. Select Test
2. Send prompt: "Who is my manager?"
3. **Consent card appears** - Select "Allow" to consent MCP server using your data
   - Consent card shows ONCE per agent and MCP server combination
   - After allowing for this agent, won't prompt again (unless adding another MCP server using same connector)
4. Verify response shows manager information
5. Check test pane left side: Agent initialized MCP server, triggered getMyManager MCP tool
6. Review details of what agent sent/received from MCP tool

*Example Queries Enabled:*
- "Who is my manager?"
- "Who are my direct reports?"
- "What is the job role of Daniel Laskewitz?"
- And much more...

**Lab 10.2 - Add Microsoft Outlook Calendar MCP Server:**

*Why This MCP Server Needed:*
User Profile MCP server enables working with user details, very helpful for planning meetings. Users don't send prompts with email/UPN when planning meetings. Instead: "meeting with Daniel Laskewitz tomorrow"

To handle natural language meeting requests, need Microsoft Outlook Calendar MCP server.

*Configuration Steps (Similar to Previous):*
1. Select Tools at top navigation
2. Select "Add a tool"
3. Filter by "Model Context Protocol"
4. Select "Microsoft Outlook Calendar MCP Server"
5. Select "Add and configure"
6. Scroll to bottom to see tools in Microsoft Outlook Calendar MCP server

*Testing Process:*
1. Enter prompt: "Get my meetings for today"
2. **Consent card appears again** (new MCP server) - Select "Allow"
3. Verify response shows meetings on calendar for today
4. Check test pane for MCP tool calls

**Lab 10.3 - Plan Interview Prep-Meeting:**

*Complete Workflow Test:*

1. **Start new test session** (to reset context)

2. **Find meeting times:**
   - Prompt: "Can you find 3 meeting times for a 30 minute meeting with Jane Doe for an interview prep-meeting?"
   - Triggers: findMeetingTimes MCP tool
   - Behavior: Looks at calendars of both user and Jane Doe, figures out times based on availability
   - Response: Three meeting time options
   - Debug pane: Shows tools called

3. **Schedule actual meeting:**
   - Prompt: "Please schedule the one on 10:30 AM UTC" (replace with suggested slot)
   - Triggers: createEvent MCP tool
   - Result: Meeting scheduled
   - Verification: Meeting request appears in Jane Doe's mailbox

**Key Technical Nuances:**

1. **Single tool per MCP server:** Major advantage over connector tools - one tool handles all actions within that MCP server

2. **Consent model per MCP server:** Each MCP server requires one-time consent per agent - not per tool within server

3. **Connection creation required:** Must create connection with your account to authenticate MCP server access

4. **MCP tool initialization:** Agent must initialize MCP server before calling specific tools (visible in debug pane)

5. **Natural language interpretation:** MCP servers understand natural language (e.g., "tomorrow", "Jane Doe" without email) - don't require structured input

6. **Calendar availability intelligence:** findMeetingTimes MCP tool automatically checks multiple calendars and respects working hours

7. **Frontier preview requirement:** MCP server integration requires Frontier preview program access - not generally available yet

8. **Microsoft Entra scopes:** Permissions granted based on scopes - agents only access what they need

9. **Audit trail visibility:** All MCP tool calls visible in debug pane and Microsoft Defender Advanced Hunting

10. **Connection reuse:** Once connection created for MCP server, reused across sessions - don't need to reconnect

**Best Practices for MCP Server Integration:**

1. **Test incrementally:** Add one MCP server at a time, test thoroughly before adding next
2. **Review available tools:** Scroll through MCP tools list to understand full capabilities
3. **Use debug pane:** Always check debug pane to understand which tools triggered and why
4. **Start with simple queries:** Test basic functionality (e.g., "Who is my manager?") before complex scenarios
5. **Verify tenant configuration:** Ensure prerequisites met (manager set, calendar events exist, test users created)
6. **Understand consent flow:** Expect consent card for each new MCP server - plan for user education
7. **Monitor permissions:** Review Microsoft Entra scopes to understand what access granted
8. **Document natural language patterns:** Keep examples of queries that work well for user training
9. **Test with multiple users:** Verify meeting scheduling works with different user profiles
10. **Check mailbox provisioning:** Ensure test users have active mailboxes before expecting meeting invites

**Comparison: MCP Servers vs Traditional Connectors:**

| Aspect | MCP Servers | Traditional Connectors |
|--------|-------------|------------------------|
| Tools per service | One tool per MCP server | One tool per connector action |
| Action handling | Single tool handles multiple actions | Separate tool for each action |
| Configuration effort | Lower - one connection per server | Higher - configure each action separately |
| Natural language | Built-in NL understanding | May require structured inputs |
| Standardization | Universal MCP standard | Connector-specific implementations |
| Discoverability | MCP tools listed under server | Actions must be individually added |
| Governance | Centralized via Agent 365 | Per-connector governance |
| Consent model | One-time per server per agent | May require per-action consent |

**Agent 365 vs Building Custom Integrations:**

*Without Agent 365 (Traditional Approach):*
- Custom API calls for each service
- Manual authentication handling
- Per-integration governance
- No unified audit trail
- Higher development effort
- Maintenance per integration

*With Agent 365 (MCP Approach):*
- Standardized MCP protocol
- Built-in authentication via Microsoft Entra
- Centralized governance and security
- Unified audit trail via Defender
- Rapid development with pre-built servers
- Consistent maintenance model

**Integration Architecture:**

```
User: "Can you find 3 meeting times for a 30 minute meeting with Jane Doe?"
    ↓
Agent processes natural language request
    ↓
Agent identifies need for calendar functionality
    ↓
Agent initializes Microsoft Outlook Calendar MCP Server
    ↓
Agent calls findMeetingTimes MCP tool
    ↓
MCP tool authenticates via Microsoft Entra (scoped permissions)
    ↓
MCP tool queries both user's calendar and Jane Doe's calendar
    ↓
MCP tool respects working hours, existing appointments
    ↓
MCP tool returns 3 available time slots
    ↓
Agent presents options to user in natural language
    ↓
User selects time: "Please schedule the one on 10:30 AM UTC"
    ↓
Agent calls createEvent MCP tool with selected time
    ↓
MCP tool creates calendar event and sends meeting request
    ↓
Meeting request delivered to Jane Doe's mailbox
    ↓
Agent confirms meeting scheduled
```

**Enterprise Governance Flow:**

```
MCP Tool Call Initiated
    ↓
Microsoft Entra validates agent identity (Agent ID)
    ↓
Scoped permissions checked (does agent have calendar access?)
    ↓
Microsoft Purview DLP policies evaluated
    ↓
Microsoft Information Protection (MIP) labels checked
    ↓
Rate limits verified
    ↓
Security scan performed
    ↓
Tool executes if all checks pass
    ↓
Action logged in Microsoft Defender Advanced Hunting
    ↓
Audit trail created for compliance
    ↓
Result returned to agent
```

**Developer Gotchas:**

1. **Frontier preview access required:** Can't use MCP servers without Frontier program membership - will fail silently or show no MCP servers available

2. **Tenant prerequisites often missed:** Forgetting to set manager, create test users, or provision mailboxes causes confusing test failures

3. **Consent card unexpected:** Users may not expect consent prompts - can cause confusion if not documented

4. **Connection account matters:** MCP server uses connection creator's account - permissions and calendar based on that identity

5. **Natural language variability:** "tomorrow" might not work if testing late at night near midnight UTC - ambiguous time references

6. **Calendar timezone confusion:** Meeting times returned in UTC - may differ from user's local timezone causing scheduling errors

7. **User not found errors:** Using display names (e.g., "Jane Doe") requires exact match or unique identifier - ambiguous names may fail

8. **Working hours not set:** If test user doesn't have working hours configured, findMeetingTimes may return inconvenient times

9. **Mailbox provisioning delay:** Newly created users may not have mailbox provisioned yet - meeting requests fail silently

10. **Debug pane information overload:** MCP tool calls show detailed payloads - can be overwhelming to parse for errors

11. **Tool initialization visible:** MCP server initialization step appears in debug pane - not an error, expected behavior

12. **Consent one-way:** Allowing consent can't be easily revoked from agent interface - must go to connection settings

13. **Connection reuse unexpected:** Once connection created, all agents with same MCP server may use it - could cause permission confusion

14. **Filter not obvious:** "Model Context Protocol" filter required to find MCP servers among all tools - easy to miss

15. **Multiple MCP tools per server:** Scrolling required to see all available MCP tools - may miss capabilities

**Production Considerations (Beyond This Mission):**

1. **User consent management:** Plan for consent card UX - educate users on what permissions being granted

2. **Service account strategy:** Determine if agents should use service accounts or user accounts for MCP connections

3. **Permission scoping:** Review Microsoft Entra scopes and apply least-privilege principle

4. **Rate limiting:** Monitor MCP tool call volumes to avoid throttling

5. **Error handling:** Plan for scenarios where MCP tools fail (user not found, calendar unavailable, permission denied)

6. **Audit trail analysis:** Regularly review Microsoft Defender Advanced Hunting logs for anomalous agent behavior

7. **DLP policy alignment:** Ensure MCP server actions align with organizational DLP policies

8. **Multi-tenant considerations:** For ISVs, plan for customers with different tenant configurations

9. **Fallback mechanisms:** Design agent to handle MCP server unavailability gracefully

10. **User communication:** Prepare documentation explaining what actions agent can perform via MCP servers

11. **Testing with real users:** Lab prerequisites (manager, calendar events, test users) may not match production scenarios

12. **Monitoring and alerting:** Set up alerts for failed MCP tool calls or permission errors

13. **Version management:** Track MCP server updates from Microsoft - capabilities may change

14. **Hybrid scenarios:** Some agents may need both MCP servers AND traditional connectors - plan integration strategy

15. **Performance optimization:** Minimize unnecessary MCP tool calls by using agent instructions to be selective

**Future of MCP in Agent 365:**

*Current State (Mission 10):*
- Pre-built MCP servers for Microsoft 365 services
- Low-code integration in Copilot Studio
- Manual connection creation per agent

*Future Capabilities (Beyond This Mission):*
- Custom MCP server creation via MCP Management Server
- Pro-code development in Azure AI Foundry
- ISV-certified MCP servers marketplace
- 1,500+ Power Platform connector integration
- Advanced governance with conditional access policies
- Automated connection management at scale

**When to Use MCP Servers vs Other Integration Methods:**

*Use MCP Servers when:*
- Connecting to Microsoft 365 services (Outlook, Teams, SharePoint)
- Need enterprise-grade security and governance
- Want standardized, auditable actions
- Require multiple related actions from same service
- Building agents in Copilot Studio or Azure AI Foundry

*Use Traditional Connectors when:*
- Connecting to non-Microsoft services without MCP servers
- Need specific connector action not yet available via MCP
- Working with legacy systems or custom APIs
- MCP server not available for target service

*Use Custom APIs when:*
- Building proprietary integrations
- MCP server and connectors don't support use case
- Need complete control over API implementation
- Internal systems with unique requirements

**Mission Accomplishments:**

✅ **MCP protocol understanding:** Grasp universal standard for AI integration (USB-C analogy)
✅ **Agent 365 platform knowledge:** Understand enterprise control plane for agent management
✅ **Pre-built MCP server integration:** Connect Microsoft 365 User Profile and Outlook Calendar MCP servers
✅ **Natural language actions:** Enable agents to perform real Microsoft 365 actions from conversation
✅ **Meeting scheduling workflow:** Complete end-to-end interview prep-meeting arrangement
✅ **Enterprise governance awareness:** Understand security, audit, and compliance features

**Connection to Next Mission:**

Mission 11 will focus on collecting and analyzing user feedback to continuously improve agent performance - complementing MCP integration with user experience optimization.

---

## Verbatim Training Text

Mission 10: Integrate with MCP Servers
🕵️‍♂️ CODENAME: OPERATION MCP RENDEZVOUS
⏱️ Operation Time Window: ~45 minutes

🎯 Mission Brief
Welcome, Operative. Your previous missions have shown you the power of prompts. You learned about multimodal document analysis, grounding your prompts with Dataverse data and document generation. Now you'll unlock another advanced capability: Model Context Protocol (MCP) server integration.

Your assignment, should you choose to accept it, is Operation MCP Rendezvous. In this operation you'll be connecting your agent to external MCP servers to extend its capabilities, enabling it to arrange interview prep meetings.

🔎 Objectives
In this mission, you'll learn:

How to understand and work with the Model Context Protocol (MCP) standard
How to use Agent 365 to integrate MCP servers with your Copilot Studio agents
How to connect your Copilot Studio agent to MCP servers
How to leverage MCP server capabilities within your agents
🔌 What is MCP?
Model Context Protocol (MCP) is an open standard that enables AI assistants to securely connect to external data sources and tools. Think of MCP as the USB-C of AI integration – just as USB-C provides a universal connector for various devices and peripherals, MCP provides a standardized way for AI systems to connect to different services, databases, and applications.

Before USB-C, every device had its own proprietary connector (remember all those different charger cables?). Similarly, before MCP, connecting AI agents to external systems required custom integrations for each service. MCP solves this by providing a universal "plug-and-play" protocol.

✨ Key benefits of MCP
Universal connectivity: One standard protocol works across different AI platforms and data sources
Secure access: Built-in authentication and permission controls protect your data
Extensibility: Easily add new capabilities to your agents without rewriting core logic
Interoperability: MCP servers can work with multiple AI assistants and applications
In this mission, you'll use MCP to connect your Copilot Studio agent to external services, dramatically expanding what your agent can do beyond its built-in capabilities.

🛠️ Where does Agent 365 come in?
Agent 365 is Microsoft's comprehensive platform for managing and extending AI agents at enterprise scale. It gives each AI agent its own Microsoft Entra Agent ID for identity, lifecycle, and access management, while providing the infrastructure to safely connect agents to business systems through MCP servers.

Think of Agent 365 as the enterprise control plane for your AI agents - it handles security, governance, and observability while enabling agents to interact with Microsoft 365 and business applications through standardized MCP tooling servers.

👥 How Agent 365 serves different roles
Agent 365 addresses the needs of everyone involved in the agent ecosystem:

IT Administrators: Monitor agent activity, enforce policies, and manage threats through the Microsoft 365 admin center
Security Teams: Apply enterprise-grade controls for identity, authentication, and compliance with Microsoft Purview and Defender integration
Developers: Build and extend agents using unified SDKs, pre-built MCP servers, and frameworks in Copilot Studio or Azure AI Foundry
Business Decision Makers: Deploy agents securely and measure their impact on productivity and business outcomes
Information Workers: Collaborate with agents seamlessly to amplify productivity
🔧 Agent 365 tooling servers for MCP integration
Agent 365 provides enterprise-grade MCP servers that give your agents safe, governed access to business systems, including:

Pre-built MCP servers for Microsoft 365 and business applications:

Outlook Calendar: Create, update, and manage calendar events
Outlook Mail: Send, read, and search emails
Teams: Create chats, post messages, and manage channels
SharePoint & OneDrive: Upload files, manage lists, and search documents
Word: Create and edit documents, add comments
Dataverse & Dynamics 365: Perform CRUD operations on business data
User Profile: Access user information, managers, and direct reports
Copilot Search: Chat with Microsoft 365 Copilot and ground responses with files
Enterprise security and governance:

Centralized control: Manage all MCP servers through the Microsoft 365 admin center - allow or block servers organization-wide
Scoped permissions: Agents only access the resources they need based on Microsoft Entra scopes
Full observability: Monitor and audit all tool calls using Microsoft Defender Advanced Hunting
Policy enforcement: Apply DLP, MIP, rate limits, and security scans at runtime
Threat protection: Detect and remediate attacks targeting agents with Microsoft Defender integration
Custom MCP server creation:

Build scenario-specific servers using the MCP Management Server - an API-first tool for creating custom MCP servers
Connect to 1,500+ Power Platform connectors (ServiceNow, JIRA, etc.)
Integrate Microsoft Graph APIs, REST APIs, and Dataverse custom APIs
Publish and certify custom servers for your organization
Enable ISVs to build and publish certified servers
Developer experience:

Available in both Copilot Studio (low-code) and Azure AI Foundry (pro-code)
Built into the Agent 365 SDK for seamless integration
Visual Studio Code integration for creating and testing custom MCP servers
Consistent, standardized interfaces across all tooling servers
💡 Why this matters for your agents
Agent 365 transforms MCP from an open standard into an enterprise-ready platform. Your agents get:

Deterministic, auditable actions - every tool call is tracked and governed
Production-grade reliability - all MCP servers undergo rigorous testing for accuracy, latency, and reliability
Security by default - enterprise controls are built-in, not bolted on
Rapid development - pre-built servers for common scenarios, easy customization for specialized needs
Unified management - one control plane for all agents, regardless of where they're built
🎯 What you'll focus on in this mission
While Agent 365 offers a comprehensive platform for agent management, governance, and custom MCP server development, this mission focuses specifically on using pre-built MCP servers in Copilot Studio.

You'll learn how to connect your agent to ready-made tooling servers (like Outlook Calendar and Teams) and enable real actions in Microsoft 365 applications - without building custom integrations. Think of this as learning to use the tools already in the toolbox before building your own.

🧪 Lab 10: Add MCP Servers to arrange an interview prep-meeting
IMPORTANT

For this lab, you need to make sure that you are part of the Frontier preview program to get early access to Microsoft Agent 365. Frontier connects you directly with Microsoft's latest AI innovations. Frontier previews are subject to the existing preview terms of your customer agreements. As these features are still in development, their availability and capabilities may change over time.

Add MCP servers to the Interview Agent
WARNING

In this lab, you will learn how to add two MCP servers: the Microsoft 365 User Profile MCP server and the Microsoft Outlook Calendar MCP. For the lab to work, you will need to configure the following in your tenant ahead of time:

Have a manager configured for your user which can be configured in the M365 Admin Center
Have an appointment on your calendar in the upcoming 24 hours - this is because you will test the MCP server by asking "Get my meetings for today"
Have an extra user created on your tenant, so that you can invite that user for the interview prep-meeting (How to create a user in M365)
For that extra user, the mailbox needs to be provisioned and it would be good to set the working days / hours
To add MCP servers to your agent you only have to add one tool per MCP server. This is different to connector tools which require you to add a tool for every connector action. This ability to add a single tool that handles multiple actions is one of the things that makes MCP Servers a lot easier to work with.

Add the Microsoft 365 User Profile MCP server
Open Copilot Studio and open the previously created Interview Agent

Select Tools in the top navigation

Tools navigation

Select Add a tool to start adding the MCP Server

Add a tool

Select Model Context Protocol in the filters to filter the tools down to only MCP Servers

Filter the tools to only MCP Servers

Select the Microsoft 365 User Profile MCP server from the tools list

Select the User Profile MCP Server from the tools list

Select Create new connection from the connection dropdown

Creation dropdown - create a connection

Select Create to start the create a connection process

Create connection process start

Select your account in the pick your account popup to create the connection

After picking your account, you will see the following screen. Select Add and configure to add the Microsoft 365 User Profile MCP server to the Interview Agent

Add and configure User Profile MCP server

If you scroll down on the tool overview page, you can find the MCP tools that are part of the MCP server:

Tools overview

Next, select Test to test out the newly added tool

Send the following prompt to the agent in the test pane:


Who is my manager?
Select Allow to consent that you are OK with the MCP server using your data. This consent card will only show once for the agent and this MCP server combination, after you have allowed it for this agent it will not prompt again (unless you add another MCP server that uses the same connector).

Consent card

Next, you will see the response from the agent. If all goes well, you will see something like this:

Who is my manager test

If you look on the left of the Test your agent pane, you will see that the agent initialized the MCP server, and it triggered the getMyManager MCP tool. You can also see the details of what the agent sent and received from the MCP tool.

Debug MCP tool

The first part of the lab is done, you can now ask questions about users on your tenant. This enables you to ask questions like:

- Who is my manager?
- Who are my direct reports?
- What is the job role of Daniel Laskewitz?
- And much much more...
You can now try out other tools if you want to as well. If you're ready, lets get the other MCP server added too.

Add the Microsoft Outlook Calendar MCP server
In the last section, you have added the User Profile MCP server, which makes it possible for you to work with user details on your tenant. This is very helpful when you want to for instance plan meetings, because users of your agent usually don't send a prompt that includes an email / user principal name when they want to plan a meeting. Instead, they will send a prompt like the following:


meeting with Daniel Laskewitz tomorrow
To add capabilities like this, we need to add another MCP server: the Microsoft Outlook Calendar MCP server. Bear with us: the following steps are a lot like the previous section.

Select Tools at the top navigation

Select Add a tool

Filter the tools by selecting Model Context Protocol

Scroll down and select the Microsoft Outlook Calendar MCP Server

Add Microsoft Outlook Calendar MCP Server

Select Add and configure

Now, you can scroll to the bottom again to see the tools in the Microsoft Outlook Calendar MCP server:

Microsoft Outlook Calendar MCP Server tools

Let's test out this MCP server.

Enter the following prompt:


Get my meetings for today
The agent will respond with the consent card again, because we added another MCP server. Select Allow to consent with the MCP server using your data

Consent card

Now you will get a response with the meetings you have on your calendar for today:

Get my meetings for today response

Plan an interview prep-meeting
Now, we know both the MCP servers work. We want to plan an interview prep-meeting though. So, let's see if that works too!

Select New test session to start a new test session

New test session

Enter the following prompt:


Can you find 3 meeting times for a 30 minute meeting with Jane Doe for an interview prep-meeting?
This will trigger the findMeetingTimes MCP tool and it will look at the calendars of both the user of the agent and the Jane Doe and figure out which times work based on their availability. It will then respond with three options for meetings:

Find meeting times output

And you will be able to figure out what tools have been called in the testing pane:

Debug

To plan the actual meeting you still have to respond to the agent.

Enter the following prompt (replace the time with one of the suggested meeting slots you got from the agent):


Please schedule the one on 10:30 AM UTC
This will trigger the createEvent MCP tool and schedule the meeting.

Schedule meeting

It will show the following meeting request in Jane Doe's mailbox:

Meeting Request

Now we're done with this lab. Hopefully this gave you a good overview of how MCP servers can help you in your agents!

🎉 Mission Complete
Great work, Operative! Operation MCP Rendezvous is now complete. You've successfully integrated external MCP servers with your Copilot Studio agent, unlocking powerful new capabilities for extending your agent's functionality!

🚀 Next up: In your next mission, you'll learn how to collect and analyze user feedback to continuously improve your agent's performance.

⏩ Move to Mission 11: Collecting feedback from users

📚 Tactical Resources
📖 Microsoft Copilot Studio ❤️ MCP Lab

📖 Model Context Protocol - Getting Started

📖 Extend agents with MCP in Copilot Studio

📖 Microsoft Agent 365 Overview

📖 Microsoft Agent 365 Tooling Servers Overview

📖 Microsoft 365 User Profile MCP Server

📖 Microsoft Outlook Calendar MCP Server

📖 Add users and assign licenses

Analytics
Pager
Previous page
Document Generation
Next page
Collecting Feedback from Users