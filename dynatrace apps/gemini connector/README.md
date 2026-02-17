# Gemini Connector for Dynatrace Workflows
Unified observability for **pipelines, jobs, stages and PRs** across multiple CI/CD providers (Azure DevOps, GitHub, GitLab, etc.) inside **Dynatrace Platform**.
<img width="1677" height="914" alt="cicd-image-1" src="https://github.com/user-attachments/assets/69897507-f272-4bb1-a17e-d87c8278b201" />

---

## ✨ Features

- **Pipeline view**: status, total time, history, recent runs.
- **Stage/Job view**: start/end, duration, outcome, metadata (pipeline, project/repo).
- **Filters (Filter Bar)**: timeframe, action name/ID, session, status.
- **Pipeline Execution Flamegraph**: hierarchical view of the job execution in that pipeline.
- **OpenPipeline Setup**:
  - Setup wizard for importing and removing OpenPipeline rules
- **Support to Custom CI/CD Providers**:
  - Event description below
- **Supported Technologies**:
  - **Azure Devops**
  - **Gitlab Pipelines**
  - **Github Actions (Workflows)**

---

## 🚀 Install the app on the Dynatrace platform

*CI/CD Observability is available as a Dynatrace app to all customers upon request. Please contact your Dynatrace representative to activate CI/CD Observability for your tenant.*

- Once installed, open the app and navigate to the Setup tab to find your target technology. Follow the instructions to Set up the webhooks on the chosen provider
- Select Import Configuration to import the Openpipeline rules to your environment. Those rules basically translate the incoming webhook events into SDLC Events (OpenTelemetry Standard), which are then consumed by the app.
- Start exploring data
*Note: Filters are only applied after clicking the refresh button to avoid unnecessary queries*

## 🖥️ Using the workflow action
Follow these steps to set up an automated AI analysis workflow in Dynatrace:

### 1. Fetch your data
Create a new workflow and add a task to fetch the data you want analyzed (e.g., logs, events, or metrics).

- *Action:* Add a DQL Query task named execute_dql_query.
- Example Query:


### 2. Data Optimization
To save on token costs and improve response accuracy, use a script to extract only the necessary records before sending them to Gemini.

- Action: Add a Run JavaScript task.
- Code:
```json
import { execution, result } from "@dynatrace-sdk/automation-utils";

export default async function () {
  // Ensure the string matches your DQL task name
  const taskExecutionResult = await result("execute_dql_query");
  return taskExecutionResult['records'];
}
```

### 3. Configure the Gemini Task
Add a new task and search for Gemini.
1
Under Input, click + Create a new connection.
2
Enter a Connection Name, your Model ID, and your API Key (which you can generate here: https://aistudio.google.com/api-keys).
Note: Do not modify the URL unless you are using a custom endpoint.

Click Add item. Your connection should now show up on the Connection dropdown for the task (refresh page if not).
3
4. Set up the Prompt
Prompt: Enter the specific question or instruction for the AI (e.g., "Analyze these logs and suggest a potential root cause").
Name of Task with data to analyze: Enter the exact name of the task from Step 1 (or Step 2 if you used the optimization script).
5. (Optional) Store the AI Response
You can archive Gemini's analysis back into Dynatrace as a log for long-term tracking.

Add a Run JavaScript task.
Use the Dynatrace SDK to ingest the task output as a log, sample code below.
import { execution, result } from "@dynatrace-sdk/automation-utils";
import { logsClient } from '@dynatrace-sdk/client-classic-environment-v2';

export default async function () {
  const taskExecutionResult = await result('gemini_1');

  console.log('print: ', taskExecutionResult.response);
  
  return await logsClient.storeLog({
    body: [
      {
        'content': taskExecutionResult.response,
        'log.source': 'Gemini',
        'type': 'AI Summary',
      }
    ],
    type: 'application/json; charset=utf-8'
  });
}
To view your AI summaries later, run the following in the Logs app:
fetch logs
| filter matchesValue(type, "AI Summary") AND matchesValue(log.source, "Gemini")





















1. Go to your newly installed app **CI/CD Observability**
2. Navigate to Setup tab to find your target techonology. Follow the instructions to **Setup the webhooks on the chosen provider**
3. Click **Import Configuration** to import the Openpipeline Rules to your environement (Those rules basically translate the incoming webhook events into SDLC Events (Opentelemetry Standard), which is then consumed by the App)
  <img width="1681" height="838" alt="cicd-image-4" src="https://github.com/user-attachments/assets/3a143725-c627-44d0-8f59-1b67fb7649fe" />
4. Navigate to CI/CD Observability to start exploring the data.











Prerequisites
Latest stable NodeJS
Latest stable Typescript
Permission to deploy apps in the Dynatrace Environment
Installation
Download zip
Unzip
Modify app.config.json
Change environmentURL to reflect your Dynatrace Environment
Run npx dt-app deploy deploy from a terminal within the project folder.
If successful, you should see a new connector as an option when adding a new task to a Workflow.
