# Mission 04: Add Event Triggers to act autonomously

## Summary

**Mission Overview:**
Mission 04 (Operation Signal Point) teaches how to transform agents from reactive to autonomous by implementing event triggers. The mission duration is approximately 45 minutes and builds upon previous missions (01 and 03).

**Core Concepts:**

*Event Triggers:*
- Enable autonomous agent behavior without user interaction
- Fire from external system events (SharePoint, email, Planner, schedules)
- Deliver payload-driven data through connectors
- Require generative orchestration to be enabled
- Each trigger delivery counts as a message toward capacity
- Use agent maker's authentication ("agent author authentication")
- Examples: new SharePoint item, new email, Planner task assigned, time-based recurrence

*Topic Triggers vs Event Triggers:*
- Topic triggers: Conversation activity starters inside chat (user-initiated)
- Event triggers: System event starters via connectors (can run without conversation)
- Topic triggers respond to user messages (By agent, Phrases, Message received)
- Event triggers respond to external system events with structured payloads

*Interactive vs Autonomous Agents:*
- Interactive: User or chat activity triggers topics; primarily Q&A and request-driven actions
- Autonomous: External events trigger actions; proactive operations and background automation
- Interactive uses topic triggers; Autonomous uses event triggers library
- Both can coexist - agents can be both interactive and autonomous

**Key Technical Nuances:**

1. **Availability Dependency:** Event trigger availability depends on organization's data policies configured in Power Automate

2. **Authentication Model:** Triggers authenticate using the agent maker's account - ensure proper connector permissions and compliance with Power Automate data policies

3. **Capacity Impact:** High-frequency recurrences consume messages quickly (e.g., 10-minute recurrence = 6 messages/hour)

4. **Split On Setting:** Critical for email triggers - enables flow to run separately for each email rather than batching multiple emails together. Must set to `@triggerOutputs()?['body/value']`

5. **Testing Path:** Use Test trigger and activity map to validate execution before publishing

**Lab Exercise Use Case:**
Automate resume processing when emails arrive with PDF attachments:
1. Event trigger detects new email with subject "Application" and attachments
2. Check attachment contentType equals "application/pdf"
3. Extract PDF file and email body (convert HTML to text)
4. Upload to Dataverse Resume table with metadata (title, cover letter, source email, upload date)
5. Pass data to child Application Intake Agent
6. Agent flow posts adaptive card to Teams channel with link to Dataverse row

**Implementation Architecture:**
- Parent Agent: Hiring Agent (contains event trigger)
- Event Trigger: "When a new email arrives (V3)"
- Power Automate Flow: Processes attachments, uploads to Dataverse
- Child Agent: Application Intake Agent (contains agent flow for Teams notification)
- Integration Points: Email → Power Automate → Dataverse → Agent Flow → Teams

**Critical Configuration Details:**

*Trigger Settings:*
- Trigger name: "When a new email arrives from an applicant"
- Include Attachments: Yes
- Subject Filter: "Application"
- Only with Attachments: Yes
- Split On: Enabled with `@triggerOutputs()?['body/value']`

*Condition Logic:*
- Check: `Attachments Content-Type` equals `application/pdf`
- Automatically creates For each loop for array processing

*Dataverse Actions:*
- Html to text: Convert email body to plain text
- Add a new Resume row: Create record with title, cover letter (truncated to 2000 chars), source email, upload date (utcNow())
- Upload Resume File: Attach PDF to Resume PDF column using contentBytes

**Key Functions and Expressions:**
- `item()?['name']` - Get attachment filename
- `item()?['contentBytes']` - Get file binary data as Base64
- `if(greater(length(body('Html_to_text')), 2000), substring(body('Html_to_text'), 0, 2000), body('Html_to_text'))` - Truncate text to 2000 characters
- `utcNow()` - Current UTC timestamp

**Developer Tips:**
1. Enable generative orchestration first - event triggers won't appear otherwise
2. Model the payload early - decide minimal fields needed
3. Control cost with throttling and filtering conditions
4. Test before publishing using Test trigger and activity map
5. Monitor auth scope - maker's account permissions matter

**Prerequisites:**
- Completed Mission 01 and Mission 03
- Hiring Agent ready
- Access to Microsoft Teams
- Appropriate Power Automate connector permissions

**Gotchas:**
- High-frequency triggers can rack up capacity consumption quickly
- For each loop automatically appears when using array parameters
- HTML email body needs conversion to text for Dataverse storage
- Cover letter field has 2000 character limit requiring truncation
- PDF validation essential to avoid processing signature images

---

## Verbatim Training Text

Mission 04: Add Event Triggers to act autonomously
🕵️‍♂️ CODENAME: OPERATION SIGNAL POINT
⏱️ Operation Time Window: ~45 minutes

🎯 Mission Brief
Welcome back, Agent. In Mission 03 - you learned how to build an Application Intake child agent and an Interview Prep connected agent to broaden your main Hiring Agent's capabilities.

Your assignment, should you choose to accept it, is Operation Signal Point - diving deeper into event triggers - elevating your agent system from reactive to autonomous operation. You'll transform your agents from waiting for human input to proactively responding to external events and taking intelligent action without supervision.

Think of it as upgrading from agents that answer questions to agents that anticipate needs and act independently. Through event triggers and automated workflows, your Hiring Agent will detect incoming resume emails, process attachments automatically, store data in Dataverse, and notify your HR recruitment team via Microsoft Teams - all while you focus on higher-value tasks.

Welcome to the world where automation meets intelligence.

🔎 Objectives
In this mission, you'll learn:

How event triggers enable autonomous agent behavior without user interaction
The differences between interactive and autonomous agents in Copilot Studio
How to create event triggers that automatically process email attachments and upload files to Dataverse
How to build agent flows that post adaptive cards to Teams channels for notifications
How to pass data between event triggers and agent flows for end-to-end automation
🤔 What is an Event trigger?
Previously in Recruit, we learned about event triggers. Let's do a quick recap on this in case you missed it.

Event triggers let an agent act on its own when something happens in another system - no user message required. When the configured event fires - such as "new SharePoint item," "new email," "Planner task assigned," or even a time‑based recurrence, a connector sends a trigger payload to your agent. The agent then follows your instructions to decide which actions or topics to call.

Key characteristics
Autonomous activation: - Unlike topic triggers that start when a user types to the agent, event triggers fire from external events, enabling proactive behavior.

Payload-driven: - Each event delivers a payload (variables + optional instructions) through a connector. The agent uses your defined instructions and the payload to choose what to do next. - For example, call a topic or execute actions defined by Tools.

Examples out-of-the-box: - SharePoint/OneDrive file or item created - Planner task completed/assigned - Microsoft Forms response submitted - Recurrence/schedule

Availability depends on your organization's data policies configured in Power Automate.

Requires generative orchestration: - Event triggers are available only when generative orchestration is enabled for the agent.

Billing/usage: - Each trigger delivery counts as a message toward Copilot Studio capacity. - For example a 10‑minute recurrence sends a message every 10 minutes.

Auth model and setup: - You add triggers within the agent Overview, under Triggers. Authentication for the trigger connector uses the agent maker's account ("agent author authentication"). - You can edit trigger parameters and payload in the Power Automate maker portal.

Testing & observability: - You can test triggers from the agent's test pane and inspect behavior with the activity map before publishing.

TL;DR for developers

Think of event triggers as webhook-like signals that push a structured payload into your agent, letting it initiate work and chain actions across systems - without waiting for a user to ask.

Topic triggers - how they differ
Previously you learned about topic triggers in Recruit, however you might still be wondering how Topic triggers differ from Event triggers, and why that distinction matters for understanding what makes an agent autonomous.

Topic triggers control when a topic runs, usually in response to a user message.

In generative orchestration, the default trigger is By agent - the planner chooses a topic whose name/description best matches the user's message.
In classic orchestration, the default is Phrases - the planner chooses a topic when one or several trigger phrases best match the user's message.
Other trigger types include Message received, Event received, Activity received, Conversation update, Invoke received, On redirect, Inactivity, and Plan complete.

Core difference

Topic triggers are conversation activity starters inside the chat.

Event triggers are system event starters delivered via connectors that can run the agent without any conversation at all.

Quick guide of Topic trigger vs Event trigger
Topic trigger: User (or chat activity) said/did X ➡️ run Topic T.
Event trigger: SharePoint/Planner/Email/Timer fired with payload P ➡️ agent evaluates instructions ➡️ call Actions/Topics accordingly.
🏓 Interactive agent vs Autonomous agent - comparison
Now that you know the difference between event triggers and topics triggers, let's next learn about the difference between an interactive agent vs an autonomous agent.

In Copilot Studio terms, "interactive" maps to agents that primarily engage via topics in a chat or channel. "Autonomous" maps to agents that also leverage event triggers to run without user input.

The following table summarizes their differences and similarities.

Dimension	Interactive agent	Autonomous agent
How it starts	User (or chat activity) triggers a topic. Example: By agent, Phrases, Message received.	External event trigger sends a payload via connector to the agent. Example: SharePoint, Planner, email, schedule, etc.
Primary use	Q&A, guided workflows, request-driven actions in chat - Teams, web, etc.	Proactive operations and background automation - react to system changes and then notify, file, or orchestrate tasks.
Trigger surface	Topic triggers: By agent / Phrases / Message received / Activity types / Invoke / Inactivity / Plan complete	Event triggers library via connectors; payload includes event data + optional instructions.
Planner (generative orchestration)	Strongly leveraged for By agent and Plan complete triggers to select/sequence topics.	Required for event triggers; the agent uses instructions + payload to decide which actions/topics to call.
Typical example	User asks "What's our refund policy?" → Topic runs, queries knowledge, response.	New Planner task assigned → Event trigger fires → Agent posts a Teams message, updates a record, or calls a topic.
Setup path	Create topics, define trigger type, author dialog/actions; publish to channels.	Add event trigger (Overview → Triggers), authenticate connector with agent author credentials, configure payload/instructions; test via test pane; publish.
Auth and governance	Runs under channel/auth context; topic triggers respond to chat activities in allowed channels.	Trigger availability depends on Power Automate data policies; connectors run under the agent maker's account.
Observability	Test topics within Copilot Studio, inspect conversation transcripts/activities.	Use Test trigger and activity map to validate execution before publishing, monitor activity after publishing.
Capacity impact	Each user message/agent response is a message consuming capacity.	Each event delivery is also a message, plus any subsequent actions. Example: a 10‑minute recurrence = 6 messages/hour
When to use which?
Choose topic triggers (interactive) when users initiate the agent conversation - FAQ, guided intake, or command‑style tasks inside chat. The planner's By agent trigger reduces manual phrase curation.
Add event triggers (autonomous) when the agent should start the conversation or take action itself - on updates in SharePoint/Dataverse, incoming email, or on a schedule. This moves you from reactive to proactive operations.
Developer tips & gotchas
Enable generative orchestration for any agent you want to make autonomous. Event triggers won't show up otherwise.

Model the payload early. Decide what minimal fields your agent needs from the trigger such as itemId, assignedTo, dueDate and add concise instructions that tell the agent which action/topic to call based on payload values.

Auth scope matters. Triggers authenticate using the agent maker's account. Ensure that account has the right connector permissions and complies with Power Automate data policies.

Control cost and noise. High‑frequency recurrences or highly chatty sources can rack up message consumption quickly - throttle where possible or add conditions in the trigger to filter events.

Test before publishing. Use Test trigger and the activity map to watch the plan and called actions - iterate on instructions/payload until behavior is stable.

🧪 Lab 04 - Automating candidate application emails
We're next going to add an event trigger to the Hiring Agent and build an agent flow in the child Application Intake Agent to handle further processing for autonomy.

✨ Use case scenario
As an HR Recruiter

I want to be notified when an email with a resume arrives in my Inbox and is automatically uploaded to Dataverse

So that I can stay notified of resumes sent by email for applications automatically uploaded to Dataverse

We'll be achieving this using two techniques

An event trigger for when the email arrives,

Check the contentType of the file equals PDF as the format type.
Extract the file and upload to Dataverse using actions through the Dataverse connector.
Then send a prompt to the agent for further processing by passing input parameters from the Dataverse actions.
An agent flow will be added to the child Application Intake Agent which is invoked by the prompt in the event trigger.

Use the input parameters passed from the prompt of the event trigger in an adaptive card posted to a channel in Microsoft Teams to notify the HR Recruitment team. The adaptive card will have a link to the Dataverse row which can be viewed in the Hiring Agent.
Let's begin!

✨ Prerequisites to complete this mission
To complete this lab you will need to:

Have completed Mission 01 and Mission 03 and have your Hiring Agent ready.
You'll also need access to Microsoft Teams to complete the second lab exercise of posting an adaptive card to Microsoft Teams.
🧪 Lab 4.1 - Automate uploading resumes to Dataverse received by email
In the Hiring Agent, scroll down in the Overview tab to the Triggers and Channels section and select + Add.

Add trigger to agent

A list of triggers will appear. Select When a new email arrives (V3) and select Next.

Select When a new email arrives (V3) trigger

We'll now see the Trigger name and the Sign in connection references for the apps listed. Rename the trigger name to the following:


When a new email arrives from an applicant
NOTE: Make sure you see a green check by each of the connection references for the apps listed. If you don't see a green check, sign in through the ellipsis (...) and select + New connection reference to create a new connection reference.

Update details for trigger name and check connection references

The final step is to set the input properties of the trigger. Update the following properties to the following,

Property	How to Set	Details
Include Attachments (Optional)	Dropdown	Yes
Subject Filter (Optional)	Type/Enter with keyboard	Application
Only with Attachments (Optional)	Dropdown	Yes
Select Create trigger.

Configure trigger inputs

Once created, a confirmation message will appear that the trigger has been added to the agent. Select Close and the trigger will be listed in the Triggers section.

We're now going to update the event trigger to add some more automation capabilities. Select the ellipsis (...) by the trigger and select Edit in Power Automate.

Select Edit in Power Automate

The trigger will then load as a flow in the Power Automate maker portal. It will open to the flow designer where we can add further logic and actions for more automation. The trigger will appear at the top, followed by Sends a prompt to the specified copilot for processing as the last action in the flow.

Flow designer in Power Automate maker portal

By default, the When a new email arrives trigger in Power Automate may process multiple emails together if several arrive at once, running the flow only once for the batch.

To ensure the flow runs separately for each email, enable the Split On setting in the trigger's settings and select @triggerOutputs()?['body/value'] in the dropdown array field.

With Split On turned on and the array field set to @triggerOutputs()?['body/value'], the flow will run individually for each message, even if many arrive simultaneously.

Turn on Split On settings in the trigger

Let's next add some logic to check the file type of the attachment, we only want to upload .PDF file attachments and not images (these could come from email signatures). Select the + icon below the trigger and select Control under the Built in tools section.

Select Control

Select the Condition action.

Select Condition action

Now we configure the condition to check if the file attachment's type is .PDF. In the Choose a value field on the left, select the lightning bolt icon.

In the Search field type the following,


content type
Then select the Attachments Content-Type parameter from the trigger.

Condition

Let's pause here for a moment, you probably noticed that the For each action automatically appeared.

For each

This action represents looping through each attachment in the email, since the Attachments Content-Type parameter is tied to each attachment.

Underneath the hood, it's an array and that's why the For each action was automatically added when we selected the Attachments Content-Type parameter in the Condition action.

To learn more about this, expand the following additional learning block.

For Each action explained

Next, in the other Choose a value field to the right in the Condition block, type the following,


application/pdf
This will ensure that for each file attachment, it will check the file extension format is .PDF.

EqualToValue

Now we'll configure the True path to extract the file from the email and upload it into the Resume Dataverse table.

Add a new action below in the True path and search for html to text. Select the Html to text action.

To learn more about the Html to text action, expand the following additional learning block.

Add HTML to text action

Next, we need to create a new connection reference for the Html to text action by selecting Create new.

Add new connection reference

The action can now be configured. Let's add the Body parameter from the trigger. In the Content field, select the lightning bolt icon or fx icon to the right.

Add Dynamic Content

In the Dynamic content tab, search for body and select the Body parameter, followed by selecting Add.

Add Body parameter

We've completed configuring this action so let's exit from the action by selecting the two angle brackets («) pointing to the left to collapse the panel.

Collapse action panel

We'll add a new action by selecting the + icon underneath the Html to text action which will load the panel to add actions. Search for Dataverse add.Select the Add a new row action.

Add a new row action

Rename the action by pasting the following as the name in the upper left hand corner of the properties panel,


Add a new Resume row
For the Table name parameter, search for res and select the Resumes table.

Rename action and configure Table name parameter

Select the Resume Title field next and select the fx icon to the right.

Configure Resume Title parameter

In the Function tab, enter the following expression that uses the item() function.


item()?['name']
Select Add to add the expression to the Resume Title parameter.

To learn more about the item () function, expand the following additional learning block.

Add expression for Resume Title parameter

We still need to configure several more parameters, select Show all and in the Cover Letter field, select the fx icon to the right.

In the Function tab, enter the following expression that uses the same expression in the previous mission.


if(greater(length(body('Html_to_text')), 2000), substring(body('Html_to_text'), 0, 2000), body('Html_to_text'))
This expression checks if the text from the Html to text action is longer than 2000 characters, and if so, returns only the first 2000 characters; otherwise, it returns the full text.

Add expression for Cover Letter parameter

The expression will now be added to the Cover Letter field.

Expression added to the Cover Letter parameter

For the Source Email Address field, select the lightning bolt icon and search for from and select the From parameter from the trigger as this contains the email address value.

Source Email Address parameter

For the Upload Date field, select the fx icon to the right. In the Function tab, enter the following expression that uses the utcNow() function.


utcNow()
To learn more about the utcNow function, expand the following additional learning block.

Upload Date Parameter

We've now completed configuring the Add a new Resume row action so let's exit from the panel by collapsing it.

Exit from action panel

We'll add a new action by selecting the + icon underneath the Add a new Resume row action which will load the panel to add actions. Search for Dataverse Upload. Select the Upload a file or an image action.

Add the Upload a file or an image action

Rename the action by pasting the following as the name,


Upload Resume File
Rename action

Select the Content name field next and select the fx icon to the right.

In the Function tab, enter the following expression that uses the item () function. This gets the name property of the current item (the attachment file).


item()?['name']
Configure Content name parameter

For the Table name parameter, search for resumes and select the Resumes table.

Configure Table name parameter

Select the Row ID field next and select the lightning bolt icon to the right.

Search for ID and select the Resume parameter from the Add a new row Dataverse action as this contains the ID value of the row to upload the PDF file to.

Select Add.

Select Row ID

Select the Column name field and select the Resume PDF option.

Configure Column name parameter

Select the Content field and select the fx icon to the right.

In the Function tab, enter the following expression that uses the item () function. This gets the contentBytes property of the current item (the attachment file). contentBytes refers to the raw binary data of a file or attachment, encoded as a Base64 string.


item()?['contentBytes']
We've completed configuring this action so let's exit from the action by selecting the two angle brackets («) pointing to the left to collapse the panel.

Collapse action panel

Next, select the Sends a prompt to the specified copilot for processing, then drag and drop this action to be below the Upload Resume File action in the True path of the condition.

Drag and drop action in True path

Select the Sends a prompt to the specified copilot for processing to configure it.

Select action

In the Body/message field, select all of the field content and clear/delete it.

Clear Body parameter

Copy and paste the following text into the Body/message field and highlight the RESUME