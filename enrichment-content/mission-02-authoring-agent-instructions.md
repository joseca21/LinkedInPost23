# Mission 02: Authoring Agent Instructions

---

## SECTION 1: SUMMARY

This section provides a condensed overview of Mission 02 for quick reference.

### Mission Overview

**Codename:** Operation Secret Directive
**Duration:** ~20 minutes (intel only, no fieldwork)
**Level:** Operative

### Key Objectives

- Master the art of writing agent instructions in Copilot Studio
- Learn to direct agents to use tools, knowledge sources, and collaborate
- Ensure agents act with precision, transparency, and efficiency

### Core Concept

Instructions shape agent behaviour. Small wording choices can dramatically change outcomes. Well-written instructions help agents:
1. Decide which tool, topic, or knowledge source to use
2. Fill in inputs for tools based on context
3. Generate appropriate responses to users

### What to Include in Instructions

| Purpose | Example |
|---------|---------|
| Guide ambiguous choices | "Use FAQ only if not relevant to Hours, Appointments, or Billing" |
| Set guardrails | "Only respond to requests about employee benefits" |
| Hint for tool inputs | "Use email from contact field when drafting emails" |
| Format responses | "Always give order status in table format" |
| Route topics | "Use ticket creation only for creating; use troubleshooting for fixing" |

### Best Practices for Descriptions

1. **Simple, direct language** - Active voice, present tense
2. **Specific and relevant** - Include keywords, differentiate similar tools
3. **Short and informative** - One or two sentences
4. **Unique names** - "Weather Forecast for Tomorrow" not "Weather"
5. **Test for overlap** - Prevent multiple topics invoking together

### Instruction Structure Template

1. Overview - Agent's mission and role
2. Process Steps - Main steps to follow
3. Collaboration Points - When to call other agents/tools
4. Safety and Moderation - Compliance requirements
5. Feedback Loop - How to collect feedback or escalate

### Key Takeaways

- Instructions must be grounded in configured tools/knowledge
- Vague instructions lead to unpredictable results
- Descriptions help the orchestrator choose the right resources
- Always test and refine in the test pane

---

## SECTION 2: VERBATIM CONTENT

This section contains the original source material in its complete form.

---

### 🕵️‍♂️ Mission 02: Authoring Agent Instructions

🕵️‍♂️ CODENAME: OPERATION SECRET DIRECTIVE

⏱️ Operation Time Window: ~20 minutes – intel only, no fieldwork required

#### 🎯 Mission Brief

Agent, your next assignment is Operation Secret Directive, a focused training mission on agent communication and control.

This mission is not a hands-on lab. Instead, it gives you the foundational knowledge you'll need to write clear, effective instructions for your agents in later exercises. You'll learn how well-written instructions influence agent behavior, decision-making, and tool usage, and why small wording choices can dramatically change outcomes.

Your objective is to understand how to author precise, actionable instructions and high-quality descriptions that help agents interpret their role, select the right tools and knowledge sources, and respond accurately to user queries. These skills form the backbone of every successful agent you'll build going forward.

Think of this as advanced training in agent behavior and intent shaping. Just as a field operative relies on clear mission parameters, AI agents depend on carefully crafted instructions to act with clarity, consistency, and purpose in real-world scenarios.

#### 🔎 Objectives

In this mission, you'll learn:

- The art and science of writing agent instructions in Copilot Studio
- How to direct agents to use tools, knowledge sources, and collaborate with other agents
- How to ensure your agents act with precision, transparency, and efficiency

#### 📝 Writing Agent Instructions

Writing effective agent instructions is the key to successful agent behavior. Instructions are used by agents to:

- Decide which tool, topic, or knowledge source to use for a user query or autonomous trigger
- Fill in inputs for any tool based on the available context
- Generate a response to the end user

**How Instructions Work**

Instructions must be grounded in the tools, topics, and knowledge sources configured for your agent. Agents cannot act on instructions for resources they do not have. For example, if you instruct your agent to search a website FAQ, you must add that FAQ as a knowledge source.

You can reference specific tools, topics, variables, or Power Fx expressions using / in your instructions. This helps the agent know exactly what to use and when.

**What to Include in Instructions**

- Add instructions for cases where you want to guide the agent's choices, especially when ambiguity is possible.
- Use instructions to set guardrails, such as restricting topics or specifying response formats.
- Give hints for filling tool inputs, e.g., "Use the email address from the contact field of the lead when helping the user to draft an email."
- Specify how responses should be formatted, e.g., "Always give responses about order status in a table format."
- Use constraints to limit agent actions, e.g., "Only respond to requests about employee benefits."

**Practical Examples**

- "Use the FAQ documents only if the question is not relevant to Hours, Appointments, or Billing."
- "Only use the ticket creation topic for creating tickets; for other requests related to fixing issues, use the troubleshooting topic."
- "Always give responses about order status in a table format."

**Testing and Refining**

- After editing instructions, use the test pane to validate agent behavior.
- Update and publish changes as needed.

**Advanced Guidance**

- Number or bullet list your instructions and specify that they must be followed in order.
- Use markdown formatting for readability and to help generative AI process your instructions.
- If you want your agent to be highly specific, consider creating a topic for that use case.
- Use exact names for tools and topics in instructions to avoid confusion.

**Safety and Moderation**

- Limit what tools the agent should use when referencing knowledge sources.
- Limit what parameters should be used for tools (e.g., only email a specified list of individuals).
- Use instructions to protect against unwanted behavior or content filtering issues.

#### ✍️ Authoring Descriptions for Tools, Topics, and Agents

High-quality descriptions are essential for generative orchestration. Your agent uses these descriptions to select the right tools, topics, and agents to respond to user queries and triggers. Follow these best practices:

**Use Simple, Direct Language:** Avoid jargon, slang, or overly technical terms. Write in active voice and present tense.

**Be Specific and Relevant:** Include keywords related to the functionality and user intent. Make sure descriptions clearly differentiate similar tools or topics to avoid ambiguity.

**Keep It Short and Informative:** Limit descriptions to one or two sentences. Summarize what the tool, topic, or agent does and how it benefits the user.

**Use Unique, Descriptive Names:** Avoid generic names. For example, use "Weather Forecast for Tomorrow" instead of just "Weather".

**List Actions or Considerations:** Use bulleted or numbered lists for clarity when describing multiple features or steps.

**Test for Overlap:** If multiple topics have similar descriptions, your agent may invoke them all. Test and revise to prevent overlap.

**Good and Bad Description Examples**

Good: This topic provides weather information for any location in the world for the next day. It provides the temperature. It doesn't get the current weather for today.

Bad: This tool can answer questions. (Too vague)

#### 🛠️ Best Practices for Instructions and Descriptions

To make your instructions and descriptions truly effective, keep these principles in mind:

- Use active voice and present tense (e.g., "This tool provides weather information").
- Avoid jargon, slang, or unnecessary technical terms unless necessary for the audience.
- Use bulleted or numbered lists to separate actions, features, or considerations.
- Include keywords that match the user's intent and the tool or topic's functionality.
- Ensure distinct names and descriptions for similar resources to avoid confusion and overlap.

#### 🗂️ Example Instruction Structure

When writing instructions, consider the following structure for clarity and completeness:

- Overview: Briefly describe the agent's mission and role
- Process Steps: List the main steps the agent should follow
- Collaboration Points: Indicate when to call other agents or use specific tools
- Safety and Moderation: Include any compliance or safety requirements
- Feedback Loop: Specify how the agent should collect feedback or escalate issues

#### 🎉 Mission Complete

Mission 02 is completed! You now have:

✅ Instruction Mastery: Learned how to write clear, actionable agent instructions

✅ Strategic Guidance: Directed agents to use tools and collaborate effectively

✅ Operational Clarity: Ensured agents act with precision and transparency

You will put your new instruction skills to practice in the upcoming lessons.

Next up is Mission 03: Building multi-agent systems.

#### 📚 Tactical Resources

- 📖 Microsoft Copilot Studio - Authoring Instructions
- 📖 Guidance for Generative Mode

---

*Source: Microsoft Agent Academy - Operative Curriculum, Mission 02*
