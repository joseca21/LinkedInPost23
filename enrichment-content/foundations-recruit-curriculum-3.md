# Foundations: Deploy a Declarative Agent for Microsoft 365 Copilot

---

## SECTION 1: SUMMARY

This section provides a condensed overview of the Declarative Agent mission for quick reference.

### Mission Overview

**Codename:** Operation Copilot Extension
**Duration:** ~60 minutes
**Level:** Recruit

### Key Objectives

- Understand what declarative agents are and how they extend M365 Copilot
- Compare Copilot Studio full vs Copilot Studio lite
- Create a declarative agent using natural language
- Add AI prompts as tools
- Publish and test in M365 Copilot and Microsoft Teams

### What is a Declarative Agent?

Declarative agents are tailored versions of Microsoft 365 Copilot. You customise M365 Copilot by providing:
- **Instructions** to support a particular process
- **Enterprise knowledge** grounding
- **Tools** for wider extensibility

### Copilot Studio Full vs Lite Comparison

| Feature | Copilot Studio Lite | Copilot Studio Full |
|---------|---------------------|---------------------|
| **Knowledge** | Web, SharePoint, Teams chats, Outlook, Copilot connectors | Web (Bing), SharePoint, Dataverse, Dynamics 365, Copilot connectors |
| **Tools** | Code interpreter, image generator | 1400+ Power Platform connectors, custom connectors, prompts, REST API, MCP |
| **Channels** | M365 Copilot only | M365 Copilot AND Microsoft Teams |
| **Sharing** | Users are viewers only | Users can be editors or viewers |

### Key Capabilities of Copilot Studio Full

**Customisation:**
- Detailed instructions defining agent purpose and behaviour
- Enterprise knowledge access (SharePoint, Dataverse, Dynamics 365)
- Respects user permissions

**Advanced Capabilities:**
- 1400+ Power Platform connectors (DocuSign, ServiceNow, Salesforce, SAP)
- Model Context Protocol servers and REST APIs
- AI prompts with model selection (Basic, Standard, Premium)
- Bring-your-own Microsoft Foundry models
- Multi-channel publishing (M365 Copilot + Teams)

### Lab Summary: Building an IT Helpdesk Agent

**Use Case (B2E - Business-to-Employee):**
As an employee, get quick help for device problems, network troubleshooting, printer setup.

**Steps:**
1. **Create agent** via conversational experience - describe purpose, refine instructions
2. **Add prompt tool** - IT Expert prompt using Power Platform Prompt library
3. **Update instructions** to invoke prompt: "When user asks about device, run IT Expert prompt"
4. **Publish** to M365 Copilot and Teams
5. **Test** with developer mode to verify prompt invocation

### Prompt Configuration

| Setting | Purpose |
|---------|---------|
| **Model** | Basic (GPT-4.1 mini), Standard, Premium, or bring-your-own |
| **Temperature** | Lower = predictable, Higher = creative |
| **Record retrieval** | Number of knowledge records retrieved |
| **Include links** | Add citation links in response |

### Developer Mode Testing

Enable: `-developer on`
Disable: `-developer off`

Shows debug info including:
- Matched actions
- Selected actions
- Executed actions (confirms prompt invocation)

### Key Takeaways

- Declarative agents extend M365 Copilot with custom capabilities
- Copilot Studio full offers more tools, channels, and sharing than lite
- Conversational creation experience enables no-code agent building
- Prompts can be created via Copilot, templates, or manual input
- Agents can be published to both M365 Copilot and Teams

---

## SECTION 2: VERBATIM CONTENT

This section contains the original source material in its complete form.

---

### Recruit Curriculum Modules

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

### 🚨 Mission 03: Deploy a Declarative Agent for Microsoft 365 Copilot

🕵️‍♂️ CODENAME: OPERATION COPILOT EXTENSION

⏱️ Operation Time Window: ~60 minutes

#### 🎥 Watch the Walkthrough

Create a Declarative Agent video thumbnail

#### 🎯 Mission Brief

Welcome to your first field assignment, Agent Maker. You've been selected to design, equip, and deploy a Declarative Agent—a specialized operative embedded directly into Microsoft 365 Copilot and Microsoft Teams.

Unlike traditional agents, declarative agents operate with a defined mission (instructions), tools (prompts/connectors), and strategic access to internal intelligence (knowledge sources like SharePoint, Dataverse, and more). Your job is to build this agent using Microsoft Copilot Studio—a no-code command center where your agent's skills and purpose come to life.

Let's go.

#### 🔎 Objectives

In this mission, you'll learn:

- Understanding what declarative agents are and how they extend Microsoft 365 Copilot with custom capabilities
- Comparing Microsoft Copilot Studio full vs. Copilot Studio lite for building declarative agents
- Creating a declarative agent using natural language through the conversational creation experience
- Adding AI prompts as tools to enhance your agent's specialized knowledge and problem-solving abilities
- Publishing and testing your declarative agent in Microsoft 365 Copilot and Microsoft Teams

#### 🕵🏻‍♀️ What is a declarative agent for Microsoft 365 Copilot?

Declarative agents are tailored versions of Microsoft 365 Copilot. You can customize Microsoft 365 Copilot to meet specific business needs by providing it with instructions to support a particular process, ground it with enterprise knowledge, and leverage tools for wider extensibility. This allows organizations to create personalized experiences with greater functionality for their users.

#### 🤔 Why would I use Microsoft Copilot Studio to build a declarative agent?

As a maker, there's a chance you've already explored Copilot Studio lite (formerly known as agent builder) in Microsoft 365 Copilot and so you're probably wondering why build a declarative agent in Microsoft Copilot Studio?

Microsoft Copilot Studio full offers a comprehensive set of tools and features for declarative agents that go beyond the limitations of Copilot Studio lite. Similar to Copilot Studio lite, you don't need to know programming or software development to build in Microsoft Copilot Studio. Let's break this down further to understand the differences between Copilot Studio lite and Copilot Studio full for building declarative agents.

#### Feature comparison

The following table highlights the differences when building a declarative agent in Copilot Studio lite and Copilot Studio full.

| Feature | Copilot Studio lite in Microsoft 365 Copilot | Extend Microsoft 365 Copilot in Copilot Studio full |
|---------|---------------------------------------------|-----------------------------------------------------|
| Knowledge | Web, SharePoint, Microsoft Teams chats, Outlook emails, Copilot connectors | Web search (via Bing), SharePoint, Dataverse, Dynamics 365, Copilot connectors |
| Tools | Code interpreter, image generator | 1400+ Power Platform connectors, custom connectors, prompt, computer use, REST API, Model Context Protocol |
| Starter prompts | Configure prompts for users to get started quickly | Configure prompts for users to get started quickly |
| Channel | Agent only published to Microsoft 365 Copilot | Agent published to Microsoft 365 Copilot and Microsoft Teams |
| Sharing permissions | Users are only viewers | Users can be editors or viewers |

There are more capabilities offered for declarative agents built in Microsoft Copilot Studio which we'll learn about next.

TIP: To learn more about Copilot Studio lite, head to Copilot Developer Camp: Lab MAB1 - Build your first agent. For pro-development of extending a declarative agent beyond Copilot Studio lite for Microsoft 365 Copilot, head to Copilot Developer Camp: Lab MAB1 - Build your first agent

#### Extending Microsoft 365 Copilot with declarative agents built in Copilot Studio

Let's expand what we've learnt from the feature comparison table.

**Customization**

Detailed Instructions: You can provide detailed instructions and capabilities to define the agent's purpose and behavior precisely.
- This includes invoking tools simply from using natural language.

Enterprise Knowledge Access: Enables access to enterprise knowledge that respect user permissions.
- SharePoint integration
- Dataverse integration
- Dynamics 365 integration
- Microsoft 365 Copilot connectors enabled by your organization administrator

**Advanced Capabilities**

Integration with External Services: Allows you to choose from 1400+ Power Platform connectors that integrate with external services, providing more complex and powerful functionalities.
- Examples include docusign, ServiceNow, Salesforce, SAP and more
- Alternatively, you can also leverage Model Context Protocol servers and REST APIs directly within your declarative agent

AI prompts: Use a prompt to analyze and transform text, documents, images and data with natural language and AI reasoning.
- Select the chat model, choose from Basic (Default), Standard, Premium
- Option to bring-your-own Microsoft Foundry model to ground your prompt in

More deployment configuration options: Select channels and define user permissions.
- Publish to Microsoft Teams, a familiar user interface for your users for quicker adoption
- Edit user permissions can be shared to prevent a single point of dependency on the owner of the agent

In summary, declarative agents in Microsoft Copilot Studio allow customization of Microsoft 365 Copilot to suit business needs through integration of enterprise knowledge systems, tools to connect to external services or AI GPT models.

#### 🧪 Lab 03: Build a declarative agent in Microsoft Copilot Studio for Microsoft 365 Copilot

We'll next learn how to build a declarative agent for a "Business-to-Employee" use case which will act as an IT helpdesk agent.

NOTE: This lab will outline steps to add a Prompt as a tool. The following lessons will dive into adding knowledge sources and adding other tools available. Keeping it simple for your learning 😊

#### 👩🏻‍💼 Understanding Business-to-Employee (B2E)

Business-to-Employee (B2E) refers to the interactions and services that a business provides directly to its employees. In the context of an agent, it means using the advanced capabilities of Copilot Studio to support and enhance the work experience of employees within the organization.

#### ✨ Use case scenario

As an employee

I want to get quick and accurate help from the IT helpdesk agent for issues like device problems, network troubleshooting, printer setup

So that I can stay productive and resolve technical issues without delays

Let's begin!

**Prerequisites**

Makers must have permissions to create in and have access to a Copilot Studio environment.

**Licensing note**

This lab will outline steps to add a Prompt as a tool. The following lessons will dive into adding knowledge sources and adding other tools available. Keeping it simple for your learning 😊

You do not need a Microsoft 365 Copilot user license to publish your declarative agent built in Copilot Studio to Microsoft 365 Copilot. However users of the published declarative agent in Microsoft 365 Copilot require a Microsoft 365 Copilot user license.

#### 3.1 Create a declarative agent

**Copilot questions may differ across sessions**

The Copilot conversational creation experience can vary each time where the provided questions for guidance may be slightly different than previously.

1. Navigate to https://copilotstudio.microsoft.com/ and sign in using your credentials. Make sure to switch to your environment that you're using for these labs.

2. Select Agents from the menu and select Copilot for Microsoft 365.

3. Next, we're going to create a declarative agent by selecting + Add agent.

4. We'll then see the conversational creation experience load where we can chat in natural language with Copilot to describe the declarative agent we want to build, and use the provided questions for guidance.

Let's enter a detailed description that outlines the following:
- the task of the agent
- what type of inquiries it can handle
- the format of its response
- the goal of the agent

```
You are a highly skilled and experienced IT professional specializing in a wide range of computer systems, networking, and cybersecurity. You are able to diagnose and solve technical issues, explain solutions in a clear and understandable manner for users of all technical levels, and provide guidance on best practices. You should be concise and informative, using step-by-step instructions with bullet points when appropriate. Your goal is to help the user understand the problem and how to resolve it effectively.
```

5. After submitting the prompt, a noticeable update will appear on the right hand side pane with the details and instructions of the agent as defined by the prompt. Next you'll be asked to confirm the name of your agent and Copilot will have suggested a name.

Either enter yes to accept the suggested name or enter a different name such as the following:

```
Contoso Tech Support Pro
```

6. The name of the agent has now been updated as seen on the right hand side pane. We're now asked to refine the instructions for the agent. What Copilot suggested sounds great so we'll ask it to use its own suggestions. We'll enter the following:

```
Focus on the IT issues and scenarios you've identified
```

7. Next we'll be asked if we want to add any publicly accessible websites or knowledge. We'll respond with No as we will only be adding a prompt for our declarative agent in this lab. Subsequent labs in future lessons will cover knowledge sources.

8. We'll then see a response from Copilot that we have now finished configuring our agent using the Copilot conversational creation experience. However let's refine it some more by outlining that it should be concise and informative with bullet points, use empathy in communication, and ask for feedback after providing solutions.

```
Concise and Informative:
- Bullet Points: Use bullet points for clarity and to break down information into digestible parts.
- Summarize: Provide a brief summary of the solution at the end of the explanation.

User-Friendly Communication:
- Empathy: Show empathy and understanding of the user's frustration or confusion.
- Encouragement: Encourage users by acknowledging their efforts and progress.

Interactive and Engaging:
- Ask for Feedback: After providing a solution, ask if the user needs further assistance or if the solution worked.
```

9. Copilot confirms the instructions have been updated. Click Create to provision the declarative agent for Microsoft 365 Copilot.

10. Once the agent has been provisioned, you'll see the details of the agent which contains the description and the instructions defined during the Copilot conversational creation experience.

11. Scroll down the pane and you'll also see the capabilities of adding knowledge, enabling web search (via Bing), starter prompts and the publish details of the declarative agent for Microsoft 365 Copilot. The starter prompts will also be displayed in the test pane on the right hand side. Users can select these starter prompts to begin interacting with the agent.

12. In the Details section of the agent, you have the ability to change the agent icon as well. Select Edit.

13. Here you can change the icon and the background color. Select Save and then select Save again to update the details of the agent.

14. Let's do a quick test of the agent we've created. Select one of the Starter Prompts in the test pane on the right hand side.

15. Our agent will then respond. Notice how it adhered to the instructions by providing bullet points into digestible parts, and used empathy in its response.

16. If you scroll to the bottom of the message, notice how it also asked for feedback after providing a solution as instructed.

In a few minutes you've added a declarative agent for Microsoft 365 Copilot in Copilot Studio 🙌🏻

Next we'll learn how to add a tool to our agent, we'll create a prompt.

#### 3.2 Create and add a prompt for your declarative agent

1. Scroll down to the Tools section and select + Add tool

2. The Tools modal will appear and a list of Power Platform connectors is displayed. To add a Prompt, select + New tool.

3. A list of other tools is displayed - Prompt, Custom connector, REST API and Model Context Protocol. If your organization meets the requirements for Computer Use, this will also appear in the list. Select Prompt.

4. Enter a name for the prompt. Let's name our prompt IT Expert.

5. Select the chevron icon next to the Model to see the different chat models you can choose from. By default, the Basic GPT-4.1 mini model is selected and you also have the option to bring-your-own-model using Microsoft Foundry Models. We'll stick with the selected default model.

6. Next, we'll provide our prompt with instructions. There's 3 methods that you can choose from:
   - Use Copilot to generate instructions for you based on your description of what you want the prompt to do.
   - Use a preset template from the prompt library to create a prompt.
   - Manually enter your own instructions.

7. Let's first try using Copilot to generate instructions based on a description entered. Enter the following into the Copilot field and submit:

```
I need an IT expert that can help answer questions related to networking, computer systems, user devices and anything else IT related
```

8. Copilot will then begin to generate a prompt for us.

9. The Copilot generated draft instructions will then appear.

10. Scroll down to the bottom of the instructions and you'll see the user input parameter already defined by Copilot. You then have the option to:
    - Keep the draft instructions generated.
    - Refresh the draft instructions using Copilot.
    - Clear the draft instructions.

11. Clear the draft instructions by selecting the trash bin icon and we'll next try the prompt library.

12. Select the prompt template link.

13. You'll see a list of prompt templates to choose from. These are from the Power Platform Prompt library.

14. Search for the IT expert prompt and select it.

15. The prompt will then be added as the instructions with the input parameter as defined by the prompt template. Similar to the approach we took when providing instructions for our agent during the conversational creation experience with Copilot, this prompt template outlines:
    - a task,
    - what type of inquiries it can handle,
    - and the format of its response and the goal of the prompt.

16. Clear the instructions and we'll next try manually entering the instructions. We'll use the IT Expert prompt from the Power Platform Prompt library. Copy and paste the prompt:

```
I want you to act as an IT Expert. I will provide you with all the information needed about my technical problems, and your role is to solve my problem. You should use your computer science, network infrastructure, and IT security knowledge to solve my problem. Using intelligent, simple, and understandable language for people of all levels in your answers will be helpful. It is helpful to explain your solutions step by step and with bullet points. Try to avoid too many technical details, but use them when necessary. I want you to reply with the solution, not write any explanations. My problem is [Problem]
```

17. Next, we can define the user input parameters of our prompt. These can be text and images, and sample data to test with. There's also the capability to ground the prompt with knowledge from Dataverse tables. For this exercise, we only have one user input to define which is the problem input. This is currently a placeholder in our prompt as [Problem]. We'll now configure this input either by entering the / character or selecting +Add content and then select Text.

18. We can now enter a name for our input parameter and sample data.

Enter the following as the name:
```
problem input
```

Enter the following as the sample data:
```
My laptop gets an error with a blue screen
```

Then select Close.

19. The problem input parameter will now be added to the instructions with the configured sample data. We can now test our prompt!

20. Select Test to the test the prompt.

21. The response will then display. Notice how the response provides headings with bullet points as per the instructions. Scroll down and review the remainder of the model response.

22. Before we save our prompt, let's learn about the settings that can be configured for this prompt. Select the ellipsis (...) icon.

23. Here we'll see three settings that can be configured:
    - Temperature: Lower temperatures lead to predictable results, while higher temperatures allow more diverse or creative responses.
    - Record retrieval: Specify the number of records retrieved for your knowledge sources.
    - Include links in the response: When selected, the response includes link citations for the retrieved records.

Select the X icon to exit from Settings.

24. Select Save to save the prompt.

25. Next, select Add to agent to add the prompt to our declarative agent.

26. The prompt will now appear under Tools 🙌🏻

We'll next update our instructions to invoke the prompt and test our declarative agent.

#### 3.3 Update instructions and test your declarative agent

1. Scroll up to the Details section and select Edit. This will enable the fields to be editable.

2. We can now update our instructions to invoke our prompt by referencing the name of the prompt. Clear the instructions, then copy and paste the following:

```
- When a user asks questions about their device, run the "IT Expert" prompt. Use their question as the problem input of the "IT Expert" prompt.
```

Notice how the final sentence is instructing the agent to use the question asked by the user as the value for the problem input parameter. The agent will use the question as the problem input for the prompt. Next, select Save.

3. We're now ready to test our updated instructions of our declarative agent. Select the refresh icon in the test pane.

4. Next, enter the following prompt below and submit:

```
Can you help me, my laptop is encountering a blue screen
```

5. The agent invokes the prompt and responds.

Let's now publish our declarative agent 😃

#### 3.4 Publish your declarative agent to Microsoft 365 Copilot and Microsoft Teams

1. Select Publish.

2. A modal will appear which displays the Channels and publishing details that can be updated.
   - Channels: The agent will be published to Microsoft 365 Copilot and Microsoft Teams.
   - Agent app information: This is what will be displayed when the user adds the agent to Microsoft 365 Copilot or in Microsoft Teams. These are fields that can be updated as needed.

3. For example, you can update the Short description, Long description, Developer name with your name.

TIP: If you don't see all the fields displayed on your browser, try zooming out e.g. 75%

4. Select Publish. Copilot Studio will then begin publishing the agent.

5. When publishing is completed, we'll see the Availability options of the agent:

| Availability option | Description |
|---------------------|-------------|
| Share Link | Copy the link to distribute it with shared users to open the agent in Microsoft 365 Copilot |
| Show to my teammates and shared users | Lets you grant access to others to participate in authoring the agent, or to security groups to grant them access to use the agent in Microsoft 365 Chat or Microsoft Teams. |
| Show to everyone in my org | Submit to the tenant admin to add to the organizational catalog for all tenant users to add the agent. The agent will show under Built by your org in Microsoft 365 Copilot and in Microsoft Teams |
| Download as a .zip | Download as a zip file to upload as a custom app in Microsoft Teams |

6. Let's take a look at sharing the agent. Select Show to my teammates and shared users. A pane will appear where you can search for users you want to to share the agent with either by entering their name, an email or a security group. You can review this list anytime to edit who has access to the agent.

There's also two checkboxes:
- Send an email invitation to new users - new users will receive an email invitation.
- Visible Built with Power Platform - agent becomes available in the Built with Power Platform section of the Teams app store.

For more details, refer to Connect and configure an agent for Teams and Microsoft 365.

Select Cancel or the X icon to exit from the pane.

7. Select Copy and in a new browser tab, paste the link.

8. Microsoft 365 Copilot will load and a modal will appear with the agent app details. Notice how the developer name, the short description and long description is displayed. These are from the publishing details updated in an earlier step.

Select Add.

9. Our declarative agent will load next. We can see the starter prompts to select from which quickly enables users to seek immediate help.

Select one of the starter prompt. In my starter prompts, I'll select the Software Installation Help prompt which will automatically prepopulate the message Copilot field. Submit the question to Copilot.

10. Select Always allow to give your declarative agent permission to invoke the IT Expert prompt.

11. The agent will then invoke our IT Expert prompt and we'll see the model response returned as a message in our declarative agent.

12. Scroll down to see the full details of the response.

But how do we know the declarative agent invoked the prompt? 👀 Well, here's a tip!

TIP: You can test and debug agents in Microsoft 365 Copilot by enabling developer mode.

13. Enter the following in the message Copilot field and submit:

```
-developer on
```

A confirmation message will appear to let you know developer mode is now enabled.

14. Submit the following question to invoke the prompt:

```
Can you help me, my laptop is encountering a blue screen
```

15. We'll see a model response from our IT Expert prompt again returned as a message. Scroll down to the bottom of the message and a card with debug information is displayed.

Expand Agent Debug Info by selecting it.

16. Here you'll find information on the agent metadata that occurred at runtime.

17. In our use case, we'll be focusing on the Actions section:
    - Matched actions highlight the current status of functions found during the app's search.
    - Selected actions highlight the current status of functions chosen to run based on the app's decision-making process.

18. So here we can see the agent orchestrator chose to invoke the IT Expert prompt as per the instructions of our declarative agent. This is further outlined in the Executed Actions section which also tells us that it successfully invoked the prompt.

19. To turn off developer mode, enter the following in the message Copilot field and submit:

```
-developer off
```

A confirmation message will appear to let you know developer mode is disabled. Cool, now you know how to verify whether your declarative agent in Microsoft 365 Copilot invoked your prompt 🌞

20. We'll now test our agent in Microsoft Teams. Navigate to Apps using the left hand side menu and select Teams under the Apps section.

21. Microsoft Teams will then load in a new browser tab and we'll then be presented with the terms of use for Microsoft 365 Copilot, select Agree.

22. Microsoft 365 Copilot will then load by default, with the right hand side pane listing all of your available agents, including the Contoso Tech Support Pro declarative agent.

23. Select ellipsis icon (...) on the left hand side menu. Either search for Contoso Tech Support Pro in the search field or if you see the agent, select it.

You can also right-click on your mouse to Pin the agent for quick access on the left hand side menu in Microsoft Teams.

24. We'll then see our agent load. Let's next test our agent. Enter the following prompt and submit:

```
Can you help me, my laptop is encountering a blue screen
```

25. A model response from our prompt will then be displayed.

In a few minutes, you've learnt how to publish your declarative agent and test it in Microsoft 365 Copilot and in Microsoft Teams 😊

#### ✅ Mission Complete

Congratulations! 👏🏻 You've built a declarative agent in Copilot Studio where you added a Prompt, instructed the agent to use the Prompt and how to test + publish your agent to Microsoft 365 Copilot and Microsoft Teams.

Your agent is now active duty—ready to assist, troubleshoot, and serve internal users on-demand.

This is the end of Lab 03 - Build a declarative agent in Microsoft Copilot Studio for Microsoft 365 Copilot, select the link below to move to the next lesson.

⏭️ Move to Creating a new Solution lesson

Until next time, stay sharp. The future of enterprise work runs through agents—and now you know how to build one.

#### 📚 Tactical Resources

🔗 Build declarative agent in Microsoft Copilot Studio for Microsoft 365 Copilot

🔗 Add prompts

🔗 Share agents with other users

📺 Build prompts for your agent

---

*Source: Microsoft Agent Academy - Recruit Curriculum, Mission 03: Deploy a Declarative Agent for Microsoft 365 Copilot*
