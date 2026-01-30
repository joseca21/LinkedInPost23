# Mission 09: Generate a Candidate Interview Questions Document

## Summary

**Mission Overview:**
Mission 09 (Operation Doc Assembly) teaches how to generate Word documents from prompts using templates and integrate document generation into agents. The mission duration is approximately 45 minutes and builds upon Mission 08. Transforms agents from data analyzers to document creators, enabling automated generation of tailored interview prep documents.

**Core Objectives:**
- Configuring prompts to output to Word documents
- Formatting Word templates to be used in prompts
- Executing prompts from agents via Agent Flows
- Using topics with slot filling for reliable file returns
- Creating structured interview questions based on candidate and job data

**The Document Generation Challenge:**

Previous missions focused on analyzing INPUT documents (multimodal prompts reading PDFs). This mission focuses on generating OUTPUT documents - creating structured Word files from AI analysis.

Use case: When job application added, automate interview document preparation with:
- Applicant key information (name, current role, experience)
- Role information (job title, requirements)
- Unique specific interview questions based on applicant background and role

**Word Template Placeholder Syntax:**

Key concept: Anywhere you want prompt to insert text, add placeholder text wrapped in double curly brackets:
```
{{JobTitle}}
{{CandidateName}}
{{Question1}}
```

Template is basic Word document with 19 identified fields (identified by curly bracket placeholders).

**Why Agent Flow Required for Document Generation:**

Critical understanding: Cannot call prompt directly from agent for document generation.

*Reason:* Currently can't get contentbytes of file (actual file content) and reliably return file item in agent alone. Agent Flow ensures predictable file extraction and return to agent.

**Formula for File Extraction:**
```
binary(outputs('Run_a_prompt')?['body/responsev2/predictionOutput/documentOutput/contentBytes'])
```

This formula necessary to properly extract file from output for agent return.

**Why Topic Required Instead of Agent Instructions:**

Critical limitation: Topic required rather than adding to agent instructions because currently it's the only way to ensure file object returned every time.

Topics provide:
- Reliable file object handling
- Slot filling for parameter extraction
- Structured file return to user

**Slot Filling Concept:**

AI feature in Copilot Studio allowing generative orchestration to identify values to bring into topic automatically.

Example for VarApplicationNumber:
```
Fill with the Job Application Number referenced in the chat. The number always starts with a J followed by at least 4 digits.
```

Language model extracts value from conversation without explicit user format requirements.

**Lab Exercise: Generating Interview Document**

Complete workflow from prompt creation through agent integration with Word document output.

**Lab 9.1 - Create the Prompt:**

*Prompt Name:* Interview Question Document Prep

*Prompt Instructions Structure:*

1. **Extract Candidate Details:**
   - Full name
   - Email address
   - Current or most recent job title
   - Location if present
   - Total years of experience (only if supported by resume dates)

2. **Analyze Job Listing Description:**
   - Must-have requirements
   - Nice-to-have requirements
   - Key responsibilities
   - Required tools and technologies
   - Treat must-have requirements as highest priority

3. **Evaluate Resume Against Job Requirements:**
   - Compare resume content against each must-have requirement
   - For each requirement determine:
     - Evidence level: Strong, Moderate, Weak, or Missing
     - Confidence score from 0-100
     - Supporting evidence using short phrases grounded in resume text only
   - Do NOT infer or invent experience

4. **Assess Overall Candidate Fit:**
   - Top strengths (up to 5)
   - Key gaps (up to 5)
   - Risks or concerns only when supported by missing or unclear evidence
   - Concise one-paragraph summary suitable for recruiter review

5. **Generate Interview Questions (Exactly 10):**
   - Distribute as follows:
     - 5 Core Requirement Questions (most critical must-have requirements)
     - 3 Gap or Clarification Questions (weak, missing, or ambiguous areas)
     - 2 Scenario-Based Questions (derived from key job responsibilities)
   - Avoid generic or culture-only questions unless explicitly required
   - Each question must include:
     - The interview question
     - The job requirement it maps to
   - Questions must be specific, non-duplicative, grounded in provided inputs
   - Produce questions in numbered format (1, 2, 3)

*Input Parameters:*

| Parameter Name | Type | Sample Data |
|----------------|------|-------------|
| ApplicationNumber | Text | Job application number from Job Application table |

*Dataverse Grounding Configuration:*

| Parameter Name | Table Path | Columns | Filter Attribute | Filter Value |
|----------------|------------|---------|------------------|--------------|
| CandidateDetails | Job Application → Candidate (Candidate) | Candidate Name, Email | Application Number | ApplicationNumber parameter |
| ResumeDetails | Job Application → Resume (Resume) | Cover Letter, Resume Number, Resume Title, Summary | Application Number | ApplicationNumber parameter |
| JobDetails | Job Application → Job Role (Job Role) | Description, Job Role Number, Job Title | Application Number | ApplicationNumber parameter |
| Evaluation Criteria | Job Application → Job Role (Job Role) → Job Role (Evaluation Criteria) | Criteria Name, Description, Weighting | Application Number | ApplicationNumber parameter |

*Critical Configuration Steps:*

1. Test with text output first to confirm correct Dataverse data retrieval
2. Change model to **GPT-4.1** (required for multi-modal inputs and outputs)
3. Change Output dropdown to **Document (preview)**
4. Upload Word template via Document settings
5. Verify 19 identified fields recognized
6. Test document generation and download to confirm correct fill
7. Save prompt

**Lab 9.2 - Create Agent Flow to Call Prompt:**

*Why Agent Flow Needed:* Ensures predictable file content extraction and return to agent.

*Agent Flow Structure:*

1. **When an agent calls the flow (Trigger):**
   - Input: ApplicationNumber (Text)
   - Description: "What's the job application number"

2. **Run a prompt:**
   - Prompt: Interview Question Document Prep
   - ApplicationNumber: Map to trigger input ApplicationNumber

3. **Respond to the agent:**
   - Output: InterviewFile (File type)
   - Value: `binary(outputs('Run_a_prompt')?['body/responsev2/predictionOutput/documentOutput/contentBytes'])`
   - Formula required for proper file extraction

*Flow Details:*
- Name: "Doc Prep"
- Description: "Creates an interview prep document and returns to the agent"

**Lab 9.3 - Create the Topic:**

*Why Topic Required:* Currently the only way to ensure file object returned every time (not possible via agent instructions alone).

*Topic Configuration:*

**Topic Name:** Generate Interview Doc

**Topic Trigger Description:**
```
This topic generates an interview prep document with applicant details, role details and interview questions.
```

**Input Variable (Slot Filling):**
- Variable name: VarApplicationNumber
- Description: "Fill with the Job Application Number referenced in the chat. The number always starts with a J followed by at least 4 digits."
- Slot filling enables AI to extract value from conversation automatically

**Topic Nodes:**

1. **Trigger** (with slot filling input)
2. **Add a Tool:** Doc Prep flow
   - ApplicationNumber input: Map to VarApplicationNumber variable
3. **Send a message:**
   - Text: "Here is your interview prep file:"
   - File Content: InterviewFile property from Doc Prep flow
   - File Name: Formula: `Topic.VarApplicationNumber&"InterviewPrep.docx"`

**Testing Command:**
```
Create an interview prep file for job application J1000
```

Expected behavior:
- Calls topic
- Passes application number
- Calls flow
- Returns file
- Downloads interview prep document

**Key Technical Nuances:**

1. **Model requirement for document output:** Must use GPT-4.1 or higher for multi-modal outputs; default models don't support document generation

2. **Double curly bracket syntax:** Word template placeholders must use `{{FieldName}}` format exactly - single brackets or other formats won't work

3. **Binary formula necessity:** `binary(outputs('Run_a_prompt')?['body/responsev2/predictionOutput/documentOutput/contentBytes'])` is required - direct file reference won't reliably extract content

4. **Topic vs agent instructions for files:** Files must be returned via topics - agent instructions alone cannot reliably handle file objects

5. **Slot filling description precision:** Slot filling description must be specific (e.g., "starts with J followed by at least 4 digits") for accurate extraction

6. **Document settings field recognition:** After uploading template, system should recognize exact number of placeholder fields - mismatch indicates syntax errors

7. **Output type change requirement:** Must explicitly change from Text to Document (preview) - not automatic when template uploaded

8. **Formula tab for dynamic file names:** File name must use Formula tab with concatenation - simple text field won't access variables

9. **Variable mapping via ellipsis menu:** Must use ... three dots menu to select variables - typing won't create proper references

10. **Dataverse grounding through relationships:** All grounding goes through Job Application table relationships - direct table access won't have Application Number filter context

**Interview Question Generation Strategy:**

*Distribution Requirements:*
- **5 Core Requirement Questions:** Target must-have requirements (highest priority)
- **3 Gap or Clarification Questions:** Address weak/missing/ambiguous areas (risk mitigation)
- **2 Scenario-Based Questions:** Derived from key job responsibilities (practical assessment)

*Question Quality Requirements:*
- Specific (not generic)
- Non-duplicative (each question unique)
- Grounded in provided inputs (no assumptions)
- Maps to specific job requirement (traceability)
- Numbered format (1, 2, 3)

*Avoided Question Types:*
- Generic questions ("Tell me about yourself")
- Culture-only questions (unless explicitly required by job description)
- Hypothetical scenarios not grounded in job responsibilities

**Resume Evaluation Methodology:**

*Evidence Levels:*
- **Strong:** Clear, direct evidence in resume
- **Moderate:** Some evidence but not comprehensive
- **Weak:** Minimal or indirect evidence
- **Missing:** No evidence found

*Confidence Scoring:*
- 0-100 scale
- Based on resume evidence only
- Do NOT infer or invent experience

*Supporting Evidence:*
- Short phrases only
- Grounded in resume text
- No assumptions or extrapolations

**Candidate Fit Assessment:**

*Top Strengths (up to 5):*
- Evidence-based only
- Must be supported by resume content

*Key Gaps (up to 5):*
- Missing or weak areas relative to must-have requirements
- Not speculation - based on requirement comparison

*Risks or Concerns:*
- Only when supported by missing or unclear evidence
- Not assumptions about candidate

*Summary Paragraph:*
- Concise (one paragraph)
- Suitable for recruiter review
- Balanced view of fit

**Best Practices for Document Generation:**

1. **Test text output first:** Verify Dataverse grounding before adding document template
2. **Use representative template:** Test with actual interview prep format needed
3. **Name placeholders clearly:** `{{CandidateName}}` better than `{{Name}}` for clarity
4. **Verify field count match:** Template fields should match prompt output fields
5. **Test download immediately:** Don't assume document filled correctly - always verify
6. **Use consistent naming:** Variable names, parameters, and placeholders should align
7. **Document formula complexity:** Binary conversion formula is non-obvious - document it
8. **Save often during testing:** Prompt configuration can be lost on errors
9. **Test with multiple application numbers:** Verify grounding works for different records
10. **Check file object in activity map:** Verify topic correctly receives and returns file

**Integration Architecture:**

```
User: "Create interview prep file for J1000"
    ↓
Topic trigger activates (slot filling extracts J1000)
    ↓
Topic calls Doc Prep Agent Flow with ApplicationNumber=J1000
    ↓
Agent Flow runs Interview Question Document Prep prompt
    ↓
Prompt uses Dataverse grounding to retrieve:
  - Candidate details (via Job Application → Candidate)
  - Resume details (via Job Application → Resume)
  - Job details (via Job Application → Job Role)
  - Evaluation criteria (via Job Application → Job Role → Evaluation Criteria)
    ↓
Prompt analyzes data and generates:
  - Candidate evaluation
  - 10 structured interview questions
  - Fills Word template with 19 fields
    ↓
Agent Flow extracts contentBytes using binary() formula
    ↓
Agent Flow returns InterviewFile to Topic
    ↓
Topic sends message with file attachment
    ↓
User downloads J1000InterviewPrep.docx
```

**Dataverse Relationship Navigation:**

Critical pattern: All data accessed through Job Application table relationships ensures proper filtering context.

```
Job Application (filter: Application Number = J1000)
    ├── Candidate (Candidate details)
    ├── Resume (Resume details)
    └── Job Role
            ├── Job Role details
            └── Evaluation Criteria (related criteria for this job role)
```

**Developer Gotchas:**

1. **Model dropdown easy to miss:** GPT-4.1 selection required but not prominently displayed - easy to forget
2. **Document output not default:** Must explicitly change from Text to Document (preview) - often overlooked
3. **Binary formula syntax sensitive:** Missing parentheses or wrong property path breaks file extraction silently
4. **Topic file return only:** Attempting file return via agent instructions leads to inconsistent behavior
5. **Slot filling description vague:** Generic descriptions like "Application number" don't extract reliably - must be specific
6. **Template field count mismatch:** If recognized fields ≠ expected fields, placeholder syntax errors exist but not clearly shown
7. **Variable mapping confusion:** Typing variable name doesn't work - must use ... three dots menu for proper reference
8. **File name formula requirement:** Using simple text for file name prevents variable access - must use Formula tab
9. **Testing without download verification:** Prompt may succeed but document empty or incorrectly filled - must open file
10. **Dataverse filter context lost:** Accessing tables directly instead of via relationships loses Application Number filter context
11. **Agent flow vs direct prompt call:** Easy to attempt direct prompt call from agent - doesn't work reliably for documents
12. **Output type affects model selection:** Some models support text but not document output - model compatibility matters

**Production Considerations (Beyond This Mission):**

1. **Error handling for missing data:** If Application Number doesn't exist, provide clear error message
2. **Template version control:** Track Word template changes separately from prompt versions
3. **Document storage strategy:** Decide where generated documents stored (SharePoint, Dataverse, OneDrive)
4. **File size limits:** Large templates or extensive content may hit size limits - test with realistic data
5. **Concurrent generation:** Multiple simultaneous requests may affect performance - consider queuing
6. **Document access control:** Ensure generated documents respect organizational security policies
7. **Template customization per role:** Different job roles may need different template formats
8. **Audit trail:** Log which documents generated, when, and by whom for compliance
9. **Template placeholder validation:** Automated testing to verify all placeholders properly filled
10. **Localization support:** Templates may need different languages based on candidate/role location

**Comparison: Mission 07 vs Mission 09:**

| Aspect | Mission 07 (Multimodal Input) | Mission 09 (Document Output) |
|--------|-------------------------------|------------------------------|
| Direction | Analyzing INPUT documents (reading PDFs) | Generating OUTPUT documents (creating Word files) |
| Model | Various models for analysis | GPT-4.1+ required for document generation |
| Output Format | JSON structured data | Word document with formatted content |
| Template | N/A - analyzing existing documents | Required - Word template with {{}} placeholders |
| Agent Integration | Direct tool call possible | Requires Agent Flow for reliable file extraction |
| Use Case | Resume parsing and data extraction | Interview prep document creation |
| Return Type | Structured JSON to agent | File object to topic for user download |

**Mission Accomplishments:**

✅ **Document generation mastery:** Configure prompts to output formatted Word documents
✅ **Template placeholder syntax:** Use {{}} syntax for dynamic content insertion
✅ **Agent Flow file handling:** Extract and return file content reliably via binary() formula
✅ **Topic-based file delivery:** Ensure consistent file object return using topics with slot filling
✅ **Structured interview questions:** Generate 10 targeted questions with proper distribution (5 core, 3 gap, 2 scenario)
✅ **Dataverse grounding integration:** Pull candidate, resume, job, and criteria data via relationships

**Connection to Next Mission:**

Mission 10 will introduce MCP servers for interview meeting scheduling and planning capabilities - extending document generation with external service integration.

---

## Verbatim Training Text

Mission 09: Generate a Candidate Interview Questions Document
🕵️‍♂️ CODENAME: OPERATION DOC ASSEMBLY
⏱️ Operation Time Window: ~45 minutes

🎯 Mission Brief
Welcome, Operative. Your previous missions have shown you the power of prompts. You learned about multimodal document analysis and grounding your prompts with Dataverse data. Now you'll unlock another prompt capability: document generation.

Your assignment, should you choose to accept it, is Operation Doc Assembly. In this operation you'll be creating a word document of interview prep questions from a prompt and calling that from an agent.

🔎 Objectives
In this mission, you'll learn:

How to configure prompts to output to a Word document
How to format a Word template to be used in a prompt
How to execute a prompt from an agent
Lab 9: Generating an Interview Document
When a job application is added, you want to automate the process of preparing a detailed interview document. This should be a Word document that summarizes the applicants key information (name, current role, experience, etc), the role information (job title, requirements) and creates unique specific interview questions based on the applicant background and role they are applying for.

Prerequisites to complete this mission
Before starting this mission you need to:

Have completed Mission 08 and have the agent ready and a good understanding of Dataverse grounding
9.1 Create the prompt
Your first objective: create a prompt capable of analyzing a job description and candidate profile to create tailored interview questions.

Sign in to Copilot Studio and select Tools from the left navigation.Tools Select

Select + New tool buttonNew Tool

Select PromptNew Prompt

Rename the prompt from the default timestamp name (E.g. Custom prompt 09/04/2025, 04:59:11 PM) to Interview Question Document Prep.

Rename

In the Instructions field, add this prompt:


You are tasked with evaluating a candidate's resume against a specific job listing description and generating a targeted set of interview questions to support structured candidate screening.
### Instructions

1. **Extract Candidate Details:**
    - Identify and extract the candidate's full name.
    - Extract contact information, specifically the email address.
    - Identify the candidate's current or most recent job title.
    - Extract location if present.
    - Estimate total years of experience only if supported by resume dates.

2. **Analyze the Job Listing Description:**
    - Review the job description to identify:
    - Must-have requirements
    - Nice-to-have requirements
    - Key responsibilities
    - Required tools and technologies
    - Treat must-have requirements as the highest priority for evaluation.

3. **Evaluate Resume Against Job Requirements:**
    - Compare the resume content against each must-have requirement.
    - For each requirement, determine:
        - Evidence level: Strong, Moderate, Weak, or Missing
        - A confidence score from 0–100
        - Supporting evidence using short phrases grounded in the resume text only
    - Do not infer or invent experience.

4. **Assess Overall Candidate Fit:**
    - Identify:
        - Top strengths (up to 5)
        - Key gaps (up to 5)
        - Risks or concerns only when supported by missing or unclear evidence
        - Provide a concise one-paragraph summary suitable for recruiter review.

5. **Generate Interview Questions (Exactly 10):**
    - Generate exactly 10 interview questions based on the job requirements and resume evaluation.
    - Distribute the questions as follows:
        - 5 Core Requirement Questions focused on the most critical must-have requirements.
        - 3 Gap or Clarification Questions targeting weak, missing, or ambiguous areas.
        - 2 Scenario-Based Questions derived directly from key job responsibilities.
    - Avoid generic or culture-only questions unless explicitly required by the job description.

**Interview Question Requirements:**
    - Each question must include:
        - The interview question
        - The job requirement it maps to
     - Questions must be specific, non-duplicative, and grounded in the provided inputs.
     - Produce questions in numbered format (1, 2, 3)

### Input Data

Application Number:  /ApplicationNumber
Candidate Details (Name, Email): /CandidateDetails
Resume Details: /Resume Details
Job Details (Job Number, Title, Description and Requirements): /JobDetails
Evaluation Criteria (Weighting, Evaluation Criteria): /Criteria
In a new tab, go to make.powerapps.com and find the Job Application table. Take note of one of the job application numbers in that table that you want to use for testing.

Job App Table

Go back to your prompt and scroll down to the input data section of the prompt. Find the /ApplicationNumber text. Delete that and type a forward slash (/) to open up the add input panel and configure the input as follows:

Parameter Name	Type	Sample Data
ApplicationNumber	Text	Enter a job application number you copied from the step previous step
Now that we have an input to pass in the Job Application number, we want to get other relevant information for this prompt from Dataverse using Dataverse Grounding.

TIP

If you want to get an in-depth understanding of Dataverse Grounding, be sure to go through module 8.

To configure Dataverse grounding for our prompt, find the remaining forward slashes in the Input Data section of the prompt and replace according to the table below:

Parameter Name	Table	Columns	Filter attribute	Filter value
CandidateDetails	Dataverse -> Job Application -> Candidate (Candidate)	Candidate Name, Email	Application Number	Add Value -> Application Number
ResumeDetails	Dataverse -> Job Application -> Resume (Resume)	Cover Letter, Resume Number, Resume Title, Summary	Application Number	Add Value -> Application Number
JobDetails	Dataverse -> Job Application -> Job Role (Job Role)	Description, Job Role Number, Job Title	Application Number	Add Value -> Application Number
Evaluation Criteria	Dataverse -> Job Application -> Job Role (Job Role) -> Job Role (Evaluation Criteria)	Criteria Name, Description, Weighting	Application Number	Add Value -> Application Number
The completed input section should look like the screenshot below

Filled Prompt

It's always a good idea to test as you go along. Select Test to see the initial text output from your prompt and confirm it is pulling the correct information from Dataverse.

First Test

Because we want to have this prompt generate a document, we need to change the model the prompt is using to one that supports multi-modal inputs and outputs. To do this, select the model dropdown and change it to GPT-4.1

Model Select

In order to have the prompt populate a Word document as the output, you need a Word template for it to fill. We have provided a template for you to use. Download the template file here and open it.

NOTE

The template itself is a basic Word document. The key thing you need to know is how to add the placeholders for where the prompt will insert the text. Anywhere that you want the prompt to insert text, you need to put the necessary placeholder text for what you want to fill it with and wrap that in double curly brackets {{ JobTitle }} as shown below.

Template

So far we have a prompt that generates a text output. To make it generate a Word document output, select the Output dropdown in the upper right hand corner of the results panel and choose the Document (preview) option.

Output Select

To associate the template file with your prompt, select the Document settings button and either drag and drop the file you downloaded in or choose select to browse.Document Settings

After you upload the file it should recognize that there are 19 identified fields (identified by looking for all those curly bracket placeholders). Select the test button again to see if the prompt outputs to the Word document.

Document Test

You should see a response similar to the following. You'll see a link at the top to download the document. Select that and confirm that it was filled out correctly.

Document Output TestDocument Filled

Click Save to save your new prompt

Save

9.2 Create an agent flow to call the prompt
Now we need to connect the prompt to our agent. To do this, we need to add an agent flow to call the prompt and return the file to the agent.

You might be wondering why we have to do this step rather than calling the prompt directly in the agent. The reason is because currently, we can't get the contentbytes of a file (aka the actual file content) and have that reliably return a file item in the agent alone. The agent flow ensures that we can predictably extract out the file and return it to our agent.

With that out of the way, let's create the agent flow.

In Copilot Studio, select the Tools tabTools Tab

Select the New tool buttonNew tool

Select the Agent Flow optionAgent Flow Button

Click on the When an agent calls the flow trigger to expand it and select the Add an input button

Add Input

Select the Text user input type

Select Input Type

Name the input ApplicationNumber and put What's the job application number as the description

Input Property

Select the + plus button below the when an agent calls the flow trigger and select the Run a prompt action

Add Action

Select the Interview Question Document Prep prompt from the dropdown list

Select the prompt

Click into the ApplicationNumber input and select the lightning bolt icon

Lightning bolt icon

Select the ApplicationNumber input that we created earlier

Map Input

Click to expand the Respond to the agent action and select Add an output

Add Output

Select File from the list of output types

File Type

Name the property InterviewFile. For the value, click the fx icon and enter the following formula then click Add


binary(outputs('Run_a_prompt')?['body/responsev2/predictionOutput/documentOutput/contentBytes'])
Formula

NOTE

This formula is necessary to properly extract the file from the output so we can return it to our agent.

Select Save Draft to save the flow

Save draft

Select the Overview tab

Overview tab

Select the Edit button next to Details

Edit Name

Put Doc Prep in the Flow name and Creates an interview prep document and returns to the agent in the description. Then slick Save

Flow Name

Select the Designer tab

Designer tab

Select the Publish button to publish your flow

Publish

9.3 Create the topic
Now we will tie all of this together with our agent by adding a topic.

A topic is required rather than adding it to the agent instructions because currently, it is the only way to ensure that a file object is returned every time.

Let's create the topic:

Click the Agents tab in Copilot Studio and select the Interview Agent. Select the Topics tab

Topics Tab

Select the Add a Topic button and the From blank option

Add topic

Change the name of the Topic by replacing the "Untitled" name with Generate Interview Doc

Topic Name

In the Topic Trigger, enter the following for the description


This topic generates an interview prep document with applicant details, role details and interview questions.
Topic Description

We need to be able to pass the Job Application Number we want to create the interview prep file for into our topic. To do that, we will use an AI feature in Copilot Studio called slot filling. This allows the generative orchestration of the language model to identify the values to bring into the topic.

To do this, select the Details button in your topic

Details

Select the Input tab in the details panel and select the Create a new variable buttonSelect Input

For the Variable name change it to VarApplicationNumber. For the Description put in


Fill with the Job Application Number referenced in the chat. The number always starts with a J followed by at least 4 digits.
Keep all the other properties the same.Input Filled

Select the + plus icon after the trigger then select Add a Tool and locate and select the Doc Prep flow from the list that we created earlier

Select the flow

Click into the ApplicationNumber input in the action, click the ... three dots and choose the VarApplicationNumber variable to map that to the input

Map Input

Now we need to add a message node to return the file to the user. To do this, click the + plus icon below the action you added and select the Send a message action

Add Message Node

In the textbox, type Here is your interview prep file:. Then click the Add button and choose the File option.

Fill out message

Click in the Content input, select the ... three dots and choose the InterviewFile property

Select File

Click in the Name input, select the ... three dots and select the Formula tab

Formula tab

In the formula window type the following formula and select the Insert button


Topic.VarApplicationNumber&"InterviewPrep.docx"
Formula

Select the Save button to save the topic

Save Topic

Now let's test and make sure our new topic is working. Open up the test panel and type in the following (replace the J1000 number with a relevant job application number in your Job Application table):


Create an interview prep file for job application J1000
Press Enter

Test

Notice how it calls the topic, passes in the application number in, calls the flow and returns the file. Click on the document link and notice how it downloads the interview prep document to your hard drive.

Test Result

Open up the document and make sure that it is filled in correctly

Document

Congratulations! You just successfully added document generation capabilities to your agent!

🎉 Mission Complete
Great work, Operative! Operation Doc Assembly is now complete. You've successfully enhanced your agent with document generating capabilities!

🚀 Next up: In your next mission, you'll learn how to use the power of MCP servers to help add interview meeting scheduling and planning capabilities.

⏩ Move to Mission 10: Integrating with MCP

📚 Tactical Resources
📖 Document output in prompts

📖 Use your own data in a prompt

📖 Create a custom prompt

📖 Work with Dataverse in Copilot Studio

📖 AI Builder custom prompts overview

📖 Training: Create AI Builder prompts using your own Dataverse data

Analytics
Pager
Previous page
Dataverse Grounding
Next page
Integrate with MCP Servers