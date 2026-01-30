# Mission 08: Enhanced Prompts with Dataverse Grounding

## Summary

**Mission Overview:**
Mission 08 (Operation Grounding Control) teaches how to enhance custom prompts with Dataverse grounding for real-time data access. The mission duration is approximately 60 minutes and builds upon Mission 07. Transforms agents from static responders with hardcoded knowledge to dynamic, data-driven systems that adapt to changing business needs by accessing live organizational data.

**Core Objectives:**
- Understanding how Dataverse grounding enhances custom prompts
- Knowing when to use data grounding vs static instructions
- Designing prompts that dynamically incorporate live data
- Enhancing the Summarize Resume flow with job role matching
- Creating job applications based on AI-suggested role matches

**The Problem with Static Prompts:**

Current limitation: Prompts operate with fixed instructions that require manual updates
```
Match this candidate to these job roles: Developer, Manager, Analyst
```

With Dataverse grounding:
```
Match this candidate to available job roles from the Job Roles table,
considering current evaluation criteria and requirements
```

**Why Dataverse Grounding Matters:**

Four key benefits:
1. **Dynamic updates:** Job roles and criteria change without prompt modifications
2. **Consistency:** All agents use the same current data sources
3. **Scalability:** New roles and criteria are automatically available
4. **Accuracy:** Real-time data ensures decisions reflect current needs

**How Dataverse Grounding Works:**

When enabled for a custom prompt:
1. **Data selection:** Choose specific Dataverse tables and columns to include; can select related tables that system filters based on parent records retrieved
2. **Context injection:** Prompt automatically includes retrieved data in prompt context
3. **Intelligent filtering:** System includes only data relevant to current request if filtering provided
4. **Structured output:** Prompt can reference retrieved data and reason about records to create output

**Transformation: From Static to Dynamic Intelligence**

*Current Static Approach (Mission 07):*
- Hardcoded evaluation criteria
- Predetermined matching logic
- Works but requires manual updates for new job roles, criteria changes, or priority shifts

*Dataverse Grounding Transformation:*
- Access current job roles from Job Roles table
- Use live evaluation criteria instead of static descriptions
- Provide accurate matches based on real-time requirements
- Automatically incorporate new data without prompt modifications

**Why Dedicated Prompts vs Agent Conversations:**

In Mission 03, Interview Agent could match candidates but required complex user prompts:
```
Upload this resume, then show me open job roles,
each with a description of the evaluation criteria,
then use this to match the resume to at least one suitable
job role even if not a perfect match.
```

**Comparison: Agent Conversations vs Dedicated Prompts**

| Aspect | Agent Conversations | Dedicated Prompts |
|--------|---------------------|-------------------|
| Consistency | Results vary based on user's prompt crafting skills | Standardized processing every time |
| Specialization | General-purpose reasoning may miss business nuances | Purpose-built with optimized business logic |
| Automation | Requires human interaction and interpretation | Triggers automatically with structured JSON output |

**Understanding Record Retrieval Settings (Critical Concept):**

*What is record retrieval?*
- Determines maximum number of records prompt can retrieve from Dataverse knowledge sources (tables) and include in prompt context sent to AI model

*Configuration Settings:*
- **Default limit:** 30 records
- **Maximum limit:** 1,000 records
- Suitable for most scenarios with proper filtering

*Critical Understanding:*
- Each record retrieved consumes tokens from model's context window
- Directly impacts cost, processing time, and response quality
- Dataverse grounding NOT designed to process large datasets directly in prompt
- Even increasing to 1,000 may not be right answer if working with thousands of records

**Key Strategy: Use Filtering Strategically**

Narrow dataset BEFORE it reaches AI model:
- Filter by status (e.g., "Active" job roles only)
- Filter by date ranges
- Filter by categories
- Filter by other relevant criteria
- Ensure only most pertinent records included

**Lab Exercise: Add Dataverse Grounding to Prompts**

Upgrade resume analysis capabilities by enhancing existing Summarize Resume flow with dynamic job role matching.

**Lab 8.1 - Examine Dataverse Tables:**

*Job Roles Table - Key Columns:*
| Column | Purpose |
|--------|---------|
| Job Role Number | Unique identifier for role matching |
| Job Title | Display name for the role |
| Description | Detailed role requirements |

Also review Evaluation Criteria table for grounding.

**Lab 8.2 - Add Dataverse Grounding Data to Prompt:**

*Enhanced Prompt Structure:*

1. **Extract Candidate Details:**
   - Full name
   - Email address

2. **Analyze Resume and Cover Letter:**
   - Review resume for skills, experience, qualifications
   - Review cover letter for motivation and suitability

3. **Match Against Open Job Roles:**
   - Compare candidate info with requirements/descriptions of open job roles
   - Use job descriptions to assess potential fit
   - Identify all roles aligning with candidate's profile (don't need perfect suitability)
   - Provide reasoning for each match based on specific job requirements

4. **Create Candidate Summary:**
   - Candidate name
   - Role(s) applied for if present
   - Contact and location
   - One-paragraph summary
   - Top skills (8-10)
   - Experience snapshot (last 2-3 roles with outcomes)
   - Key projects (1-3 with metrics)
   - Education and certifications
   - Availability and work authorization

*Enhanced JSON Output Format:*
```json
{
  "CandidateName": "string",
  "Email": "string",
  "MatchedRoles": [
    {
      "JobRoleNumber": "ppa_jobrolenumber from grounded data",
      "RoleName": "ppa_jobtitle from grounded data",
      "Reasoning": "Detailed explanation based on job requirements"
    }
  ],
  "Summary": "string"
}
```

*Dataverse Grounding Configuration:*

**Job Roles Table:**
- Columns: Job Role Number, Job Title, Description
- Filter: Status = "Active"
- Access via: + Add content → Dataverse → Job Role

**Related Evaluation Criteria:**
- Access via: Job Roles → Job Role (Evaluation Criteria)
- Columns: Criteria Name, Description
- **Critical:** Select related Evaluation Criteria by first selecting Job Role, then navigating to Job Role (Evaluation Criteria) - ensures only related records for Job Role loaded

**Prompt Settings:**
- Record retrieval: 1000 (allows maximum Job Roles and Evaluation criteria)

**Lab 8.3 - Test Enhanced Prompt:**

*Testing Process:*
1. Upload sample resume from Mission 07
2. Select Test
3. Verify JSON output includes MatchedRoles
4. Select "Knowledge used" tab to see Dataverse data merged with prompt before execution
5. Save updated prompt

*Result:* System automatically includes Dataverse data when Summarize Resume Agent Flow calls prompt.

**Lab 8.4 - Add Job Application Agent Flow:**

Purpose: Allow Application Intake Agent to create Job Applications based on suggested roles; agent calls tool for each suggested job role candidate interested in.

*Agent Flow Structure:*

1. **When an agent calls the flow (Trigger):**
   - Input: ResumeNumber (Text) - MUST start with letter R
   - Input: JobRoleNumber (Text) - MUST start with letter J

2. **Get Resume (List rows - Dataverse):**
   - Table: Resumes
   - Filter: `ppa_resumenumber eq 'ResumeNumber'` (replace with trigger parameter)
   - Row count: 1

3. **Get Job Role (List rows - Dataverse):**
   - Table: Job Roles
   - Filter: `ppa_jobrolenumber eq 'JobRoleNumber'` (replace with trigger parameter)
   - Row count: 1

4. **Add Application (Add a new row - Dataverse):**
   - Table: Job Applications
   - Candidate: `concat('ppa_candidates/',first(outputs('Get_Resume')?['body/value'])?['_ppa_candidate_value'])`
   - Job Role: `concat('ppa_jobroles/',first(outputs('Get_Job_Role')?['body/value'])?['ppa_jobroleid'])`
   - Resume: `concat('ppa_resumes/', first(outputs('Get_Resume')?['body/value'])?['ppa_resumeid'])`
   - Application Date: `utcNow()`

5. **Respond to the agent:**
   - Output: ApplicationNumber (Text)
   - Value: Add Application → Application Number
   - Description: "The [ApplicationNumber] of the Job Application created"

*Flow Details:*
- Name: "Create Job Application"
- Description: "Creates a new job application when given [ResumeNumber] and [JobRoleNumber]"

**Lab 8.5 - Add Create Job Application to Agent:**

*Tool Configuration:*
- Add tool: Flow → Create Job Application
- Description: "Creates a new job application when given [ResumeNumber] and [JobRoleNumber]"
- When this tool may be used: "Only when referenced by topics or agents"

**Lab 8.6 - Define Agent Instructions:**

*Enhanced Instructions for Application Intake Agent:*

**3. Post Resume Upload:**
- Respond with formatted bullet list of [SuggestedJobRoles] candidate could apply for
- Use format: [JobRoleNumber] - [RoleDescription]
- Ask user to confirm which Job Roles to create applications for
- When user confirms [JobRoleNumber]s, move to next step

**4. Post Upload - Application Creation:**
- After user confirms which [SuggestedJobRoles] for specific [ResumeNumber]:
  - Examples: "Apply [ResumeNumber] for the Job Roles [JobRoleNumber], [JobRoleNumber], [JobRoleNumber]"
  - "apply to all suggested job roles" - implies use all [JobRoleNumbers]
- Loop over each [JobRoleNumber] and send with [ResumeNumber] to /Create Job Application
- Summarize Job Applications Created

**Strict Rules (must never be broken):**
1. The only valid identifiers are:
   - ResumeNumber (ppa_resumenumber) → format R#####
   - CandidateNumber (ppa_candidatenumber) → format C#####
   - ApplicationNumber (ppa_applicationnumber) → format A#####
   - JobRoleNumber (ppa_jobrolenumber) → format J#####
2. Never guess or invent these values
3. Always extract identifiers from current context (conversation, data, or system output)

**Generative Orchestration Magic:**
These instructions use generative orchestration's ability to iterate over multiple rows when making decisions about steps and tools. Matched Job Roles automatically read and Application Intake Agent runs for each row - "Welcome to the magical world of generative orchestration!"

**Lab 8.7 - Test Your Agent:**

*Testing Workflow:*

1. Upload sample resume and type:
   ```
   This is a new resume for the Power Platform Developer Role.
   ```

2. Agent provides list of Suggested Job Roles with Job Role numbers

3. Confirm which roles to apply for:
   - "Apply for all of those job roles"
   - "Apply for the J10009 Power Platform Developer role"
   - "Apply for the Developer and Architect roles"

4. Create Job Application tool runs for each specified job role

5. Verify in Activity map: See Create Job Application tool run for each Job Role

**Key Technical Nuances:**

1. **Related table selection is critical:** Must select Evaluation Criteria via Job Roles → Job Role (Evaluation Criteria) path, NOT directly selecting Evaluation Criteria table - ensures proper filtering to related records only

2. **Record retrieval defaults to 30:** Must explicitly increase to 1000 if expecting many job roles - but always prefer filtering over increasing limit

3. **Filtering prevents token waste:** Active status filter ensures only current job roles included, saving tokens and improving response quality

4. **MatchedRoles array in JSON:** New field added to output structure - enables structured processing of multiple role matches

5. **Concat expressions for lookups:** Dataverse lookup fields require concat with table prefix (`ppa_candidates/`, `ppa_jobroles/`, `ppa_resumes/`)

6. **Generative orchestration looping:** Agent automatically iterates over multiple [JobRoleNumber]s without explicit loop syntax - AI understands intent and executes multiple tool calls

7. **Identifier format validation:** Strict format requirements (R#####, J#####, C#####, A#####) prevent data corruption from invented values

8. **Knowledge used tab visibility:** Critical for debugging - shows exact Dataverse data merged into prompt context before AI processing

9. **Filter attribute parameter:** Must use exact column name for filtering (e.g., "Status" not "status" or "StatusCode")

10. **Prompt parameter preservation:** When adding Dataverse grounding, must ensure existing Resume and CoverLetter parameters remain intact

**Best Practices for Dataverse Grounding:**

1. **Start with filtering:** Always filter at Dataverse level before retrieval (status, dates, categories)
2. **Select minimal columns:** Only include columns needed for prompt reasoning - reduces token consumption
3. **Use related tables strategically:** Related table selection automatically filters to parent records
4. **Test with "Knowledge used" tab:** Verify correct data being retrieved before full testing
5. **Set appropriate record limits:** Balance between completeness and token efficiency
6. **Provide clear JSON structure:** Define exact field names and data types in output format
7. **Include reasoning fields:** MatchedRoles array includes Reasoning field for explainability
8. **Handle empty results:** Prompt instructions include guidance for when no matches found
9. **Use consistent naming:** Match Dataverse column names in prompt instructions and JSON output
10. **Document identifier formats:** Strict Rules section prevents common errors with invented IDs

**Integration Architecture:**

```
User uploads resume → Summarize Resume Agent Flow runs
    ↓
Flow runs Summarize Resume prompt with Dataverse grounding
    ↓
Prompt retrieves active Job Roles + related Evaluation Criteria from Dataverse
    ↓
AI matches resume to job roles using live data
    ↓
Returns JSON with CandidateName, Email, MatchedRoles[], Summary
    ↓
Agent displays suggested job roles with Job Role Numbers
    ↓
User confirms which roles to apply for
    ↓
Agent loops over each confirmed JobRoleNumber
    ↓
For each: Create Job Application Agent Flow runs
    ↓
Creates Job Application record in Dataverse linking Resume, Candidate, Job Role
    ↓
Agent summarizes applications created with Application Numbers
```

**Dynamic Data vs Static Instructions Comparison:**

*Static Approach (Pre-Mission 08):*
- Hardcoded job titles in prompt
- Manual prompt updates when roles change
- No evaluation criteria context
- Generic matching logic
- Requires republishing after every business change

*Dataverse Grounding Approach (Post-Mission 08):*
- Live job roles automatically retrieved
- Zero maintenance when roles added/removed
- Evaluation criteria included for intelligent matching
- Business-specific reasoning based on current requirements
- Self-updating system that stays current

**Developer Gotchas:**

1. **Related table selection path matters:** Selecting Evaluation Criteria directly vs via Job Roles relationship produces different results - always use relationship path
2. **Record retrieval affects all tables:** Setting to 1000 applies to ALL Dataverse sources in prompt - monitor token usage
3. **Filter syntax must be exact:** OData filter syntax - `ppa_resumenumber eq 'Value'` not `ppa_resumenumber = 'Value'`
4. **Lookup field expressions complex:** Concat with table prefix required - `concat('ppa_candidates/', guid)` not just guid
5. **Generative orchestration looping implicit:** No explicit for-each syntax needed - AI infers from instructions
6. **Identifier format validation critical:** One wrong character in format (e.g., "r12345" vs "R12345") breaks flow
7. **Knowledge used tab essential for debugging:** Shows pre-processed context before AI sees it
8. **Prompt changes require flow re-test:** Updating prompt doesn't automatically update cached flow behavior
9. **Empty MatchedRoles handling:** Must provide instructions for zero-match scenario to prevent errors
10. **Status filter prevents retired data:** Without "Active" filter, retired job roles included in matching

**Production Considerations (Beyond This Mission):**

1. **Error handling for missing data:** If Job Role Number doesn't exist, flow should return clear error
2. **Duplicate application prevention:** Check if application already exists before creating
3. **Application status workflow:** Add initial status (e.g., "Submitted") to applications
4. **Notification integration:** Trigger Teams/email notifications when applications created
5. **Audit logging:** Track who created applications and when for compliance
6. **Candidate consent tracking:** Verify candidate authorized application to specific roles
7. **Role capacity checking:** Validate job role hasn't exceeded application limit
8. **Priority-based matching:** Weight job roles by priority or urgency in matching logic
9. **Skill gap analysis:** Include missing skills in reasoning for near-miss candidates
10. **Batch processing optimization:** Group multiple applications in single transaction

**Mission Accomplishments:**

✅ **Dataverse grounding mastery:** Connect custom prompts to live data sources for dynamic intelligence
✅ **Enhanced resume analysis:** Summarize Resume flow accesses real-time job role data and evaluation criteria
✅ **Data-driven decisions:** AI makes intelligent matches based on current business requirements
✅ **Automated application creation:** Streamlined workflow from resume upload to job applications
✅ **Generative orchestration iteration:** AI loops over multiple items without explicit programming

**Connection to Future Missions:**

Techniques learned establish foundation for:
- Advanced knowledge grounding scenarios
- Multi-table relationship navigation
- Complex data filtering strategies
- Automated workflow orchestration
- Intelligent decision-making systems

---

## Verbatim Training Text

🚨 Mission 08: Enhanced prompts with Dataverse grounding
🕵️‍♂️ CODENAME: OPERATION GROUNDING CONTROL
⏱️ Operation Time Window: ~60 minutes

🎯 Mission Brief
Welcome back, Operative. Your multi-agent hiring system is operational, but there's a critical enhancement needed for data grounding - your AI models need real-time access to your organization's structured data to make intelligent decisions.

Currently, your Summarize Resume prompt operates with static knowledge. But what if it could dynamically access your job roles database to provide accurate, up-to-date matches? What if it understood your evaluation criteria without you having to hardcode them?

In this mission, you'll enhance your custom prompt with Dataverse grounding - connecting your prompts directly to live data sources. This transforms your agents from static responders to dynamic, data-driven systems that adapt to changing business needs.

Your mission: integrate real-time job role and evaluation criteria data into your resume analysis workflow, creating a self-updating system that stays current with your organization's hiring requirements.

🔎 Objectives
In this mission, you'll learn:

How Dataverse grounding enhances custom prompts
When to use data grounding vs static instructions
Designing prompts that dynamically incorporate live data
Enhancing the Summarize Resume flow with job role matching
🧠 Understanding Dataverse grounding for prompts
Dataverse grounding allows your custom prompts to access live data from your Dataverse tables when processing requests. Instead of static instructions, your prompts can incorporate real-time information to make informed decisions.

Why Dataverse grounding matters
Traditional prompts work with fixed instructions:


Match this candidate to these job roles: Developer, Manager, Analyst
With Dataverse grounding, your prompt accesses current data:


Match this candidate to available job roles from the Job Roles table,
considering current evaluation criteria and requirements
This approach provides several key benefits:

Dynamic updates: Job roles and criteria change without prompt modifications
Consistency: All agents use the same current data sources
Scalability: New roles and criteria are automatically available
Accuracy: Real-time data ensures decisions reflect current needs
How Dataverse grounding works
When you enable Dataverse grounding for a custom prompt:

Data selection: Choose specific Dataverse tables and columns to include. You can also select related tables that the system will filter based on the parent records retrieved.
Context injection: The prompt automatically includes the retrieved data in the prompt context
Intelligent filtering: The system includes only data relevant to the current request if you provide any filtering.
Structured output: Your prompt can reference the retrieved data and reason about the records retrieved to create the output.
From static to dynamic: The grounding advantage
Let's examine your current Summarize Resume flow from Mission 07 and see how Dataverse grounding transforms it from static to dynamic intelligence.

Current static approach: Your existing prompt included hardcoded evaluation criteria and predetermined matching logic. This approach works but requires manual updates whenever you add new job roles, change evaluation criteria, or shift company priorities.

Dataverse grounding transformation: By adding Dataverse grounding, your Summarize Resume flow will:

Access current job roles from your Job Roles table
Use live evaluation criteria instead of static descriptions
Provide accurate matches based on real-time requirements
🎯 Why dedicated prompts vs agent conversations
In Mission 03, you experienced how the Interview Agent could match candidates to job roles, but required complex user prompts like:


Upload this resume, then show me open job roles,
each with a description of the evaluation criteria,
then use this to match the resume to at least one suitable
job role even if not a perfect match.
While this worked, dedicated prompts with Dataverse grounding offer significant advantages for specific tasks:

Key advantages of dedicated prompts
Aspect	Agent Conversations	Dedicated Prompts
Consistency	Results vary based on user's prompt crafting skills	Standardized processing every time
Specialization	General-purpose reasoning may miss business nuances	Purpose-built with optimized business logic
Automation	Requires human interaction and interpretation	Triggers automatically with structured JSON output
⚙️ Understanding record retrieval settings
When configuring Dataverse grounding for your prompts, it's critical to understand the Record Retrieval setting, which controls how much data is made available to your AI model.

What is record retrieval?
Record retrieval determines the maximum number of records that the prompt can retrieve from your Dataverse knowledge sources (tables) and include in the prompt context sent to the AI model.

Configuring record retrieval: Finding the right balance
While you can retrieve up to 1,000 records from Dataverse, understanding when and how to adjust this setting is critical for optimal prompt performance. The default limit is 30 records and the maximum is 1000, which is suitable for most scenarios with proper filtering. Each record you retrieve consumes tokens from your model's context window, directly impacting cost, processing time, and response quality.

Dataverse grounding is not designed to process large datasets directly in the prompt. Even increasing the limit to 1,000 may not be the right answer if you're working with thousands of records. The key is to use filtering strategically to narrow your dataset before it reaches the AI model. Always filter by status, date ranges, categories, or other relevant criteria to ensure only the most pertinent records are included.

🧪 Lab 8: Add Dataverse grounding to prompts
Time to upgrade your resume analysis capabilities! You'll enhance the existing Summarize Resume flow with dynamic job role matching.

Prerequisites to complete this mission
You'll need to:

Have completed Mission 07 and have your resume analysis system ready
Have downloaded sample resume documents from test Resumes
8.1 Add Dataverse grounding to your prompt
You'll build on the Summarize Resume prompt that you created in Mission 07. Currently it simply summarizes the resume, but now you'll ground it with the job roles as they currently exist in Dataverse, keeping it always current.

First, let's examine the Dataverse tables you'll be grounding with:

Navigate to Power Apps and select your environment using the Environment switcher on the top right of the navigation bar.

Select Tables and locate the Job Roles table

Review the key columns you'll use for grounding:

Column	Purpose
Job Role Number	Unique identifier for role matching
Job Title	Display name for the role
Description	Detailed role requirements
Similarly, review the other tables such as the Evaluation Criteria table.

8.2 Add Dataverse grounding data to your prompt
Navigate to Copilot Studio, and select your environment using the Environment switcher on the top right of the navigation bar.

Select Tools from the left-hand navigation.

Choose Prompt and locate your Summarize Resume prompt from Mission 07.
Select Prompt

Select Edit to modify the prompt, and replace with the enhanced version below:

IMPORTANT

Ensure the Resume and Cover Letter parameters remain intact as parameters.


You are tasked with extracting key candidate information from a resume and cover letter to facilitate matching with open job roles and creating a summary for application review.

### Instructions:
1. **Extract Candidate Details:**
   - Identify and extract the candidate's full name.
   - Extract contact information, specifically the email address.

2. **Analyze Resume and Cover Letter:**
   - Review the resume content to identify relevant skills, experience, and qualifications.
   - Review the cover letter to understand the candidate's motivation and suitability for the roles.

3. **Match Against Open Job Roles:**
   - Compare the extracted candidate information with the requirements and descriptions of the provided open job roles.
   - Use the job descriptions to assess potential fit.
   - Identify all roles that align with the candidate's cover letter and profile. You don't need to assess perfect suitability.
   - Provide reasoning for each match based on the specific job requirements.

4. **Create Candidate Summary:**
   - Summarize the candidate's profile as multiline text with the following sections:
      - Candidate name
      - Role(s) applied for if present
      - Contact and location
      - One-paragraph summary
      - Top skills (8–10)
      - Experience snapshot (last 2–3 roles with outcomes)
      - Key projects (1–3 with metrics)
      - Education and certifications
      - Availability and work authorization

### Output Format

Provide the output in valid JSON format with the following structure:

{
  "CandidateName": "string",
  "Email": "string",
  "MatchedRoles": [
    {
      "JobRoleNumber": "ppa_jobrolenumber from grounded data",
      "RoleName": "ppa_jobtitle from grounded data",
      "Reasoning": "Detailed explanation based on job requirements"
    }
  ],
  "Summary": "string"
}

### Guidelines

- Extract information only from the provided resume and cover letter documents.
- Ensure accuracy in identifying contact details.
- Use the available job role data for matching decisions.
- The summary should be concise but informative, suitable for quick application review.
- If no suitable matches are found, indicate an empty list for MatchedRoles and explain briefly in the summary.

### Input Data
Open Job Roles (ppa_jobrolenumber, ppa_jobtitle): /Job Role
Resume: {Resume}
Cover Letter: {CoverLetter}
In the prompt editor, replace /Job Role by selecting + Add content, selecting Dataverse → Job Role and select the following columns, and then select Add:

Job Role Number

Job Title

Description

TIP

You can type the table name to search.

In the Job Role dialog, select Filter attribute, select Status, and then type Active as the Filter value.
Add Dataverse Grounding

TIP

You can use Add value here to add in an input parameter as well - for example if you had a prompt to summarize an existing record, you could provide the Resume Number as a parameter to filter by.

Next, you'll add the related Dataverse table Evaluation Criteria, by again selecting + Add content, finding Job Roles, and instead of selecting the columns on Job Role, expand Job Role (Evaluation Criteria) and select the following columns, and then select Add:

Criteria Name

Description
Add related evaluation criteria

Completed Prompt parameters and grounding

TIP

It is important to select the related Evaluation Criteria by first selecting the Job Role, and then navigating in the menu to Job Role (Evaluation Criteria). This will ensure that only the related records for the Job Role will be loaded.

Select the three dots (...) in the Instructions pane and select Settings. Adjust the Record retrieval to 1000 - this will allow the maximum Job Roles and Evaluation criteria to be included in your prompt.
Prompt Settings

8.3 Test the enhanced prompt
Select the Resume parameter, and upload a sample resume that you used in Mission 07.

Select Test.

Once the test has run, notice that the JSON output now includes the Matched Roles.

Select the Knowledge used tab, to see the Dataverse data that merged with your prompt before execution.

Save your updated prompt. The system will now automatically include this Dataverse data with your prompt when the existing Summarize Resume Agent Flow calls it.

Matched roles in JSON

8.4 Add Job Application Agent Flow
To allow our Application Intake Agent to create Job Roles based on the suggested roles, we need to create an Agent Flow. The agent will call this tool for each of the suggested job roles that the candidate is interested in.

Agent Flow Expressions

It is very important that you follow the instructions for naming your nodes and entering expressions exactly because the expressions refer to the previous nodes using their name! Refer to the Agent Flow mission in Recruit for a quick refresher!

Inside the Hiring Agent, select the Agents tab, and open the Application Intake Agent child agent.

Inside the Tools panel, select + Add → + New tool → Agent Flow

Select the When an agent calls the flow node, use + Add an input to add the following parameter:

Type	Name	Description
Text	ResumeNumber	Be sure to only use the [ResumeNumber] - it MUST start with the letter R
Text	JobRoleNumber	Be sure to only use the [JobRoleNumber] - it MUST start with the letter J
When an agent calls the flow

Select the + Insert action icon below the first node, search for Dataverse, select See more, and then locate the List rows action.

Rename the node as Get Resume, and then set the following parameters:

Property	How to Set	Value
Table name	Select	Resumes
Filter rows	Dynamic data (thunderbolt icon)	ppa_resumenumber eq 'ResumeNumber' Select and replace ResumeNumber with When an agent calls the flow → ResumeNumber
Row count	Enter	1
Get Resume

Now, select the + Insert action icon below Get Resume, search for Dataverse, select See more, and then locate the List rows action.

Rename the node as Get Job Role, and then set the following parameters:

Property	How to Set	Value
Table name	Select	Job Roles
Filter rows	Dynamic data (thunderbolt icon)	ppa_jobrolenumber eq 'JobRoleNumber' Select and replace JobRoleNumber with When an agent calls the flow → JobRoleNumber
Row count	Enter	1
Get Job Role

Now, select the + Insert action icon below Get Job Role, search for Dataverse, select See more, and then locate the Add a new row action.

Rename the node as Add Application, and then set the following parameters:

Property	How to Set	Value
Table name	Select	Job Applications
Candidate (Candidates)	Expression (fx icon)	concat('ppa_candidates/',first(outputs('Get_Resume')?['body/value'])?['_ppa_candidate_value'])
Job Role (Job Roles)	Expression (fx icon)	concat('ppa_jobroles/',first(outputs('Get_Job_Role')?['body/value'])?['ppa_jobroleid'])
Resume (Resumes)	Expression (fx icon)	concat('ppa_resumes/', first(outputs('Get_Resume')?['body/value'])?['ppa_resumeid'])
Application Date (use Show all)	Expression (fx icon)	utcNow()
Add Application

Select the Respond to the agent node, and then select + Add an output

Property	How to Set	Details
Type	Select	Text
Name	Enter	ApplicationNumber
Value	Dynamic data (thunderbolt icon)	Add Application → See More → Application Number
Description	Enter	The [ApplicationNumber] of the Job Application created
Respond to the agent

Select Save draft on the top right

Select the Overview tab, Select Edit on the Details panel

Flow name:Create Job Application
Description:Creates a new job application when given [ResumeNumber] and [JobRoleNumber]
Save
Select the Designer tab again, and select Publish.

8.5 Add Create Job Application to agent
Now you'll connect the published flow to your Application Intake Agent.

Navigate back to the Hiring Agent and select the Agents tab. Open the Application Intake Agent, and then locate the Tools panel.

Select + Add

Select the Flow filter, and search for Create Job Application. Select the Create Job Application flow, and then Add and configure.

Set the following parameters:

Parameter	Value
Description	Creates a new job application when given [ResumeNumber] and [JobRoleNumber]
Additional details → When this tool may be used	Only when referenced by topics or agents
Select Save
Add Agent Flow to Agent

8.6 Define agent instructions
To create job applications, you need to tell the agent when to use the new tool. In this case, you'll ask the user to confirm which suggested job roles to apply to, and instruct the agent to run the tool for each role.

Move back in to the Application Intake Agent, and then locate the Instructions panel.

In the Instructions field, add the following clear guidance for your child agent to the end of the existing instructions:


3. Post Resume Upload
   - Respond with a formatted bullet list of [SuggestedJobRoles] the candidate could apply for.
   - Use the format: [JobRoleNumber] - [RoleDescription]
   - Ask the user to confirm which Job Roles to create applications for the candidate.
   - When the user has confirmed a set of [JobRoleNumber]s, move to the next step.

4. Post Upload - Application Creation
    - After the user confirms which [SuggestedJobRoles] for a specific [ResumeNumber]:
    E.g. "Apply [ResumeNumber] for the Job Roles [JobRoleNumber], [JobRoleNumber], [JobRoleNumber]
    E.g. "apply to all suggested job roles" - this implies use all the [JobRoleNumbers]
     - Loop over each [JobRoleNumber] and send with [ResumeNumber] to /Create Job Application
     - Summarize the Job Applications Created

Strict Rules (that must never be broken)
You must always follow these rules and never break them:
1. The only valid identifiers are:
  - ResumeNumber (ppa_resumenumber)→ format R#####
  - CandidateNumber (ppa_candidatenumber)→ format C#####
  - ApplicationNumber (ppa_applicationnumber)→ format A#####
  - JobRoleNumber (ppa_jobrolenumber)→ format J#####
2. Never guess or invent these values.
3. Always extract identifiers from the current context (conversation, data, or system output).
Where the instructions include a forward slash (/), select the text following the / and select the Create Job Application tool.

Select Save
Create Job Application Instructions

Iterating over multiple items in Generative Orchestration

These instructions use generative orchestration's ability to iterate over multiple rows when making decisions about which steps and tools to use. The Matched Job Roles will be automatically read and the Application Intake Agent will run for each row. Welcome to the magical world of generative orchestration!

8.7 Test your agent
Open your Hiring Agent in Copilot Studio.

Upload a sample resume into the chat, and type:


This is a new resume for the Power Platform Developer Role.
Notice how the agent provides a list of Suggested Job Roles - each with a Job Role number.
Test results with suggested roles

You can then provide which of these you would like the Resume to be added as a job application for. Examples:


"Apply for all of those job roles"
"Apply for the J10009 Power Platform Developer role"
"Apply for the Developer and Architect roles"
Test results creating job applications

The Create Job Application tool will then be run for each job role you specified. Inside the Activity map, you will see the Create Job Application tool run for each of the Job Roles you asked to create an application for:
Create Job Application in Activity Map

🎉 Mission Complete
Outstanding work, Operative! Operation Grounding Control is now complete. You've successfully enhanced your AI capabilities with dynamic data grounding, creating a truly intelligent hiring system.

Here's what you've accomplished in this mission:

✅ Dataverse grounding mastery
You now understand how to connect custom prompts to live data sources for dynamic intelligence.

✅ Enhanced resume analysis
Your Summarize Resume flow now accesses real-time job role data and evaluation criteria for accurate matching.

✅ Data-driven decis