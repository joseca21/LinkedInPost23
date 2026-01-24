# Mission 01: Get Started with the Hiring Agent

---

## SECTION 1: SUMMARY

This section provides a condensed overview of Mission 01 for quick reference.

### Mission Overview

**Codename:** Operation Talent Scout
**Duration:** ~45 minutes
**Level:** Operative

### Key Objectives

- Understand the hiring automation scenario and its business value
- Import and configure the hiring management system solution
- Create the Hiring Agent as the central orchestrator

### The Hiring Automation Scenario

A multi-agent system for HR teams that:
- Automatically processes resumes received via email
- Suggests suitable job roles based on candidate profiles
- Creates job applications and interview guides
- Ensures fair and compliant hiring practices
- Collects feedback for improvement

### Multi-Agent Architecture

| Agent | Role |
|-------|------|
| **Hiring Agent** | Central orchestrator, coordinates process, stores data in Dataverse |
| **Application Intake Agent** | Reads resumes, creates job applications |
| **Interview Prep Agent** | Generates interview questions and documents |

### Solution Components

| Component | Type | Purpose |
|-----------|------|---------|
| Candidate | Table | Candidate information |
| Evaluation Criteria | Table | Evaluation criteria for roles |
| Hiring Hub | Model-Driven App | Managing the hiring process |
| Job Application | Table | Job applications |
| Job Role | Table | Job roles |
| Resume | Table | Candidate resumes |

### Lab Summary

1. **Lab 1.1:** Import the pre-configured Operative solution into Copilot Studio
2. **Lab 1.2:** Import sample data (job roles, evaluation criteria) via CSV
3. **Lab 1.3:** Create the Hiring Agent with description "Central orchestrator for all hiring activities"

### Skills Mastered

- Scenario understanding for hiring automation
- Solution deployment and configuration
- Agent creation as central orchestrator

---

## SECTION 2: VERBATIM CONTENT

This section contains the original source material in its complete form.

---

### 🚨 Mission 01: Get started with the Hiring Agent

🕵️‍♂️ CODENAME: OPERATION TALENT SCOUT

⏱️ Operation Time Window: ~45 minutes

#### 🎯 Mission Brief

Welcome, Agent. Your first assignment is Operation Talent Scout - establishing the foundational infrastructure for an AI-powered recruitment system that will transform how organizations identify and hire top talent.

Your mission, should you choose to accept it, is to deploy and configure a comprehensive hiring management system using Microsoft Copilot Studio. You'll import a pre-built solution containing all the necessary data structures, then create your first AI agent - the Hiring Agent - which will serve as the central orchestrator for all future recruitment operations.

This initial deployment establishes the solution that you'll enhance throughout the Agent Academy Operative course. Consider this your base of operations - the foundation upon which you'll build an entire network of specialized agents in subsequent missions.

#### 🔎 Objectives

In this mission, you'll learn:

- About the scenario and gain comprehensive knowledge of hiring automation challenges and solutions
- How to successfully import and configure the fundamentals of a hiring management system
- How to build a hiring agent that is the start of the scenario you're going to build as an Agent Academy Operative

#### 🔍 Prerequisites

Before embarking on this mission, ensure you have:

- Copilot Studio license
- Access to a Microsoft Power Platform environment
- Administrative permissions to create solutions and agents

Prerequisites help:

If you need help getting a Copilot Studio license, please reference the Recruit Course Setup lab which walks you through setting up a Power Platform environment with a Copilot Studio trial.

#### 🏢 Understanding the Hiring Automation Scenario

This scenario demonstrates how a company can use Microsoft Copilot Studio full to improve and automate its hiring process. It introduces a system of agents that work together to handle tasks like reviewing resumes, recommending job roles, preparing interview materials, and evaluating candidates.

**Business Value**

The solution helps HR teams save time and make better decisions by:

- Automatically processing resumes received via email.
- Suggesting suitable job roles based on candidate profiles.
- Creating job applications and interview guides tailored to each candidate.
- Ensuring fair and compliant hiring practices through built-in safety and moderation features.
- Collecting feedback to improve the solution.

**How It Works**

- A central Hiring Agent coordinates the process and stores data in Microsoft Dataverse.
- An Application Intake Agent reads resumes and creates job applications.
- An Interview Prep Agent generates interview questions and documents based on the candidate's background.
- The system can be published to a demo website, allowing stakeholders to interact with it.

This scenario is ideal for organizations looking to modernize their recruitment workflows using AI-powered automation, while maintaining transparency, fairness, and efficiency.

#### 🧪 Lab 1: Setup the Hiring Agent

In this hands-on lab, you'll establish the foundation for your hiring automation system. You'll begin by importing a pre-configured solution that contains all the necessary Dataverse tables and data structure for managing candidates, job positions, and hiring workflows. Next, you'll populate these tables with sample data that will support your learning throughout this module and provide realistic scenarios for testing. Finally, you'll create the Hiring Agent in Copilot Studio, setting up the basic conversational interface that will serve as the cornerstone for all the other features you'll add in future missions.

#### 🧪 Lab 1.1: Import solution

1. Go to Copilot Studio
2. Select the ... in the left navigation and select Solutions
3. Select the Import Solution button on the top
4. Download the prepared solution
5. Select Browse and select the downloaded solution from the previous step
6. Select Next
7. Select Import

NOTE: On success, you will see a green notification bar with the following message when it's done: "Solution "Operative" imported successfully."

Once you see the "imported successfully" message, take a look at what you imported by selecting the display name of the solution (Operative) in the solutions list.

Review the solution and ensure that the following components are imported:

| Display Name | Type | Description |
|--------------|------|-------------|
| Candidate | Table | Candidate information |
| Evaluation Criteria | Table | Evaluation criteria for the role |
| Hiring Hub | Model-Driven App | Application for managing the hiring process |
| Hiring Hub | Site Map | Navigation structure for the Hiring Hub app |
| Job Application | Table | Job applications |
| Job Role | Table | Job roles |
| Resume | Table | Resumes of the candidates |

As the last task for this lab, Select the Publish all customizations button at the top of the page.

#### 🧪 Lab 1.2: Import sample data

In this lab, you will add sample data to some of the tables that you imported in lab 1.1.

**Download the files to import**

- Download the CSV-file with the evaluation criteria
- Download the CSV-file with the job roles

**Import the Job Role sample data**

1. Go back to the solution you just imported in the last lab
2. Select the Hiring Hub Model-Driven App by selecting the checkmark in front of the row
3. Select the Play button at the top

WARNING: You might be prompted to login again. Make sure to do that. After doing that, you should see the Hiring Hub app.

4. Select Job Roles in the left navigation
5. Select the More icon (three dots below each other) in the command bar
6. Select the right arrow next to Import from Excel
7. Select Import from CSV
8. Select the Choose File button, select the job-roles.csv file you just downloaded and then select Open
9. Select Next
10. Leave the next step as is and select Review Mapping
11. Make sure the mapping is correct and select Finish Import

NOTE: This will start an import and you will be able to track progress or finish the process immediately by selecting Done

12. Select Done

This can take a little while, but you can hit the Refresh button to see if the import has succeeded.

**Import the Evaluation Criteria sample data**

1. Select Evaluation Criteria in the left navigation
2. Select the More icon (three dots below each other) in the command bar
3. Select the right arrow next to Import from Excel
4. Select Import from CSV
5. Select the Choose File button, select the evaluation-criteria.csv file you just downloaded and then select Open
6. Select Next
7. Leave the next step as is and select Review Mapping

Now we have to do a bit more work for the mapping. Select the magnifying glass(🔎 icon) next to the Job Role field

8. Make sure Job Title is selected here, and if not - add it
9. Select OK
10. Make sure the rest of the mapping is correct too and select Finish Import

NOTE: This will start an import again and you will be able to track progress or finish the process immediately by selecting Done

11. Select Done

This can take a little while, but you can hit the Refresh button to see if the import has succeeded.

#### 🧪 Lab 1.3: Create the hiring agent

Now you are done with the setup of the prerequisites, it's time for the actual work! Let's add our Hiring Agent first!

1. Go to Copilot Studio and make sure you are in the same environment as where you imported the solution and the data
2. Select Agents in the left navigation
3. Select New Agent
4. Select Configure
5. For Name, enter: Hiring Agent
6. For Description, enter: Central orchestrator for all hiring activities
7. Select the ... next to the Create button on the top right corner
8. Select Update advanced settings
9. As Solution, select Operative
10. Select Update
11. Select Create in the top right corner

This will create the Hiring Agent for you, which you will use throughout this Operative course.

#### 🎉 Mission Complete

Mission 01 is completed! You now have mastered the following skills:

✅ Scenario Understanding: Comprehensive knowledge of hiring automation challenges and the solution you will be building

✅ Solution Deployment: Successfully imported and configured the building blocks of the hiring management system

✅ Agent Creation: Built an hiring agent that is the start of the scenario you're going to build as an Agent Academy Operative

Next up is Mission 02: Agent Instructions

#### 📚 Tactical Resources

- 📖 Microsoft Copilot Studio - Create an agent
- 📖 Microsoft Dataverse Documentation

---

*Source: Microsoft Agent Academy - Operative Curriculum, Mission 01*
