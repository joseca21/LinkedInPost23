# Foundations Recruit Curriculum - Session 9

## Summary

This session transforms conversational agents into automation powerhouses by introducing agent flows in Copilot Studio. Participants learn how to move beyond simple chat interactions to create workflows that take real actions within business systems. The curriculum covers:

- **Core Concepts**: Understanding agent flows as deterministic, step-by-step workflows that automate tasks and integrate with applications and services, distinguishing them from Power Automate cloud flows
- **Key Features**: Exploring natural language authoring, AI actions for intelligent document processing and summarization, generative actions for adaptive workflows, integration with 1400+ connectors, and human-in-the-loop approval processes
- **Agent Flow Designer**: Using the visual canvas to build workflows with drag-and-drop actions, managing parameters, version history, error checking, and testing capabilities
- **Expressions & Functions**: Implementing formulas for dynamic data handling, including text manipulation, math operations, date/time functions, logical conditions, and data transformations
- **Best Practices**: Building flows incrementally, using descriptive naming, thorough testing, version control, and maintaining clean workflow designs
- **Practical Application**: Creating an end-to-end device request automation that captures user input via adaptive cards, retrieves SharePoint data, sends manager notifications via email, and provides seamless feedback

The hands-on lab demonstrates how agent flows integrate SharePoint connector actions and Office 365 Outlook actions to create a complete business automation scenario within the conversational agent experience.

---

## Verbatim Content

Skip to content

Agent Academy


Menu
On this page
Sidebar Navigation
Home

Our Team

Recruit
Overview

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

🚨 Mission 09: Add an agent flow to your Topic for automation
🕵️‍♂️ CODENAME: OPERATION AUTOMATION POWERHOUSE
⏱️ Operation Time Window: ~30 minutes

🎥 Watch the Walkthrough

Agent flow video thumbnail

🎯 Mission Brief
Your agent can now converse with users and provide information, but true operational excellence requires your agent to take action. This mission will transform your conversational agent into an automation powerhouse by equipping it with agent flows.

By mission's end, you'll have created an end-to-end device request automation that captures user input through an adaptive card, retrieves data from SharePoint, sends notifications to managers via email, and provides seamless user feedback - all orchestrated by your agent through intelligent workflow automation.

🔎 Objectives
In this mission, you'll learn:

Understanding what agent flows are and how they differ from Power Automate cloud flows for automation
Learning the key features that make agent flows powerful including AI actions and natural language authoring
Exploring the agent flow designer and how to use expressions for dynamic data handling
Creating a complete device request automation that integrates SharePoint data and email notifications
🤔 What is an agent flow?
Agent flows are a powerful way to automate repetitive tasks and integrate your apps and services. Think of them as structured, step-by-step workflows that your agent can execute to automate tasks or connect with other applications and services. You can think of them as mini workflows that help your agent do things like send notifications, update records, or respond to events.

Unlike autonomous agents that use AI to make decisions on the fly, agent flows are deterministic workflows - meaning they follow the same path every time, ensuring consistent and reliable results.

In simple terms:

They help your agent do things, not just say things to users.
They're reusable across topics and agents, and can be triggered by user messages, events, or other applications and services.
🙋🏽 Yes, but how is it different to Power Automate cloud flows?
Both agent flows and Power Automate cloud flows help automate tasks. They're designed for different purposes and work in different ways.

🤖 Agent flows in Copilot Studio
What they're for:

Built for conversational and autonomous agents (via agent instructions) in Copilot Studio.
Focused on smart, AI-driven automation that interacts with business systems.
Why they're useful:

Easy to build and manage directly in Copilot Studio.
Great for automating tasks that happen during the conversation with users such as submitting a leave request.
You don't need a separate Power Automate license as billing is based on usage inside Copilot Studio. This can save time and cost for enterprise teams.
Limitations:

You can't share them, copy them, or assign co-owners.
Agent flows are only visible and usable within Copilot Studio.
Currently, event triggers for agents can be edited in the Power Automate maker portal.
☁️ Power Automate cloud flows
What they're for:

Designed for general-purpose automation across many apps and services.
Can run independently or work alongside agent flows.
Why they're useful:

Offers a wide range of connectors.
Ideal for automating processes outside of agents.
Can be shared, reused, and managed across teams.
Requirements:

You need a Power Automate license to use them.
📗 Summary
Use this	When you want to
Agent flows	Automate tasks inside an agent, use AI, and keep everything in Copilot Studio
Power Automate cloud flows	Automate across apps and services, or build workflows outside of agents
👍🏻 Why use agent flows
Agent flows always follow a fixed path - they do the same thing every time when given the same input.

This makes them:

Reliable - you can trust that they'll behave the same way every time.
Predictable - you know what result to expect when the flow runs.
Rule based - they follow steps that you define.
Other benefits are:

Automation - enables your agent to handle repetitive tasks such as submitting forms or sending notifications.
Connected - connect with 1400+ connectors like ServiceNow, SharePoint, Salesforce. Otherwise you can build your own custom connector.
Tightly integrated - agent flows are part of the agent's logic, they're triggered directly by user messages or actions in the conversation.
Scalability - reuse flows across multiple agents or scenarios.
No-code or low-code - you can build flows using natural language or a visual designer.
All-in-one-platform - you can design, test and deploy agent flows in one place - Copilot Studio. No need to switch between platforms.
🏄🏻‍♂️ How do agent flows enhance your agent?
Agent flows expand what your agent can do beyond "chatting" with users. They allow it to take action and interact with systems.

Let's say you're working in a finance department and you receive a lot of invoices from vendors. Normally, someone has to read each invoice, pull out the important details - the amount, date, who it's from, and check if everything matches your records. Then send it to the right person for approval. This takes time and effort.

With agent flows in Copilot Studio, you can automate this process. As soon as the invoice comes in, the agent:

Reads the document using intelligent document processing to find the key information.
Checks the details against your enterprise data to make sure everything looks correct.
Route it for approval to the right person(s).
This saves time, reduces mistakes and makes the whole process much smoother.

Think of it this way
Agents: the smart decision-makers
Agent flows: the reliable executors
Why it matters
You get the best of both worlds: reliable automation and flexible AI.
It's easy to build and update flows as your business needs change.
You can scale automation across teams.
🔌 Key features that make agent flows powerful
Natural language authoring

You can describe what you want the flow to do in plain English.
Copilot understands your intent and builds the flow for you.
No need to write code - explain your idea.
AI actions

Use AI to:

Read and understand documents or images.
Summarize long content into short, useful answers.
Make smart recommendations or decisions.
Generative actions

These let the flow adapt in real time.
The agent can plan and adjust steps based on changing information.
Integration actions

Connect your flow to other tools like Outlook, Microsoft Teams, ServiceNow, SharePoint and other applications and services, through from +1400 built-in connectors or from your own custom connector.
This helps your agent work with the apps your team already uses.
Human in the loop

Add approval steps where a person needs to review or confirm something.
Advanced approvals supports reminders, delegation, and multi-stage approvals.
⚙️ How they work
Trigger

An event starts the flow - such as a user asking a question, invoking the flow from a topic, a scheduled time, or an event happening in another system.

Actions

These are steps that the agent follows next - send an email, call an API, update a ticket in ServiceNow.

🧶 How to create an agent flow
Natural language: describe what you want the agent to do, and Copilot builds it for you.
Designer canvas: drag and drop actions, conditions, and loops in the agent flow designer to build your agent flow.
🎨 What is the agent flow designer?
It's a visual tool in Copilot Studio that helps you build, edit, and manage agent flows that provide step-by-step instructions your agent follows to complete tasks. It's designed to be straightforward to use, even if you're new to agent flows.

Key features of the agent flow designer
Visual canvas

You can see your entire flow laid out like a diagram.
Easily zoom in/out, fit the view or use a minimap to navigate large flows.
Add and remove actions

Click the plus (+) button to add a new action such as sending a message or updating an item in a SharePoint list.
You can search for actions from connectors, and configure them through its settings.
To remove an action, click the three dots (⋮) and select Delete.
Check parameters

Click on any action to view or edit its settings called parameters.
You can enter values manually or use expressions to make them dynamic.
Version history

Every time you save your flow, a version is recorded.
You can go back and view or restore previous version if needed.
Error checking

The Flow Checker highlights any errors.
All errors will need to be resolved prior to publishing your flow.
Publish and test

Once your flow is error-free, publish to make it live.
Use the Test feature to run your flow manually or automatically, and check if it works as expected.
Why use the agent flow designer?
Visual and intuitive - you can build flows by dragging and clicking.
Safe to experiment - version history lets you undo changes.
Built-in testing - helps you make sure everything works before going live.
🔤 You mentioned expressions - what are expressions?
Expressions are small formulas or commands that help your agent flow work with data. You use them to calculate values, format text, make decisions, or pull specific information from inputs.

Why use expressions?
Expressions let you:

Customize how data is handled - combine names, format dates.
Make decisions - if a value is greater than 10, do something.
Transform data - change text to lowercase, extract part of a string.
Automate logic - without writing full code.
What do expressions look like?
Expressions use functions. I'm going to borrow an explanation of what functions are from former Microsoft MVP, Jerry Weinstock.

!!! quote Functions are built-in logic to transform your data either through simple or complex operations in your expression.

Functions enable you to build expressions without you needing to write any code.

The way I like to describe it, is that a function in agent flows is similar to Excel functions. You can perform an operation on data to transform it into a desired output. When building your formula in Excel you select your input value from the cells in a table or a range, and then apply functions to manipulate the data output. An example is using the COUNT function to work out the number of cells that contain numbers from a range.

In agent flows, instead of referencing data from cells in a table, you're referencing data outputs from the trigger or actions when building your expressions. Continuing with the previous example, use the function length to retrieve the number of items returned from the Get items SharePoint connector action.

Why do functions matter?
Using functions makes your agent flows:

Smarter - they can react to different inputs or conditions.
Flexible - you can customize how data is handled.
Efficient - you avoid manual steps by automating logic.
Most useful functions
The following are common functions used in agent flows. For the full list of functions, head to the reference guide.

🔡 Text
concat() - Joins two or more pieces of text together. - Example: concat('Hello ', firstName) → "Hello John"

toLower() / toUpper() - Changes text to lowercase or uppercase. - Useful for standardizing input.

substring() - Extracts part of a string. - Example: Get the first 3 letters of a name.

trim() - Removes spaces from the beginning and end of text.

🔢 Math and number
add(), sub(), mul(), div() - Basic math operations. - Example: add(5, 3) - the output is 8
📅 Date and time
utcNow() - Gets the current date and time in UTC. - Great for timestamps.

addDays(), addHours() - Adds time to a date. - Example: addDays(utcNow(), 7) output is 7 days from now.

formatDateTime() - Formats a date into a readable string. - Example: Monday, July 7, 2025

✅ Logical
if() - Runs one value if true, another if false. - Example: if(score > 50, 'Pass', 'Fail')

equals() - Checks if two values are the same.

and(), or(), not() - Combine multiple conditions.

🪣 Other handy functions
coalesce() - Returns the first non-empty value. - Useful for fallback/default values.

guid() - Generates a unique ID. - Useful for tracking or logging.

length() - Counts how many characters or items are in a string or array.

⭐ Best practices
Here are some best practices for building agent flows in Copilot Studio.

Start simple and build gradually

Begin with a small, clear task such as sending a message.
Add more steps after testing the basics of your automation.
Use clear and descriptive action names

Label each step clearly so you know and your team understands what it does.
Example: instead of the default name of "Update item" for the SharePoint connector action, rename it to what it's updating, such as "Update device status."
Check for errors before publishing

Use the flow checker to find and fix any issues.
You can't publish flows if there are errors, so try to resolve them when they occur.
Test your flow thoroughly

Just because it saves and publishes, doesn't mean it works as expected.
Use the Test feature to run your flow manually or automatically, and check the results.
Use Version History

Save your flow often so you can go back to earlier versions if needed.
You can view and restore previous versions using the Version History panel.
Use parameters and expressions wisely

When configuring actions, use parameters to make your flow dynamic.
You can enter values manually or use expressions to calculate them, or combine it with values from actions upstream by using the dynamic content picker.
Delete unused actions

If you add an action and later decide you don't need it, remove it to keep your flow clean.
🧪 Lab 09 - Add an agent flow for automation and enhance topic capabilities
We're now going to learn how to enhance our topic with adaptive cards and using advanced functionality of topics and nodes.

✨ Use case
As a manager of an employee

I want to receive device requests

So that I can review the device requested by the employee.

Let's begin!

Prerequisites
SharePoint list

We'll be using the Devices SharePoint list from Lesson 00 - Course Setup - Step 3: Create new SharePoint site.

If you have not set up the Devices SharePoint list, please head back to Lesson 00 - Course Setup - Step 3: Create new SharePoint site.

Contoso Helpdesk Agent

We're going to use the same agent created previously in Lesson 06 - Create a custom agent using natural language with Copilot and grounding it with your data.

9.1 Create an agent flow
In this exercise, we'll create an agent flow that retrieves the SharePoint item of the selected device and send an email to a manager with the device details.

In the Request device topic, scroll down to the Ask with adaptive card node and add a new node. Select Add a tool and in the Basic tools tab of the fly out pane, select New Agent flow.

Add new Agent flow

The Agent flows Designer will load with a trigger and action.

Trigger - When an agent calls the flow

This will trigger a flow from a Copilot Studio agent.
Action - Respond to the agent

This send a response that can contain output values back to the Copilot Studio agent.
Select the trigger.

Select the trigger

Next, we're going to add several inputs for the agent flow.

DeviceSharePointId - this will store the value, ID, of the SharePoint item. This ID value is an output from the Ask with adaptive card node where the user selected the device.

User - this will be the name of the user which will be from a system variable of the agent.

AdditionalComments - this will be the the comment entered by the user, which is an output from the Ask with adaptive card node.

We'll first add the DeviceSharePointId as an input for our trigger. Select + Add an input.

Add an input

For the type of user input, select Text.

Select Text

For the name of the input, enter the following.


DeviceSharePointId
DeviceSharePointId input

We'll now add the second input, User. Repeat the same steps, select + Add an input and select Text.

Add an input

For the name of the input, enter the following.


User
User input

We'll now add the third input, AdditionalComments. Repeat the same steps, select + Add an input and select Text.

Add an input

For the name of the input, enter the following.


AdditionalComments
AdditionalComments input

For the AdditionalComments input, we'll update it to make it optional. Select the ellipsis (...) icon and select Make the field optional.

Make the field optional

Great work! The trigger has now been configured, let's continue. Select the plus + icon under the trigger to insert a new action.

Add action

The Actions pane will appear where you can view actions from 1400+ built-in connectors to Microsoft and third-party services. In the search field enter the following,


Get item
A list of actions will display in the search results. Select the Get item action from the SharePoint connector.

Get item action

We can now begin configuring the Get item action.

Select the Ellipsis (...) icon in the Get item action.

Select ellipsis

Select Rename.

Select Rename

Rename the action to,


Get Device
Rename action

In the Site Address field, select the Site address of the Contoso IT SharePoint site created in Lesson 00 - Course Setup - Step 3: Create new SharePoint site.

In the List Name field, select the Devices SharePoint list.

Input parameters

In the Id field, select the lightning bolt icon or fx icon to the right.

Dynamic content picker

In the Dynamic content tab of the flyout pane, enter the following,


sharepoint
The search results will show input parameters that match the value searched. Select the DeviceSharePointId parameter from the trigger.

Next, select Add to add the dynamic content input into the Id parameter of the action.

Select DeviceSharePointId input

The dynamic content input from the trigger is now referenced in the Id parameter of the action. We're going to update one of the advanced parameters next. Select Show all to view the advanced parameters.

View advanced parameters

The Limit Columns by View parameter will be displayed and by default it's set to Use all columns (Do not limit). We'll update this value to a view to limit the columns returned in the response of the action. Select the Limit Columns by View parameter to view the list of views.

Select parameter

Select the All Items view.

Select All Items view

Select the plus + icon under the Get Device action to insert a new action.

Add new action

In the search field enter the following,


send an email
A list of actions will display in the search results. Select the Send an email (V2) action from the Office 365 Outlook connector.

Send an email action

We next need to create a connection for the connector action. Select Sign in.

Create connection

Select your signed in user account.

Select user account

Select Allow access. A connection has now been created.

Select allow access

Rename the action to the following,


Send an email to manager
Let's next define the input parameters of our action.

For the To input parameter, select yourself. Normally this would be your manager or we'd use another action that pulls through your manager based on your Entra ID profile but for the purpose of this lesson, select yourself.

For the Subject input parameter, enter the following,


Request type: new device
For the Body input parameter, enter the following,


Hi,

New device requested from

Manufacturer:
Model:
Link to item in SharePoint
Additional comments from:

This is an automated email from Contoso Helpdesk Copilot
Re
