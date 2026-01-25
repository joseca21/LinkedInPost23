# Foundations Recruit Curriculum - Session 11

## Summary

This session focuses on the critical final step of deploying agents to production by publishing them and making them accessible through various channels. Participants learn how to transition their developed agents from the development environment to live production use where real users can benefit from their capabilities. The curriculum covers:

- **Publishing Fundamentals**: Understanding why publishing is essential to make agent updates live and available to end users, and recognizing that unpublished changes remain unavailable regardless of configuration
- **Channel Configuration**: Exploring the eight available channels (Microsoft Teams & Microsoft 365 Copilot, Demo website, Custom website, Mobile app, SharePoint, Facebook Messenger, Power Pages, Azure Bot Service) and understanding how each channel serves different use cases
- **Channel-Specific Experiences**: Learning how different channels render agent content differently, including variations in adaptive cards, multiple-choice options, markdown support, welcome messages, and "Did-You-Mean" suggestions
- **Teams & M365 Copilot Integration**: Configuring the primary business channel to enable users to access agents within their existing workflow without switching applications, increasing adoption and reducing friction
- **Publication Process**: Step-by-step publishing workflow including confirmation, notification monitoring, and validation that updates are live
- **Organizational Deployment**: Making agents available tenant-wide through Teams App Store submission, admin approval processes, global setup policies, auto-installation, and app pinning for easy access
- **Practical Application**: Publishing the Contoso IT Help Desk agent to Microsoft Teams and Microsoft 365 Copilot, configuring availability options, editing agent details (icons, descriptions, Teams settings), and submitting for admin approval

The hands-on lab demonstrates the complete publication lifecycle from development to tenant-wide availability, ensuring learners understand how to manage agent details, control availability, and work with administrators to deploy production-ready solutions.

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

🚨 Mission 11: Publish Your Agent
🕵️‍♂️ CODENAME: OPERATION PUBLISH PUBLISH PUBLISH
⏱️ Operation Time Window: ~30 minutes

🎥 Watch the Walkthrough

Publish agent video thumbnail

🎯 Mission Brief
After completing a series of challenging modules, Agent Maker, you're now ready for your most critical step yet: publishing your agent. It's time to make your creation available to users across Microsoft Teams and Microsoft 365 Copilot.

Your agent—equipped with a clear mission, powerful tools, and access to key knowledge sources—is ready to serve. Using Microsoft Copilot Studio, you deploy your agent so it can start assisting real users, right where they work.

Let's launch your agent into action.

🔎 Objectives
📖 This lesson covers:

Why it's important to publish your agent
What happens when you publish your agent
How to add a channel (Microsoft Teams & Microsoft 365 Copilot)
How to add the agent in Microsoft Teams
How to make the agent available in Microsoft Teams for your whole organization
🚀 Publish an agent
Every time you work on an agent in Copilot Studio you might update it by adding knowledge or tools. When you're ready with all the changes, and you tested thoroughly, you're ready to publish it. Publishing ensures that the latest updates are live. When you update your agent with new tools, and you don't hit the publish button, it's not available yet for end users.

Make sure to always hit the publish button when you want to push the updates to the users of your agent. Your agent might have channels added to it and when you hit publish the updates are available for all the channels you added to the agent.

!!! important ❗ There was a recent change to Copilot Studio Trial environments that prohibits the publishing of agents. If you are in a trial environment you will not be able to complete this module to publish your agent. It will require a paid environment to publish an agent. Publishing of the agent is not required to receive a badge.

⚙️ Configure channels
Channels determine where your users can access and interact with your agent. After you publish your agent, you can make it available in multiple channels. Each channel may display your agent's content differently.

You can add your agent to the following channels:

Microsoft Teams and Microsoft 365 Copilot - Make your agent available in Teams chats and meetings, and within Microsoft 365 Copilot experiences (Learn more)
Demo website - Test your agent on a demo website provided by Copilot Studio (Learn more)
Custom website - Embed your agent directly into your own website (Learn more)
Mobile app - Integrate your agent into a custom mobile application (Learn more)
SharePoint - Add your agent to SharePoint sites for document and site assistance (Learn more)
Facebook Messenger - Connect with users through Facebook's messaging platform (Learn more)
Power Pages - Integrate your agent into Power Pages websites (Learn more)
Azure Bot Service channels - Access additional channels including Slack, Telegram, Twilio SMS, and more (Learn more)
To add a channel, navigate to the Channels tab in your agent and select the channel you want to configure. Each channel has specific setup requirements and may require additional authentication or configuration steps.

Channels tab in agent

📺 Channel experiences
Different channels have different user experiences. When building an agent for multiple channels, make sure to be aware of the differences per channel. It's always a good strategy to test your agent in multiple channels to see if it really does what you intended.

Experience	Website	Teams and Microsoft 365 Copilot	Facebook	Dynamics Omnichannel for Customer Service
Customer satisfaction survey	Adaptive card	Text-only	Text-only	Text-only
Multiple-choice options	Supported	Supported up to six (as hero card)	Supported up to 13	Partially Supported
Markdown	Supported	Partially Supported	Partially supported	Partially Supported
Welcome message	Supported	Supported	Not supported	Supported for Chat. Not supported for other channels.
Did-You-Mean	Supported	Supported	Supported	Supported for Microsoft Teams, Chat, Facebook, and text-only channels (short message service (SMS) via TeleSign and Twilio, WhatsApp, WeChat, and Twitter). Suggested actions are presented as a text-only list; users must retype an option to respond.
NOTE

There are some examples of where you can use different logic for different channels. An example of it can be found in the Power Platform Snippets repository:

Henry Jammes shared an example of how to show a different adaptive card when the channel is Microsoft Teams. (Link to example)

🧪 Lab 11: Publish your agent to Teams and Microsoft 365 Copilot
🎯 Use case
Your Contoso IT Help Desk agent is now fully configured with powerful capabilities—it can access SharePoint knowledge sources, create support tickets, send proactive notifications, and respond intelligently to user queries. However, all these features are currently only available in the development environment where you built them.

The Challenge: End users can't benefit from your agent's capabilities until it's properly published and made accessible through the channels where they actually work.

The Solution: Publishing your agent ensures that the latest version—with all your recent updates, new topics, enhanced knowledge sources, and configured flows—is available to real users. Without publishing, users would still interact with an older version of your agent that might be missing critical functionality.

Adding the Teams and Microsoft 365 Copilot channel is equally crucial because:

Teams Integration: Your organization's employees spend most of their day in Microsoft Teams for collaboration, meetings, and communication. By adding your agent to Teams, users can get IT support without leaving their primary work environment.

Microsoft 365 Copilot: Users can access your specialized IT help desk agent directly within their Microsoft 365 Copilot experience, making it seamlessly integrated into their daily workflow across Office applications.

Centralized Access: Instead of remembering separate websites or applications, users can access IT support through the platforms they're already using, reducing friction and increasing adoption.

This mission transforms your development work into a production-ready solution that delivers real value to your organization's end users.

Prerequisites
Before starting this lab, ensure you have:

✅ Completed previous labs and have a fully configured Contoso Helpdesk Agent
✅ Your agent has been tested and is ready for production use
✅ Permissions in your Copilot Studio environment to publish agents
✅ Access to Microsoft Teams in your organization
11.1 Publish your agent
Now that all our work on the agent is done, we have to make sure all our work is available for the end users that are going to use our agent. To make sure the content is available for all users, we need to publish our agent.

Go to the Contoso Helpdesk Agent in Copilot Studio (via the Copilot Studio maker portal)

In Copilot Studio, it's easy to publish your agent. You can just select the publish button at the top of the agent overview.

Publish Agent overview

Select the Publish button in your agent

It opens the publish pop-up - to confirm you really want to publish your agent.

Publish confirmation

Select Publish to confirm publishing your agent

Now a message shows that your agent is publishing. You don't have to keep that popup open. You get notified when the agent is published.

Agent is publishing

When the agent is done publishing, you see the notification at the top of the agent page.

Notification publish done

But - we only published the agent, we didn't add it to a channel yet, so lets fix that now!

11.2 Add the Teams and Microsoft 365 Copilot channel
To add the Teams and Microsoft 365 Copilot channel to our agent, we need to select Channel in the top navigation of the agent

Channels tab

Here we can see all the channels we can add to this agent.

Select Teams and Microsoft 365

Select Teams and Microsoft 365

Select Add channel to complete the wizard and add the channel to the agent

Select add channel

It will take a little while until it's added. After it's added a green notification will appear on the top of the sidebar.

Channel added

Select See agent in Teams to open a new tab

See agent in Teams

Select Add to add the Contoso Helpdesk Agent to Teams

Add agent to Teams

This should take a little while. After it should show the following screen:

Agent added successfully

Select Open to open the agent in Teams

This will open the agent in Teams as a Teams app

Agent open in Microsoft Teams

Now we have published the agent to work for you in Microsoft Teams, but you might want to make this available for more people.

11.3 Make the agent available for all users in the tenant
Close the browser tab where the Contoso Helpdesk Agent is opened

This should bring you back to Copilot Studio where the Teams and Microsoft 365 Copilot side panel is still open. We only opened the agent in Teams now, but we can do a lot more here. We can edit the details of the agent, we can deploy the agent to more users and more.

Select Edit details

Edit details

This will open a pane where we can change a bunch of details and settings of the agent. We can change basic details like the icon, the background color of the icon and the descriptions. We can also change Teams settings (for instance allowing a user to add the agent to a team, or allowing to use this agent in group and meeting chats) here. When you select more, you can also change developer details like the developer name, the website, the privacy statement and the terms of use.

Edit details pane

Select Cancel to close the Edit details pane

Select Availability options

Availability options

This will open the availability options pane, where you can copy a link to send to users to use this agent (be aware, you need to share the agent with the user too) and you can download a file to add your agent to the Microsoft Teams or Microsoft 365 store. To show the agent in the store, you have other options too: you can show it to your teammates and shared users (to show in the Built with Power Platform section) or you can show it to everyone in your org (this needs administrator approval).

Select Show to everyone in my org

Availability options

Select Submit for admin approval

Submit for approval

Now, your administrator has to approve your agent submission. They can do that by going to the Teams Admin Center and look up the Contoso Helpdesk Agent in Apps. In the screenshot you can see what the administrator would see in Teams Admin Center.

Teams app pending approval

The administrator has to select the Contoso Helpdesk Agent and select Publish to publish the Contoso Helpdesk Agent to everyone.

Teams app publish

When the administrator has published the agent submission, you will be able to refresh Copilot Studio and you should see the available in app store banner in the availability options.

Available in App Store

There are even more possibilities here. Your admin can change the global setup policy and auto install the Contoso Helpdesk Agent for everyone in the tenant. On top of that - you are able to pin the Contoso Helpdesk Agent to the left rail so that everyone has easy access to it.

✅ Mission Complete
🎉 Congratulations! You successfully published your agent and added it to Teams and Microsoft 365 Copilot! Next up is the last mission of the course: Understanding licensing.

⏭️ Move to the Understanding licensing mission

📚 Tactical Resources
🔗 Publish channels documentation

Analytics
Pager
Previous page
Add Event Triggers
Next page
Understanding Licensing
