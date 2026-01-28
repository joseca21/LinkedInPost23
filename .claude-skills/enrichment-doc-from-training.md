# Skill: Create Enrichment Document from Training

**Skill Name:** `enrichment-doc-from-training`

## Purpose
Create a structured markdown document in the enrichment-content folder from verbatim training text.

## Input Required
- Verbatim training text (provided by user)
- Document name/title

## Output Structure
The created markdown document will have exactly 2 sections:

### Section 1: Comprehensive Summary
- Title: "## Summary"
- Content: A comprehensive summary that captures:
  - All key points from the training
  - Important nuances and subtleties
  - Critical details that shouldn't be missed
  - Structured in a clear, digestible format

### Section 2: Verbatim Text
- Title: "## Verbatim Training Text"
- Content: An exact, unmodified copy of the original training text provided

## File Location
All documents created with this skill should be saved to:
```
./enrichment-content/[document-name].md
```

## Process
1. Receive verbatim training text from user
2. Analyze the text to extract key points and nuances
3. Create comprehensive summary in Section 1
4. Copy verbatim text exactly into Section 2
5. Save document to enrichment-content folder
6. Confirm creation with user

## Usage
User invokes this skill by saying:
- "Use skill: enrichment-doc-from-training"
- "Apply enrichment-doc-from-training skill"
- Or simply referencing the skill name in context

## Example Output Format
```markdown
# [Document Title]

## Summary
[Comprehensive summary with key points and nuances]

## Verbatim Training Text
[Exact copy of original training text]
```
