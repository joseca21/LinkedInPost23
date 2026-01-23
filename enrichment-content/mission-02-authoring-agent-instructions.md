# Mission 02: Authoring Agent Instructions

**Codename:** Operation Secret Directive
**Duration:** ~20 minutes (intel only, no fieldwork required)

## Mission Brief

This mission is focused training on agent communication and control. It provides foundational knowledge for writing clear, effective instructions for AI agents.

The key insight: well-written instructions influence agent behavior, decision-making, and tool usage. Small wording choices can dramatically change outcomes.

The objective is to understand how to author precise, actionable instructions and high-quality descriptions that help agents:
- Interpret their role
- Select the right tools and knowledge sources
- Respond accurately to user queries

Think of this as advanced training in agent behavior and intent shaping. Just as a field operative relies on clear mission parameters, AI agents depend on carefully crafted instructions to act with clarity, consistency, and purpose.

## Learning Objectives

- The art and science of writing agent instructions in Copilot Studio
- How to direct agents to use tools, knowledge sources, and collaborate with other agents
- How to ensure agents act with precision, transparency, and efficiency

## Writing Agent Instructions

Writing effective agent instructions is the key to successful agent behavior. Instructions are used by agents to:

1. **Decide** which tool, topic, or knowledge source to use for a user query or autonomous trigger
2. **Fill in inputs** for any tool based on the available context
3. **Generate a response** to the end user

### How Instructions Work

Instructions must be grounded in the tools, topics, and knowledge sources configured for your agent. Agents cannot act on instructions for resources they do not have.

**Example:** If you instruct your agent to search a website FAQ, you must add that FAQ as a knowledge source.

You can reference specific tools, topics, variables, or Power Fx expressions using `/` in your instructions. This helps the agent know exactly what to use and when.

### What to Include in Instructions

| Purpose | Example |
|---------|---------|
| Guide choices when ambiguity is possible | "Use the FAQ documents only if the question is not relevant to Hours, Appointments, or Billing." |
| Set guardrails | "Only respond to requests about employee benefits." |
| Hints for tool inputs | "Use the email address from the contact field of the lead when helping the user to draft an email." |
| Response formatting | "Always give responses about order status in a table format." |
| Topic routing | "Only use the ticket creation topic for creating tickets; for other requests related to fixing issues, use the troubleshooting topic." |

### Testing and Refining

- After editing instructions, use the test pane to validate agent behaviour
- Update and publish changes as needed
- Iterate based on observed outcomes

### Advanced Guidance

- Number or bullet list your instructions and specify that they must be followed in order
- Use markdown formatting for readability and to help generative AI process your instructions
- If you want your agent to be highly specific, consider creating a topic for that use case
- Use exact names for tools and topics in instructions to avoid confusion

### Safety and Moderation

- Limit what tools the agent should use when referencing knowledge sources
- Limit what parameters should be used for tools (e.g., only email a specified list of individuals)
- Use instructions to protect against unwanted behaviour or content filtering issues

## Authoring Descriptions for Tools, Topics, and Agents

High-quality descriptions are essential for generative orchestration. Your agent uses these descriptions to select the right tools, topics, and agents to respond to user queries and triggers.

### Best Practices

1. **Use Simple, Direct Language:** Avoid jargon, slang, or overly technical terms. Write in active voice and present tense.

2. **Be Specific and Relevant:** Include keywords related to the functionality and user intent. Clearly differentiate similar tools or topics to avoid ambiguity.

3. **Keep It Short and Informative:** Limit descriptions to one or two sentences. Summarise what the tool, topic, or agent does and how it benefits the user.

4. **Use Unique, Descriptive Names:** Avoid generic names.
   - Good: "Weather Forecast for Tomorrow"
   - Bad: "Weather"

5. **List Actions or Considerations:** Use bulleted or numbered lists for clarity when describing multiple features or steps.

6. **Test for Overlap:** If multiple topics have similar descriptions, your agent may invoke them all. Test and revise to prevent overlap.

### Good vs Bad Description Examples

| Quality | Description | Why |
|---------|-------------|-----|
| Good | "This topic provides weather information for any location in the world for the next day. It provides the temperature. It doesn't get the current weather for today." | Specific, clear scope, states limitations |
| Bad | "This tool can answer questions." | Too vague, no context |

## Example Instruction Structure

When writing instructions, consider this structure for clarity and completeness:

1. **Overview:** Briefly describe the agent's mission and role
2. **Process Steps:** List the main steps the agent should follow
3. **Collaboration Points:** Indicate when to call other agents or use specific tools
4. **Safety and Moderation:** Include any compliance or safety requirements
5. **Feedback Loop:** Specify how the agent should collect feedback or escalate issues

## Key Principles Summary

- Use active voice and present tense
- Avoid jargon unless necessary for the audience
- Use bulleted or numbered lists to separate actions, features, or considerations
- Include keywords that match the user's intent and the tool or topic's functionality
- Ensure distinct names and descriptions for similar resources to avoid confusion and overlap

## Skills Mastered

- **Instruction Mastery:** Learned how to write clear, actionable agent instructions
- **Strategic Guidance:** Directed agents to use tools and collaborate effectively
- **Operational Clarity:** Ensured agents act with precision and transparency

## Key Takeaways

1. **Instructions shape behaviour:** The quality of your instructions directly determines how well your agent performs
2. **Grounding is essential:** Instructions only work if the referenced tools/knowledge exist
3. **Specificity prevents errors:** Vague instructions lead to unpredictable outcomes
4. **Testing is critical:** Always validate behaviour in the test pane before publishing
5. **Descriptions matter:** Good descriptions help the orchestrator choose the right resources

---

*Source: Microsoft Agent Academy - Operative Curriculum, Mission 02*
