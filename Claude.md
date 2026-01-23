# LinkedIn Post Enrichment Workflow

## Overview

This workflow transforms draft LinkedIn posts into polished, enriched content by combining source material and stylistic patterns from published examples.

**Important**: When writing the final post, always follow the writing guidelines in [skills.md](skills.md). This defines the tone, structure, length, and quality standards for all LinkedIn posts.

## Folder Structure

```
LinkedInPost23/
├── drafts/                  # Place your rough draft posts here
├── enrichment-content/      # Supporting materials to enrich drafts
├── published-examples/      # Your previously published posts for style reference
├── skills.md                # LinkedIn post writing skill & guidelines
└── Claude.md                # This instruction file
```

## Workflow Instructions

### Step 1: Read the Draft

1. Look in the `drafts/` folder for any markdown or text files
2. Identify the core message, topic, and key points the author wants to convey
3. Note any specific requests or directions included in the draft

### Step 2: Gather Enrichment Content

1. Read all materials in the `enrichment-content/` folder
2. These may include:
   - Research articles or summaries
   - Statistics and data points
   - Quotes or expert opinions
   - Case studies or examples
   - Related news or trends
3. Extract relevant facts, insights, and supporting points that align with the draft's topic

### Step 3: Analyze Published Examples for Style

1. Read all posts in the `published-examples/` folder
2. Identify patterns in:
   - **Tone**: Professional, conversational, inspirational, provocative?
   - **Structure**: How are posts organized? Hook, body, CTA?
   - **Length**: Typical word count and paragraph size
   - **Formatting**: Use of line breaks, emojis, bullet points, hashtags
   - **Opening hooks**: How do posts grab attention?
   - **Closing style**: Questions, calls-to-action, reflections?
   - **Voice**: First person, storytelling, direct address to reader?
   - **Signature elements**: Any recurring phrases or patterns?

### Step 4: Create the Enriched Post

**Follow the writing guidelines in [skills.md](skills.md)** for tone, structure, and quality standards.

1. **Preserve the core message** from the original draft
2. **Incorporate relevant enrichment content** to add:
   - Credibility through data/stats
   - Depth through examples or case studies
   - Context through industry trends
3. **Apply the author's style** by matching:
   - The identified tone and voice from published examples
   - Structural patterns
   - Formatting preferences
   - Opening and closing techniques
4. **Apply skills.md standards**:
   - Informative, non-boastful tone
   - ~2,800 characters (max 3,000)
   - British English spelling
   - 7-part structure (hook, context, core idea, practical breakdown, example, reflection, CTA)
   - 3–6 relevant hashtags

### Step 5: Output

1. Present the enriched post ready for LinkedIn (plain text, no markdown headings)
2. Ensure the post meets all skills.md quality checks
3. Optionally highlight what was added from enrichment content
4. Optionally note which stylistic elements were applied from examples

## Usage

To process a draft, simply ask:

> "Enrich my draft post following the Claude.md workflow"

or

> "Process the draft in the drafts folder"

## Tips for Best Results

- **Drafts**: Can be rough notes, bullet points, or partial thoughts - the messier the better to see transformation
- **Enrichment content**: The more relevant material provided, the richer the final post
- **Published examples**: Include 3-5 of your best posts that represent your authentic voice
