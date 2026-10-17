# Task Delay Alert System
An automated task monitoring system that detects overdue and completed tasks, sends the appropriate email notifications, and tracks notification status using Google Sheets and Zapier.

## 🎯 Problem

### The Context
Software companies rely on different teams, such as Software Development, Quality Assurance (QA), Design, and Project Management, to complete tasks and deliver projects on time. These teams often depend on each other's work to keep projects moving forward.

### The Problem
Task tracking often depends on employees manually checking spreadsheets to identify overdue tasks and confirm completion. This can cause delayed notifications, missed deadlines, and extra work for team members and managers.

### Why It Matters
Automated task monitoring helps teams identify delays earlier, notify the right people, reduce repetitive manual follow-up, and maintain a more organized record of task notifications.

## 💡 Solution

The Task Delay Alert System is a rule-based automation workflow that monitors task records in Google Sheets and sends email notifications based on task deadlines, completion status, and previous notification records.

### What does the system do?

- Stores tasks, responsible employees, departments, deadlines, and task statuses in Google Sheets.
- Checks task records on a scheduled basis.
- Identifies overdue tasks that are not completed and have not already been notified.
- Sends an overdue alert to the responsible employee.
- Sends a completion notification to the team manager when a task is marked as completed.
- Updates notification fields after successful email delivery through the configured workflow.
- Helps managers review task statuses and identify tasks that may require intervention.

## 👤 Users

**Primary Users:**
- Project managers.
- Team managers.
- Software development teams.
- Quality Assurance (QA) teams.
- Design teams.
- Employees responsible for completing assigned tasks.

**User Need:**

Users need a reliable way to monitor deadlines, receive timely notifications, track completed tasks, and reduce the time spent checking task records manually.

## 🧠 How I Designed the Solution

I followed a process-first engineering approach by analyzing the business problem before designing the automation.

I divided the process into clear steps, identified the required task data, and defined decision rules for overdue and completed tasks.

I designed two separate automation paths:

- **Path A — Overdue Task:** Identifies overdue, incomplete tasks that have not already received an overdue notification.
- **Path B — Completed Task:** Identifies completed tasks that have not already triggered a completion notification.

I also included notification tracking to reduce duplicate emails during subsequent scheduled runs.

The first version uses predefined rules rather than AI because the decisions depend on explicit conditions, such as deadlines, task status, and notification fields.

## ⚙️ How It Works

**Input**

Task records are added or updated in Google Sheets.

↓

**Scheduled Monitoring**

Schedule by Zapier triggers the workflow at predefined intervals.

↓

**Data Retrieval and Validation**

The workflow reads task records and checks deadlines, task statuses, email addresses, and notification fields.

↓

**Decision Logic**

Paths by Zapier directs each task to the appropriate path according to the configured conditions.

↓

**Action**

- Overdue tasks: Gmail sends an alert to the responsible employee.
- Completed tasks: Gmail sends a notification to the team manager.

↓

**Output**

The workflow updates the relevant notification fields in Google Sheets after successful sending, helping prevent repeated notifications and maintain a task monitoring record.

## 🤖 Role of AI

### What does AI do in this solution?

The first version of this project does not require AI.

Instead, it uses predefined conditions and rule-based logic to identify overdue and completed tasks. This approach is suitable because the required decisions depend on structured data rather than interpreting unstructured information.

### What AI Should NOT Do

Since AI is not part of the first version, it does not make task decisions or send notifications.

If AI is introduced in a future version, it should not:
- Invent deadlines or task statuses.
- Change task deadlines automatically.
- Evaluate employee performance without an appropriate process.
- Make disciplinary or other management decisions on behalf of managers.
- Treat a completed status as proof that a task passed QA or received client approval.

## 🔄 Automation

The workflow is designed to automate the following tasks:

- Running periodic task checks through Schedule by Zapier.
- Reading task records from Google Sheets.
- Evaluating task deadlines, completion statuses, and notification history.
- Routing tasks using Paths by Zapier.
- Sending overdue alerts through Gmail.
- Sending completion notifications to the team manager.
- Updating notification fields after successful email sending.
- Processing multiple task records during a scheduled run, subject to the configured Zapier workflow and its capabilities.

## 🗂️ Data

### Input

Each task record may include:

- Task ID or task name.
- Responsible employee.
- Employee email address.
- Department.
- Expected delivery date.
- Current task status.
- Overdue notification status.
- Completion notification status.
- Team manager email address.

### Output

- Overdue email alerts.
- Task completion email notifications.
- Updated notification status fields in Google Sheets.
- A structured task record that supports monitoring and follow-up.

The workflow depends on accurate source data, including deadlines, statuses, and email addresses.

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Google Sheets | Stores task details, deadlines, statuses, and notification tracking fields. |
| Zapier | Connects the tools and executes the automation workflow. |
| Schedule by Zapier | Triggers periodic task monitoring. |
| Paths by Zapier | Routes tasks according to predefined conditions. |
| Gmail | Sends overdue alerts and completion notifications. |

## 🔑 Key Design Decisions

### Decision 1: Use Rule-Based Automation Instead of AI

**Decision:**

Use predefined conditions to identify overdue and completed tasks.

**Why:**

The required decisions are based on structured information and explicit business rules. AI would add unnecessary complexity to the first version.

### Decision 2: Separate Overdue and Completed Tasks into Two Paths

**Decision:**

Create separate paths for overdue alerts and completion notifications.

**Why:**

Each situation requires a different recipient, message, and set of conditions. Separating the paths makes the workflow easier to understand, maintain, and test.

### Decision 3: Track Notification Status

**Decision:**

Use fields such as `Overdue Notified` and `Completion Notified` to record whether the relevant notification has been sent.

**Why:**

Without notification tracking, the scheduled workflow could send the same email repeatedly. Tracking notification status helps reduce duplicate notifications.

### Decision 4: Keep Human Oversight

**Decision:**

Allow managers to review task records and handle cases that require intervention.

**Why:**

The system supports monitoring and communication but should not replace management judgment or make decisions about employee performance.

## 🧪 Testing

The following test cases are based on the project's success criteria. Actual results must be recorded after testing the implemented workflow.

### Test 1: Overdue and Incomplete Task

**Input:**

A task has a deadline in the past, its status is `In Progress`, and `Overdue Notified` is `No`.

**Expected Result:**

The system identifies the task as overdue, sends an email to the responsible employee, and updates `Overdue Notified` after successful sending.

**Actual Result:** Pending execution.

**Status:** ⏳ Not tested.

### Test 2: Completed Task

**Input:**

A task has the status `Completed`, and `Completion Notified` is `No`.

**Expected Result:**

The system sends a completion notification to the team manager and updates `Completion Notified` after successful sending.

**Actual Result:** Pending execution.

**Status:** ⏳ Not tested.

### Test 3: Prevent Duplicate Notifications

**Input:**

An overdue task has `Overdue Notified` set to `Yes`.

**Expected Result:**

The system does not send another overdue alert during the next scheduled run.

**Actual Result:** Pending execution.

**Status:** ⏳ Not tested.

### Test 4: Completed Task Past Its Deadline

**Input:**

A task has a past deadline but its status is `Completed`.

**Expected Result:**

The system does not send an overdue alert. If its completion notification has not been sent, it follows the completion path instead.

**Actual Result:** Pending execution.

**Status:** ⏳ Not tested.

### Test 5: Multiple Tasks in One Run

**Input:**

Google Sheets contains multiple tasks with different deadlines, statuses, and notification values.

**Expected Result:**

Each task is evaluated against the configured conditions, and the appropriate actions are performed for each eligible record.

**Actual Result:** Pending execution.

**Status:** ⏳ Not tested.

## 📸 Evidence

### Final Result

Add a screenshot of the Google Sheets task tracker showing task names, assigned employees, deadlines, statuses, and notification fields.

If available, include an example of a successfully sent overdue alert and a completion notification.

### Workflow

Add screenshots of the Zapier workflow showing:

- Schedule by Zapier trigger.
- Google Sheets task retrieval.
- Task condition checks.
- Paths for overdue and completed tasks.
- Gmail notification actions.
- Google Sheets notification status updates.

Additional evidence can include successful Zapier test runs and updated task records.

## ⚠️ Challenges & Failures

### What didn't work as expected?

No implementation failures have been confirmed in the provided project description.

Potential challenges to investigate during testing include:

- Ensuring that all relevant spreadsheet rows are processed.
- Comparing deadlines and current dates correctly.
- Preventing duplicate emails during repeated scheduled runs.
- Updating the correct task row after sending a notification.
- Handling missing email addresses or invalid task data.
- Ensuring that completed tasks are not incorrectly treated as overdue.

### How did I solve it?

These challenges require verification during implementation. Possible solutions include:

- Testing the workflow with multiple task records and different statuses.
- Defining explicit routing conditions for each path.
- Tracking notification status in separate fields.
- Checking that each update targets the correct spreadsheet row.
- Adding validation and error-handling steps for missing or invalid data.
- Updating notification fields only after the email action succeeds.

These are proposed solutions, not confirmed fixes for issues already encountered.

## 📚 What I Learned

### Technical Lesson

How to connect Google Sheets, Schedule by Zapier, Paths by Zapier, and Gmail to create a rule-based task monitoring workflow.

### Problem-Solving Lesson

How to analyze a business process, break it into smaller steps, define decision rules, and design separate paths for different business situations before implementing automation.

### AI Lesson

Not every automation problem requires AI. When the process relies on structured data and clear conditions, rule-based automation can be a simpler and more predictable solution.

## 🔮 Future Improvements

If I continued developing this project, I would:

- Add error logging for failed notifications and spreadsheet updates.
- Add validation for missing deadlines and invalid email addresses.
- Introduce escalation notifications for tasks that remain overdue.
- Add configurable reminders before deadlines.
- Create a dashboard summarizing overdue, completed, and pending tasks.
- Track workflow execution results and notification failures.
- Add more advanced monitoring and reporting for project managers.

## 🔗 Project Links

**Live Demo:** [Add link if available]

**Workflow:** 

**Repository:**(https://github.com/baraa-abuwatfa/Automation-Projects-WAC/tree/efb77510430823b377382dea80962f2026a0f820/Project1)

## 👩‍💻 Author

**Baraa Abu Watfa**

 AI & Automation
Linked in 
http://www.linkedin.com/in/baraa-abuwatfa
Github
https://github.com/baraa-abuwatfa
