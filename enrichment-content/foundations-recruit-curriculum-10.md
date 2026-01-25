# Foundations Recruit Curriculum - Session 10

## Summary

This session elevates agents from conversational assistants to autonomous operatives by introducing Event Triggers in Copilot Studio. Participants learn how to enable agents to act proactively without user prompts, responding automatically to external system events. The curriculum covers:

- **Core Concepts**: Understanding Event Triggers as mechanisms that enable agents to monitor external systems (SharePoint, Teams, Outlook, Dataverse) and execute intelligent actions autonomously when specific events occur
- **Trigger Architecture**: Learning the three-step workflow (Event Detection → Trigger Activation → Agent Response) and understanding how trigger payloads carry event information and processing instructions to agents
- **Event vs Topic Triggers**: Distinguishing between event-driven autonomous behavior and user-initiated conversational responses, including differences in authentication models and activation patterns
- **Payload Customization**: Implementing default and custom payloads to provide agents with specific instructions and data formatting, balancing global agent instructions with trigger-specific guidance
- **Common Scenarios**: Exploring practical use cases including IT help desk automation, employee onboarding, project management, document management, and meeting assistance
- **Security & Publishing**: Understanding maker authentication implications, data protection best practices, DLP policies, quota management, and technical requirements for production deployment
- **Practical Application**: Building an autonomous IT Help Desk agent that responds to SharePoint list item creation events, processes ticket details, and sends AI-generated email acknowledgments without human intervention

The hands-on lab demonstrates end-to-end autonomous agent behavior using Power Automate cloud flows, custom expressions for trigger payloads, and connector tools for email automation, preparing learners to deploy self-operating agents in production environments.

---

## Verbatim Content

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

🚨 Mission 10: Add Event Triggers - Enable autonomous agent capabilities
🕵️‍♂️ CODENAME: OPERATION GHOST ROUTINE
⏱️ Operation Time Window: ~45 minutes

🎥 Watch the Walkthrough

Event triggers video thumbnail

🎯 Mission Brief
It's time to elevate your agent from conversational assistant to autonomous operative. Your mission is to enable your agent to act without being summoned - responding to signals from across your digital domain with precision and speed.

With Event Triggers, you'll train your agent to monitor external systems like SharePoint, Teams, and Outlook, and execute intelligent actions the moment a signal is received. This operation transforms your agent into a fully operational field asset - silent, swift, and always watching.

Success means building agents that initiate value - not just respond to it.

🔎 Objectives
📖 This lesson will cover:

Understanding Event Triggers and how they enable autonomous agent behavior
Learning the difference between event triggers and topic triggers, including trigger workflows and payloads
Exploring common Event Trigger scenarios
Understanding authentication, security, and publishing considerations for event-driven agents
Building an autonomous IT Help Desk agent that responds to SharePoint events and sends email acknowledgments
🤔 What is an Event Trigger?
An Event Trigger is a mechanism that allows your agent to act autonomously in response to external events, without requiring direct user input. Think of it as making your agent "watch" for specific events and automatically take action when those events occur.

Unlike topic triggers, which require users to type something to activate a conversation, event triggers activate based on things happening in your connected systems. E.g.:

When a new file is created in SharePoint or OneDrive for Business
When a record is created in Dataverse
When a task is completed in Planner
When a new Microsoft Form response is submitted
When a new Microsoft Teams message is added
Based on a recurring schedule (like daily reminders)
Add Trigger
Why Event Triggers matter in autonomous agents
Event triggers transform your agent from a reactive assistant into a proactive, autonomous helper:

Autonomous operation - your agent can work 24/7 without human intervention, responding to events as they happen.

Example: Automatically welcome new team members when they're added to a team.
Real-time responsiveness - instead of waiting for users to ask questions, your agent responds immediately to relevant events.

Example: Alert the IT team when a SharePoint document is modified.
Workflow automation - chain together multiple actions based on a single trigger event.

Example: When a new support ticket is created, create a task, notify the manager, and update the tracking dashboard.
Consistent processes - ensure important steps never get missed by automating responses to key events.

Example: Every new employee automatically gets onboarding materials and access requests.
Data-driven actions - use information from the triggering event to make smart decisions and take appropriate actions.

Example: Route urgent tickets to senior staff based on priority level in the trigger payload.
⚙️ How do Event Triggers work?
Event triggers operate through a three-step workflow that enables your agent to respond autonomously to external events:

The trigger workflow
Event Detection - A specific event occurs in a connected system (SharePoint, Teams, Outlook, etc.)
Trigger Activation - The event trigger detects this event and sends a payload to your agent via a Power Automate Cloud Flow.
Agent Response - Your agent receives the payload and executes the instructions you've defined
Event vs Topic triggers
Understanding the difference between these two trigger types is crucial:

Event Triggers	Topic Triggers
Activated by external system events	Activated by user input/phrases
Enable autonomous agent behavior	Enable conversational responses
Use maker's authentication	Option for user's authentication
Run without user interaction	Require user to start conversation
Examples: File created, email received	Example: "What's the weather?"
📦 Understanding trigger payloads
When an event occurs, the trigger sends a payload to your agent containing information about the event and instructions on how to respond.

Default vs custom payloads
Every trigger type comes with a default payload structure, but you can customize it:

Default payload - Uses the standard format like Use content from {Body}

Contains basic event information
Uses generic processing instructions
Good for simple scenarios
Custom payload - Add specific instructions and data formatting

Include detailed directions for your agent
Specify exactly what data to use and how
Better for complex workflows
Agent instructions vs custom payload instructions
You have two places to guide your agent's behavior with event triggers:

Agent Instructions (Global)

Broad guidance that applies to all triggers
Example: "When processing tickets, always check for duplicates first"
Best for general behavior patterns
Payload Instructions (Trigger-specific)

Specific directions for individual trigger types
Example: "For this SharePoint update, send a summary to the project channel"
Best for complex agents with multiple triggers
💡 Pro tip: Avoid conflicting instructions between these two levels, as this can cause unexpected behavior.

🎯 Common Event Trigger scenarios
Here are practical examples of how event triggers can enhance your agent:

IT Help Desk Agent
Trigger: New SharePoint list item (support ticket)
Action: Automatically categorize, assign priority, and notify appropriate team members
Employee Onboarding Agent
Trigger: New user added to Dataverse
Action: Send welcome message, create onboarding tasks, and provision access
Project Management Agent
Trigger: Task completed in Planner
Action: Update project dashboard, notify stakeholders, and check for blockers
Document Management Agent
Trigger: File uploaded to specific SharePoint folder
Action: Extract metadata, apply tags, and notify document owners
Meeting Assistant Agent
Trigger: Calendar event created
Action: Send pre-meeting reminders and agenda, book resources
⚠️ Publishing and authentication considerations
Before your agent can use event triggers in production, you need to understand authentication and security implications.

Maker authentication
Event triggers use the agent creator's credentials for all authentication:

Your agent accesses systems using your permissions
Users can potentially access data through your credentials
All actions are performed "as you" even when users interact with the agent
Data protection best practices
To maintain security when publishing agents with event triggers:

Evaluate data access - Review what systems and data your triggers can access
Test thoroughly - Understand what information triggers include in payloads
Narrow trigger scope - Use specific parameters to limit what events activate triggers
Review payload data - Ensure triggers don't expose sensitive information
Monitor usage - Track trigger activity and resource consumption
⚠️ Troubleshooting and limitations
Keep these important considerations in mind when working with event triggers:

Quota and billing impacts
Each trigger activation counts toward your message consumption
Frequent triggers (like every-minute recurrence) can quickly consume quota
Monitor usage to avoid throttling
Technical requirements
Only available for agents with generative orchestration enabled
Requires solution-aware cloud flow sharing to be enabled in your environment
Data Loss Prevention (DLP)
Your organization's DLP policies determine which triggers are available
Administrators can block event triggers entirely
Contact your admin if expected triggers aren't available
🧪 Lab 10 - Add Event Triggers for autonomous agent behavior
🎯 Use case
You'll enhance your IT Help Desk agent to automatically respond to new support requests. When someone creates a new item in your SharePoint support tickets list, your agent will:

Trigger autonomously when the SharePoint ticket is created
Provide the ticket details and instructions on the steps that you want it to perform
Automatically acknowledge the ticket to the submitter via an AI generated email
This lab demonstrates how event triggers enable truly autonomous agent behavior.

Prerequisites
Before starting this lab, ensure you have:

✅ Completed previous labs (especially Lab 6-8 for the IT Help Desk agent)
✅ Access to the SharePoint site with the IT support tickets list
✅ Copilot Studio environment with event triggers enabled
✅ Your agent has generative orchestration enabled
✅ Appropriate permissions in SharePoint and your Copilot Studio environment
10.1 Enable Generative AI and create a SharePoint item creation trigger
Open your IT Help Desk agent in Copilot Studio

First, ensure Generative AI is enabled for your agent:

Navigate to the Overview tab
Under the Orchestration section, Toggle Generative orchestration to On if it's not already enabled
Enable Generative AI
Navigate to the Overview tab and locate the Triggers section

Click + Add trigger to open the trigger library
Navigate to Triggers

Search for and select When an item is created (SharePoint)
Select SharePoint Trigger

Configure the trigger name and connections:

Trigger name: New Support Ticket Created in SharePoint
Wait for the connections to configure, and select Next to proceed.
Configure trigger name and connections

Configure the trigger parameters:

Site Address: Select your "Contoso IT" SharePoint site

List Name: Choose your "Tickets" list

Additional instructions to the agent when it's invoked by the trigger:


New Support Ticket Created in SharePoint: {Body}

Use the 'Acknowledge SharePoint Ticket' tool to generate the email body automatically and respond.

IMPORTANT: Do not wait for any user input. Work completely autonomously.
Configure trigger parameters

Select Create trigger to complete the trigger creation. A Power Automate Cloud Flow is automatically created to trigger the agent autonomously.

Select Close.

10.2 Edit the Trigger
Inside the Triggers section of the Overview tab, Select the ... menu on the New Support Ticket Created in SharePoint trigger

Select Edit in Power Automate
Edit trigger in Power Automate

Select the Sends a prompt to the specified copilot for processing node

In the Body/message field, remove the Body content, press the forward slash key (/) and select Insert Expression
Insert expression for trigger

Enter the following expression to provide the agent with specific details about the ticket:


concat('Submitted By Name: ', first(triggerOutputs()?['body/value'])?['Author/DisplayName'], '\nSubmitted By Email: ', first(triggerOutputs()?['body/value'])?['Author/Email'], '\nTitle: ', first(triggerOutputs()?['body/value'])?['Title'], '\nIssue Description: ', first(triggerOutputs()?['body/value'])?['Description'], '\nPriority: ', first(triggerOutputs()?['body/value'])?['Priority/Value'],'\nTicket ID : ', first(triggerOutputs()?['body/value'])?['ID'])
Select Add
Trigger output expression

Select Publish on the top right toolbar.

10.3 Create a tool for email acknowledgment
Return to your Agent in Copilot Studio

Navigate to the Tools tab in your agent

Click + Add a tool and select Connector

Search for and select Send an email (V2) connector
Select Outlook Connector

Wait for the connection to configure, and then select Add and configure

Configure the tool settings:

Name: Acknowledge SharePoint ticket
Description: This tool sends an email acknowledgement that a ticket has been received.
Select Customize next to the input parameters and configure as follows:

To:

Description: The email address of the person submitting the SharePoint Ticket
Identify as: Email
Body:

Description: An acknowledgement that the Ticket was received, and we aim to respond within 3 working days.
Configure Input Parameters

Select Save

10.4 Test the trigger
Inside your Help Desk Agent, select the Overview tab

Click Test Trigger icon next to the New Support Ticket Created in SharePoint trigger. This will load the Test your trigger window.

Open a new browser tab and navigate to your SharePoint IT Support Tickets list

Click + Add new item to create a test ticket:

Title: "Unable to connect to VPN"
Description: "Unable to connect to corporate WIFI network after recent update"
Priority: "Normal"
Save the SharePoint item
Create Test Ticket

Return to Copilot Studio and monitor the Test your trigger panel for the trigger activation. Use the Refresh icon to load the trigger event, this may take a few minutes.
Monitor Trigger Test

Once the trigger appears, select Start testing

Select the Activity Map icon at the top of the Test your agent panel

Verify that your agent:

Received the trigger payload
Called the "Acknowledge SharePoint ticket" tool
Test trigger
Check the email inbox of the submitter to confirm the acknowledgment email was sent
Test email sent

Review the Activity tab in Copilot Studio to see the complete trigger and tool execution

✅ Mission Complete
🎉 Congratulations! You've successfully implemented event triggers with connector tools that enable your agent to operate autonomously, automatically sending email acknowledgments and processing support tickets without user intervention. Once your agent is published, it will act autonomously on your behalf.

🚀 Next up: In our next lesson, you'll learn how to publish your agent to Microsoft Teams and Microsoft 365 Copilot, making it available to your entire organization!

⏭️ Move to Publish your agent lesson

📚 Tactical Resources
Ready to dive deeper into event triggers and autonomous agents? Check out these resources:

Microsoft Learn: Make your agent autonomous in Copilot Studio
Documentation: Add an event trigger
Best Practices: Power Automate triggers introduction
Advanced Scenarios: Using Power Automate flows with agents
Security: Data loss prevention for Copilot Studio
Analytics
Pager
Previous page
Add an agent flow to your Topic for automation
Next page
Publish your agent
