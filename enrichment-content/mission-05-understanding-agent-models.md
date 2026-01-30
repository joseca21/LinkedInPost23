# Mission 05: Understanding Agent Models

## Summary

**Mission Overview:**
Mission 05 (Operation Archetype) teaches how to select and manage AI models for Copilot Studio agents. The mission duration is approximately 45 minutes and builds upon Mission 02's focus on agent instructions.

**Core Concepts:**

*What is the Agent Model:*
- The underlying generative AI engine powering agent responses
- Determines how the agent thinks and responds (speed, quality, reasoning depth)
- Different models have distinct capabilities: some respond faster, others provide more detailed answers or excel at complex reasoning
- Selection affects user satisfaction, performance, and costs

**Model Use Categories:**

1. **Deep Models:**
   - Optimized for deliberate, multi-step reasoning and tool-supported workflows
   - Strengths: Complex analytics, multi-hop reasoning, policy/contract analysis, multi-system troubleshooting, long document synthesis with citations
   - Highest latency, highest cost, deepest reasoning depth

2. **Auto Models:**
   - Optimized for mixed workloads; routes queries dynamically
   - Strengths: Helpdesk and employee agents with mixed intents, blending knowledge and actions, tier-0 customer support with unpredictable complexity
   - Variable latency and cost, multi-step tool-rich reasoning

3. **General Models:**
   - Optimized for speed and cost on everyday chat and light grounding
   - Strengths: Drafting, rewriting, summarizing, translation, FAQ-style grounded answers, simple action automation
   - Lowest latency, lowest cost, shallow-to-moderate reasoning

**Model Availability Tags:**

- **Experimental:** For experimentation only, not recommended for production; subject to preview terms with limitations on availability and quality
- **Preview:** Will eventually become GA, not recommended for production; subject to preview terms with limitations
- **No tag (Generally Available):** Production-ready for scaled use; most have no limitations on availability/quality
- **Default:** The default model for all agents, usually best performing GA model; periodically upgraded; used as fallback if selected model unavailable
- **Retired:** Old default model after new one takes over; usable for up to 1 month after retirement

**OpenAI Models (as of 2025):**

| Model | Category | Availability | Key Strengths | Ideal Use Cases |
|-------|----------|--------------|---------------|-----------------|
| GPT-4o | General | Retired | Fast, versatile; text+image input; cost-effective | Routine Q&A, summarizing, quick drafts, text+visuals |
| GPT-4.1 | General | Default | Higher accuracy/reasoning than 4o; excellent complex text analysis (text-only) | Detailed document analysis, complex knowledge Q&A, precision-critical scenarios |
| GPT-5 Chat | General | Preview | Advanced conversational abilities, strong context retention, human-like dialogue | Employee self-service, IT/HR helpdesks, natural interactive agents |
| GPT-5 Auto | Auto | General | Optimized for orchestrating multi-step workflows, automates actions across systems | End-to-end process automation, multi-step sequences, "digital project manager" scenarios |
| GPT-5 Reasoning | Deep | Preview | Latest complex reasoning model (trained to Oct 2024), high document understanding scores | Advanced reasoning, extensive planning, complex data interpretation |
| GPT-5.1 Chat | General | Experimental | Latest experimental conversational model, improved context awareness/responsiveness | General Q&A, versatile chatbot scenarios with newest capabilities |
| GPT-5.1 Reasoning | Deep | Experimental | Experimental top-tier reasoning, maximum depth/accuracy for complex tasks | Ultra-complex analytical queries, high-stakes data analysis, intricate strategic planning |

**Anthropic Models (External - Preview):**

| Model | Status | Key Strengths | Ideal Use Cases |
|-------|--------|---------------|-----------------|
| Claude Sonnet 4.5 | Experimental | Excels at code-related tasks and complex agent workflows; strong tool use and step-by-step reasoning | Advanced software development (code generation/debugging), multi-step autonomous agents, external tool/system integration |
| Claude Opus 4.1 | Experimental | Specialized for intensive analysis and structured problem-solving | In-depth data analysis, research projects, complex reasoning (compliance auditing, elaborate planning) |

**Critical Technical Nuances:**

1. **Context Length:** All models support large context windows (e.g., GPT-4.1 supports 128K tokens); all trained on data up to mid-2024

2. **Model Location:** Settings page → Model section in Generative AI tab → dropdown to select

3. **Default Starting Model:** New agents start on GPT-4o (balanced choice for most scenarios)

4. **Model Updates:** Microsoft periodically upgrades models; November 2025 added GPT-5.1 Chat and GPT-5.1 Reasoning

5. **Retired Model Grace Period:** Up to 30 days to continue using retired model after upgrade via "Continue using retired models" toggle

**Why Continue Using Retired Models:**

- **Compatibility:** New model outputs may differ in format/content; downstream systems may need adjustment
- **Compliance & Data Policies:** Strict vetting required; new model may not be approved yet or handle data differently (different regions)
- **Business Needs:** Mission-critical events where stability trumps new features

**Admin Controls (Critical for Model Selection):**

| Admin Setting | Effect | Location |
|---------------|--------|----------|
| Allow Anthropic models | When allowed, users can connect to Anthropic external models; when disabled, only OpenAI available | Microsoft 365 Admin Center |
| Allow Preview & Experimental Models | When ON, makers can choose preview/experimental AI models; when OFF, only production-ready available | Power Platform admin center |
| Move Data Across Regions | Required ON if experimental models enabled; permits data processing/storage outside home region; if OFF, cross-region models blocked | Power Platform admin center |

**Key Admin Control Implications:**
- Experimental/preview models may process data in non-standard ways or outside certain regions
- Organizations can restrict who can use preview models
- If experimental models missing or warnings appear, admin may have disabled them or not enabled cross-region data movement
- Regulated industries may need to stick to GA models unless clearance obtained

**Anthropic External Models Warning:**
- Hosted outside Microsoft, subject to Anthropic terms and data handling
- Requires review and acceptance before makers can use
- Available before official release for early access/feedback
- NOT recommended for production
- May experience slowdowns/timeouts due to limited capacity
- Might not be supported in future

**Response Formatting:**
- Defines style and structure of AI replies (bold, italic, links, dynamic content)
- Critical for readability and user experience
- Supports subset of Markdown for rich text
- Options include: Bold (highlight key info), Italics (subtle emphasis)
- Configured in generative answer node

**Developer Best Practices:**

1. **Model Selection Strategy:**
   - Use General models for everyday chat, FAQ, quick tasks (lowest cost/latency)
   - Use Auto models for mixed workloads with unpredictable complexity
   - Use Deep models for complex reasoning, multi-step workflows, analytical tasks

2. **Testing Experimental Models:**
   - Only use in Sandbox or Developer environments
   - NOT for production use
   - May have variable quality, latency, or timeouts
   - Still billed at established rate if published

3. **Managing Model Transitions:**
   - Test new model in controlled environment before switching
   - Use 30-day grace period to update prompts/instructions
   - Compare old vs new model responses
   - Ensure downstream systems compatible with new model outputs

4. **Compliance Considerations:**
   - Verify data residency requirements
   - Check if cross-region data movement is acceptable
   - Ensure model approved by compliance team
   - Understand Anthropic external hosting implications

**Gotchas:**

1. Experimental/preview models have limited testing and higher performance variability
2. Anthropic models are external and subject to different terms/data handling
3. Cross-region data movement required for many experimental models
4. Admin controls can block model access even if technically available
5. Retired models only available for 30 days post-upgrade
6. Model upgrades can change response format/tone requiring prompt adjustments
7. Preview models may be discontinued in future

---

## Verbatim Training Text

Understanding Agent Models
🕵️‍♂️ CODENAME: OPERATION ARCHETYPE
⏱️ Operation Time Window: ~45 minutes

🎯 Mission Brief
Welcome back, Agent. In Mission 02,you learned how strong instructions shape agent behavior.

Now it's time to choose the brain.

In Operation Archetype, you'll learn how to select the right AI model for your agent and how to test model changes to see the impact on response quality, structure, and depth. Different models can respond faster or slower, be more concise or more detailed, and handle complex reasoning differently.

By the end of this mission, you'll be able to confidently choose a model based on your scenario and validate that choice by comparing results.

🔎 Objectives
In this mission, you'll learn:

How to understand and select the optimal AI model for your agent's use case
How to compare different model capabilities and performance characteristics
How to switch your agent's model
How to test and evaluate differences in output when you change models
🤔 What is the Agent Model?
The agent model is the underlying generative AI engine powering your Copilot agent's responses. Copilot Studio lets you select which model your agent uses, enabling you to leverage different strengths (speed, output quality, cost, etc.) depending on your scenario. The model you choose determines how your agent thinks and responds, for example, one model may respond faster, another may produce more detailed answers, while another might excel at complex reasoning.

🎭 Why it matters
Selecting the appropriate model ensures your agent performs optimally for your use case. Each available model has distinct capabilities and specializations, so aligning the model with your requirements (such as quick replies vs. deep analysis) can improve user satisfaction and manage costs.

🪁 Available models
Copilot Studio supports OpenAI models and Anthropic models. Each model will have a category tag and an availability tag.

Model use categories
Different models are designed for specific tasks. Selecting the right model improves your agent's performance. For instance, use a Deep model for complex decision-making or a General model for broad, conversational topics.

The table below outlines model tags, their strengths, and key considerations - source.

Tag	Description	Strengths	Latency	Cost	Reasoning depth
Deep	Optimized for deliberate, multi-step reasoning and tool-supported workflows.	Complex analytics, multi-hop reasoning, policy and contract analysis, troubleshooting with multi-system steps, and synthesis of long documents with citations	Highest	Highest	Multi-step, tool-rich
Auto	Optimized for coverage across mixed workloads; routes queries dynamically.	Helpdesk and employee agents with mixed intents, blending knowledge and actions, and tier‑0 customer support with unpredictable complexity	Variable	Variable	Multi-step, tool-rich
General	Optimized for speed and cost on everyday chat and light grounding.	Drafting, rewriting, summarizing, and translation, FAQ-style grounded answers, and simple action automation	Lowest	Lowest	Shallow-to-moderate
Model availability
Models are released in stages. You can explore cutting-edge options like Experimental or Preview models, or stick with a stable, fully tested Generally Available model.

The table below explains the availability tags - source.

Tag	Description
Experimental	Used for experimentation, and not recommended for production use. Subject to preview terms, and can have limitations on availability and quality. See Limitations of experimental and preview models.
Preview	Will eventually become a generally available model, but currently not recommended for production use. Subject to preview terms, and can have limitations on availability and quality. See Limitations of experimental and preview models.
No tag	Generally available. You can use this model for scaled and production use. In most cases, generally available models have no limitations on availability and quality, but some might still have some limitations, like regional availability.
Default	The default model for all agents, and usually the best performing generally available model. The default model is periodically upgraded as new, more capable models become generally available. Agents also use the default model as a fallback if a selected model is turned off or unavailable.
Retired	When a new model becomes the default model, the old default model is retired. You can still use the retired model for up to one month after retirement. For more information, see Continue using a retired AI model.
OpenAI models
AI capabilities evolve rapidly, and Copilot Studio keeps up by offering a range of Azure OpenAI models. As of 2025, the primary models to choose from include OpenAI's GPT-4.1, and the latest GPT-5 previews. The following table summarizes the main choices and what each is best suited for:

Model Version	Category	Availability	Key Strengths	Ideal Use Cases
GPT‑4o	General	Retired	Fast, versatile responses; supports text and image input; cost-effective balance of speed and accuracy.	Routine Q&A; summarizing support chats or calls; quick content drafts; tasks combining text with visuals.
GPT-4.1	General	Default	Higher accuracy and reasoning than GPT-4o; excellent at complex text analysis (text-only model).	Analyzing detailed documents (policies, reports); complex knowledge-base Q&A; scenarios where precision is critical.
GPT‑5 Chat	General	Preview	Advanced conversational abilities with strong context retention; produces human-like dialogue.	Employee self-service chatbots; IT/HR helpdesk assistants; interactive agents requiring natural, human-like responses.
GPT‑5 Auto	Auto	General	Optimized for orchestrating multi-step workflows; can automate actions across systems (not just chit-chat).	End-to-end process automation (e.g. ticket creation to resolution); multi-step task sequences across apps; "digital project manager" scenarios.
GPT‑5 Reasoning	Deep	Preview	- Latest model optimized for complex reasoning (trained up to Oct 2024) - High scores in document understanding and response accuracy	Advanced reasoning tasks where top-tier analytical capability is required (such as extensive planning, interpreting complex data). Again, use cautiously in testing since it's a preview model.
GPT‑5.1 Chat	General	Experimental	Latest experimental conversational model with broad task proficiency; improves on context awareness and responsiveness.	General-purpose Q&A and dialogue tasks leveraging the newest model's capabilities; versatile chatbot scenarios where enhanced performance is beneficial.
GPT‑5.1 Reasoning	Deep	Experimental	Experimental top-tier reasoning model offering maximum depth and accuracy for complex tasks.	Ultra-complex analytical queries or decision support requiring the highest precision (e.g. intricate strategic planning, high-stakes data analysis).
WARNING

Experimental/preview models (like GPT-5 Chat) are accessible for testing new capabilities before they're production-ready. They may have limited testing and higher variability in performance.
They are not recommended for production use because of possible instability (variable quality, latency, or even time-outs). Always review any Preview model's limitations and consider using them only in non-critical environments. Use them in Sandbox or Developer environments. If you do publish an agent with an experimental model, usage will still be billed at that model's established rate.
Anthropic models (external)
Currently there are two Anthropic models which are currently under Preview, they are accessible in early release environments.

Claude Sonnet 4.5 is Anthropic's newest, coding and agent-focused model.
Claude Opus 4.1 is a reasoning-focused model.
OpenAI remains as the default model for new agents in Copilot Studio and you have the flexibility in selecting either of these models.

Both are available in Microsoft Copilot Studio as opt-in preview (Frontier Program) models rather than General Availability (GA), meaning they're for early experimental use only. The table below compares their status, strengths, and ideal use cases in the Copilot Studio context:

Model Version	Status	Key Strengths	Ideal Use Cases
Claude Sonnet 4.5	Experimental	Excels at code-related tasks and complex "agent" workflows; strong at tool use and step-by-step reasoning.	Advanced software development assistance (code generation & debugging); building multi-step autonomous agents; tasks requiring integration with external tools or systems.
Claude Opus 4.1	Experimental	Specialized for intensive analysis and structured problem-solving.	In-depth data analysis and research projects; complex reasoning scenarios (e.g. compliance auditing, elaborate planning) where thoroughness is paramount.
WARNING

It's important to note that these are external models. Anthropic models are hosted outside Microsoft and are subject to Anthropic terms and data handling, which need to be reviewed and accepted before makers can use them. These models are available before an official release so that you can get early access and provide feedback. Therefore, it is not recommended to use these models for Production purposes.
Please note that you could also experience slowdowns or timeouts due to limited capacity and availability, and these models might not be supported in the future. Admins can control access to this feature (more of this soon as you progress from here!).
🔢 Context length and data training
All the above models are capable with large context windows. For instance, GPT-4.1 supports up to 128K tokens of context. They are all trained on data up to mid-2024 (GPT-5 on slightly later data). This means they know information up to those cut-off dates, which is useful for understanding their knowledge limitations when they generate answers.

🔧 Changing and updating the model of your agent
By default, a new Copilot agent starts on the GPT-4o model, which is optimized as a balanced choice for most scenarios.

You can switch the agent's primary model anytime via the agent's Settings page ➡️ Model section in the Generative AI tab, using a simple dropdown to pick from available models.

Agent models available

This flexibility allows you to experiment with different models even after your agent is built. For example, switching to an experimental model to evaluate if it improves answer quality for your use case.

📶 Model updates and retired models
Microsoft periodically upgrades the available models to newer versions. Notably, in November 2025, several models were made available:

GPT-5.1 Chat
GPT-5.1 Reasoning
NOTE

Refer to Model updates periodically to understand model updates made by Microsoft.

If your agent was using the retired GPT-4o model, it would have been transparently moved to GPT-4.1 which is the default OpenAI model.

🧶 Why might you continue using a "Retired" model?
With AI model upgrades happening automatically, Copilot Studio provides a safety valve for continuity. You may have cases where you need to stick with the previous model for a short time, even after an upgrade.

For example, to maintain compatibility, to meet compliance requirements, or simply because your solution's behavior with the new model needs evaluation before fully switching over. Microsoft recognizes this and allows makers to continue using a retired model for up to 30 days after an automatic upgrade.

Compatibility: Perhaps the new model's outputs differ in format or content. If your downstream systems or prompts expect the old model's style, you might need time to adjust your logic. The grace period lets you run on the known model while you update and test your agent with the new model in a controlled way. You can make adjustments without disrupting users.

Compliance & Data Policies: Some organizations have strict vetting for AI models. An experimental new model might not yet be approved for use, or it might handle data in a different way (for example, the new model might use data centres in different regions). If that's a concern, an admin might decide to delay the switch until compliance checks are done.

Specific Business Needs: You might have a mission-critical event (product launch, demo) where stability is more important than getting new features quickly. Sticking with the older model ensures no surprises during that period.

🌳 How to use a retired model
On your agent's Settings page, in the Model section in the Generative AI tab, there is a toggle option labeled "Continue using retired models". This becomes available when a model update is rolled out.

Setting for Continue using retired models

If you switch this on, your agent will remain on the previous model version for that 30-day window. During that window, you can toggle between the old and new model to compare responses and gradually roll over. After 30 days, the old model is fully removed from service, so you should plan to move to the new model by then. In practice, this feature offers a buffer to support a smooth transition.

Example
Suppose your agent was using GPT-4o and it got upgraded to GPT-4.1. If you notice the AI's tone changed or it uses slightly different phrasing that doesn't align with your established conversational style, you could toggle on "use retired model" to temporarily revert to GPT-4o.

You then have a few weeks to update your prompts/instructions to suit GPT-4.1's style (maybe adding an instruction like "keep responses brief") and test thoroughly. Test your agent on GPT-4.1 in a safe environment, and then disable the retired model toggle once confident. This way, your end users have a consistent experience during the transition.

🔐 Admin controls for AI model selection
It's worth noting that not every copilot environment allows all model choices by default. There are organization-level settings that tenant administrators control. This is especially relevant for experimental models. Organizations may want to restrict who can use preview AI models (since they might process data in non-standard ways or outside certain regions).

Here are the key admin controls affecting which models a maker/developer can select for an agent:

Enable Anthropic models to be used within your organization: An admin with the Global administrator role needs to enable (allow) anthropic models in the Microsoft 365 Admin Center. If this setting is disabled, only OpenAI models will be available to select.
Allow Anthropic provider setting in Microsoft 365 admin center

Allow Preview (Experimental) models to be used in Copilot Studio environments: An admin can toggle whether preview and experimental AI models are available in a given environment. If this is turned off, makers/developers will only see generally-available models (like GPT-4o) in the dropdown.

To use GPT-5 or any future preview, the admin must turn this setting on for that specific environment.

Enable external model setting

Move data across regions: Because experimental models may not run in the same regional data centers as standard models, enabling them often requires allowing cross-region data movement. In the Power Platform admin center (environment settings), there is a setting called Move data across regions. This must be turned on by the admin if you want to permit experimental model usage. It acknowledges that data processed by these models may leave your organization's geographic boundaries.

For example, if your environment is in Europe and an experimental model is only hosted in US datacenters, this setting needs to be enabled to let that data flow happen. If it's disabled, Copilot won't use those models.

Move data across regions settings

These admin settings ensure that organizations stay in control of sensitive aspects like data residency and feature stability. As a developer building an agent, if you find that the option for GPT-5 preview models are missing or you see a warning about generative AI not being available, it could be that your admin has disabled experimental models or hasn't enabled cross-region data movement. In such cases, you'd need to contact your tenant admin to adjust the environment settings if experimental features are desired.

For a quick reference, here's a summary of the admin controls related to model selection:

Admin Setting	Effect on Model selection	Setting location
Allow Anthropic models	When Allowed, users can connect to the Anthropic external models for agents built in Copilot Studio. When disabled, only OpenAI models are available.	Microsoft 365 Admin Center
Allow Preview & Experimental Models	When ON, makers can choose preview/experimental AI models (for example GPT-5 Chat) for their agents. When OFF, only production-ready models are available.	Power Platform admin center
Move Data Across Regions	Required to be ON if experimental models are enabled. It permits data from the agent to be processed and stored outside the home region. If this is OFF, any model that would require cross-region data flow will be blocked, leading to the agent's generative AI features being unavailable. Managed in the Power Platform admin centre by a tenant administrator.	Power Platform admin center
TIP

If you're an admin concerned about data compliance, disable the use of Anthropic models + keep the preview models off and cross-region data moving off.
If you're a developer in a highly regulated industry environment, you may need to stick to General Availability (GA) models unless you get clearance to use preview models (OpenAI) or external preview models (Anthropic).
🔠 Response Formatting
Once you've sorted out what your agent will say by picking the right model and providing good instructions, the next focus is how the answer should look when delivered to the user.

Response Formatting in Copilot Studio refers to defining the style and structure of the AI's replies - such as whether text should be bold or italic, if links can be included, or if any dynamic content/expressions should be inserted.

🖼️ Why Response Formatting matters
It's all about readability and user experience. Even the most correct answer can confuse or frustrate a user if it's a blob of unstructured text. By applying consistent formatting, you ensure key information stands out and the answer is easy to scan.

For example,

bold text can highlight an important number or term
lists can break complex instructions into steps
hyperlinks can point the user to additional resources without overcrowding the answer
Additionally, your brand's style or tone should be reflected in formatting choices. For instance, a formal agent might avoid emojis and use bold text for emphasis, while a playful one might use italics to highlight lighthearted or humorous comments.

In Copilot Studio's generative answer node, you can allow or disallow certain formatting in the responses. Let's go through what options exist and how to use them effectively.

🖌️ Available formatting options
Copilot Studio generative answers support a subset of Markdown for rich text. Here are the main formatting elements you can leverage in the AI's responses, and what they do:

Formatting Option	Purpose and Effect	Example Usage
Bold	Makes important words or phrases stand out. Use bold to highlight key information or critical values.	"Your account balance is $1,250." - The amount is bold so it's immediately noticeable.
Italics	Adds subtle emphasis or denot