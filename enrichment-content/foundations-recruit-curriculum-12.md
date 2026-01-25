# Foundations Recruit Curriculum - Session 12

## Summary

This session provides essential knowledge about Copilot Studio licensing and cost management to prevent unexpected billing surprises when deploying agents to production. Participants learn how usage is measured, billed, and optimized for sustainable agent operations. The curriculum covers:

- **Copilot Credits Model**: Understanding the consumption-based currency that measures all agent work including information lookups, question answering, workflow execution, topic invocations, tool calls, and grounding operations
- **Licensing Options**: Exploring three acquisition models - Pay-As-You-Go ($0.01 per credit via Azure with no upfront commitment), Copilot Credit Capacity Packs (25,000 credits/month pooled at tenant level), and Pre-Purchase Plans (annual prepaid Copilot Credit Commit Units for volume discounts)
- **User Licensing**: Distinguishing between Copilot Studio Tenant Licenses (enabling the platform) and Copilot Studio User Licenses ($0 licenses required for makers to create/manage agents)
- **Microsoft 365 Copilot Integration**: Understanding what M365 Copilot licenses ($30/user/month) include (app access, basic agent interactions in Teams/M365 channels) versus when Copilot Studio credits are still consumed (agent flows, connectors, external publishing, advanced actions)
- **Capacity Planning**: Using the Copilot Studio Agent Usage Estimator for consumption forecasting, disabling unused tools, mixing credit packs with pay-as-you-go for service continuity, and monitoring usage through Power Platform admin center
- **Real-World Scenarios**: Analyzing credit consumption patterns across different deployment models including internal Teams agents, connector-based automation, autonomous agents, external web publishing, and maker activities
- **Cost Control Strategy**: Implementing pre-planning practices to design agents that are effective, predictable, and sustainable in production environments

The lesson emphasizes that understanding licensing early enables informed design decisions, accurate cost estimation, and avoidance of budget surprises when agents scale to real user volumes in production.

---

## Verbatim Content

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

🚨 Mission 12: Understanding Licensing
🕵️‍♂️ CODENAME: OPERATION KNOW WHAT YOU OWE
⏱️ Operation Time Window: ~15 minutes – intel only, no fieldwork required

🎯 Mission Brief
Welcome, Recruit. Before you deploy agents into production, you need more than working prompts and polished responses, you need a clear understanding of how those agents are measured and billed. Licensing surprises tend to show up after an agent goes live, when usage scales and costs rise faster than expected.

This mission exists to help prevent that moment. You'll learn how Copilot Studio usage is tracked, how different deployment choices affect cost, and why pre-planning matters before publishing an agent to real users. Understanding licensing early helps you design agents that are not only effective, but also predictable and sustainable in production.

Think of this as your cost-control briefing. With the right context, you can make informed design decisions, estimate impact ahead of time, and avoid unpleasant surprises once your agent is in the wild.

🔎 Objectives
In this lesson, you'll learn:

How Copilot Studio licensing works using the Copilot Credits consumption model
How Copilot Credits are acquired through pay-as-you-go, capacity packs, and prepaid commitments
What Microsoft 365 Copilot user licenses include — and where Copilot Studio credits are still required
How different agent scenarios (internal, external, automated, and integrated) affect credit consumption
How to plan, estimate, and monitor usage to avoid unexpected costs when deploying agents at scale
🔎 What are Copilot Credits?
Copilot Credits are the currency used to measure usage in Copilot Studio.

Think of credits like metered usage, similar to minutes on a phone plan or miles on a taxi.

Copilot credits are used whenever an agent:
looks up information
answers a question
run workflows and actions
Every topic invocation, tool call, grounding operation, and custom skill consumes Copilot Credits.
More complex behavior uses more credits than simple answers
Every time your agent does real work behind the scenes, it uses Copilot Credits.

Copilot Credits replace the older "message" concept. Instead of counting interactions, you now count credits, which map more directly to work done by the agent (including actions and advanced tooling).

How Copilot Studio Licensing Works
1. Copilot Studio Pay-As-You-Go (PAYGO) Meter
This option includes:

No upfront commitment
You pay for actual Copilot Credits consumed in a billing month
Billed at $0.01 per Copilot Credit via Azure (credits consumed = cost)
Provides flexible, scalable usage without capacity limits upfront
This is ideal for early development, variable usage, or unpredictable agent workloads
2. Copilot Studio License (Copilot Credit Capacity Pack)
Monthly subscription that gives you 25,000 Copilot Credits per pack
Capacity packs are pooled at the tenant level
You can buy multiple packs depending on estimated consumption
Unused credits do not roll over month-to-month
Best for predictable usage
This option provides better predictable capacity for production environments
3. Copilot Credit Pre-Purchase Plan
Annual, prepaid option for large volumes of Copilot Credits
Credits are purchased as Copilot Credit Commit Units (CCCUs)
Each Copilot CRedit Commit Unit converts to 100 Copilot Credits
Unused credits do not roll over month-to-month
This option gives cost advantage at scale and predictable budgeting for big agent fleets
📌 Copilot Studio User Licenses
Even with capacity or credits available, your makers need the right access:

Copilot Studio Tenant License (credit capacity pack or pay-as-you-go) enables Copilot Studio in your tenant.
Copilot Studio User License ($0 license) must be assigned to any person who will create or manage agents in Copilot Studio.
This separation allows admin control of capacity while still enabling individual makers to build agents.

🧠 What Microsoft 365 Copilot Licenses Include
Microsoft 365 Copilot (e.g., $30/user/month business plans) includes:

Copilot access in apps like Word, Teams, Outlook, and Excel.
The ability for licensed users to create and interact with agents in hosted channels like Teams or Microsoft 365 Copilot.
When Copilot Studio Credits Still Apply
Even when users have Microsoft 365 Copilot licenses, Copilot Credits from your Copilot Studio capacity are used when agents do more advanced work, including:

Running agent flows
Using connectors or external services
Publishing and using agents outside of internal Microsoft 365 experiences
Executing topics, triggers, or workflows that involve actions beyond simple responses
These usages draw from your Copilot Studio capacity (paid credits), not just from an individual's Copilot user subscription.

Simple rule of thumb
Internal interaction in M365 and basic responses — usually covered by the Microsoft 365 Copilot user license when the user is signed in and using built-in channels.
Automation, integrations, and external publishing — consume your Copilot Studio credits, regardless of individual Copilot subscriptions.
📊 Capacity Planning Tips
Before you launch an agent:

Estimate consumption using the Copilot Studio Agent Usage Estimator which helps you forecast credits used per agent per month.
Disable unused tools if you aren't using them in your agent to avoid incurring extra costs.
Mix credit packs + pay-as-you-go to prevent service interruptions if capacity packs run out.
Assign Copilot Studio User Licenses to all builders to avoid access issues.
Monitor consumption in the Power Platform admin center (Billing > License > Copilot Studio).
TIP

✅ Run the Copilot Studio Usage Estimator early in the planning process and again after building to compare expected vs. actual usage.

🧠 Real-World Licensing Scenarios
Scenario	Licensing / Credits
Internal Teams agent answering questions from default knowledge sources	Covered by user license for basic interaction; external actions still use credits
Agent with Power Automate/connector actions	Uses Copilot Credits
Autonomous agents	Uses Copilot Credits
Published on external web or system	Uses Copilot Credits
Maker building agents	Requires Copilot Studio User License
🏁 Mission Complete
You now understand:

How Copilot Credits work in Copilot Studio
What Microsoft 365 Copilot licenses include and what they don't
How to plan with capacity packs, pay-as-you-go, and prepaid plans
With this knowledge, you're ready to manage agent usage cost-effectively and confidently as you scale your solutions.

📚 Tactical Resources
Learn more about licensing and billing in Copilot Studio

📄 Copilot Studio Licensing & Message Rates
📘 Power Platform Licensing Guide (July 2025)
📊 Message Management & Capacity Monitoring
Analytics
Pager
Previous page
Publish your agent
Next page
Securing Your Recruit Badge
