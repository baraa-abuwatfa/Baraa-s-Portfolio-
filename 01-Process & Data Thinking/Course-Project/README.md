# AI Client Intake & Request Routing System
An AI-powered automation system that organizes client requests, checks information completeness, and routes requests to the appropriate next step.

## 🎯 Problem

### The Context
Service companies receive requests from potential clients who want services such as website design, digital marketing, and application development. These requests may vary in detail, clarity, and completeness.

### The Problem
Employees must manually read each request, understand the client's needs, organize the information, check for missing details, and decide what to do next. This repetitive process can consume time and lead to delays or missed information.

### Why It Matters
A structured intake process helps companies handle requests more efficiently, keep information organized, and identify cases that require additional information or human review.

## 💡 Solution

The AI Client Intake & Request Routing System is designed to automate the initial processing of client requests using AI and workflow automation tools.

### What does the system do?

- Receives client requests through an online form.
- Extracts and organizes important information using AI.
- Checks whether the request contains sufficient information for the next step.
- Routes requests according to predefined rules.
- Records request details and processing results in a spreadsheet.
- Identifies unclear or incomplete requests for human review.
- Supports notifications for relevant processing outcomes.

## 👤 Users

**Primary Users:**
- Service-based companies.
- Sales and customer support teams.
- Employees responsible for receiving and reviewing client requests.
- Small businesses that need a more organized intake process.

**User Need:**

Users need a consistent way to collect, understand, organize, and route client requests without manually repeating every initial processing step.

## 🧠 How I Designed the Solution

I followed a process-first engineering approach instead of starting with automation immediately.

First, I analyzed the business problem and the desired outcome. Then, I divided the process into smaller steps, identified the required data, and defined decision rules and exception cases.

Finally, I used this analysis to design an automation workflow that combines AI-based information extraction with rule-based routing and human review.

The design is documented through six stages:

1. Business analysis.
2. Workflow decomposition.
3. Data design.
4. Decision and exception design.
5. Automation design.
6. Zapier implementation and testing.

## ⚙️ How It Works

**Input**

Client submits a request through Google Forms.

↓

**Data Collection**

The request is passed to the automation workflow.

↓

**AI Processing**

AI by Zapier extracts and organizes the relevant information.

↓

**Validation and Decision Logic**

The system checks the available information against predefined rules to identify complete, incomplete, or unclear requests.

↓

**Request Routing**

The request is directed to the appropriate next step based on the decision rules.

↓

**Output**

The request and its processing results are recorded in Google Sheets, and relevant notifications can be sent. Requests requiring clarification or additional judgment are flagged for human review.

## 🤖 Role of AI

### What does AI do in this solution?

- Extracts relevant information from free-text client requests.
- Organizes unstructured messages into predefined fields.
- Helps identify missing or unclear information.
- Produces structured results that can be used by the automation workflow.

### What AI Should NOT Do

- Invent information that the client did not provide.
- Treat missing information as confirmed facts.
- Make unsupported decisions about client needs.
- Automatically resolve unclear or exceptional cases without appropriate review.
- Replace human judgment when a request requires clarification or a business decision.

## 🔄 Automation

The workflow is designed to automate the following tasks:

- Triggering the workflow when a new form response is received.
- Passing request information to the AI processing step.
- Recording structured information and processing results in Google Sheets.
- Applying predefined rules to determine the next action.
- Routing incomplete or unclear cases for human review.
- Sending relevant notifications when the corresponding steps are configured.

## 🗂️ Data

### Input

- Client name and contact information, if collected by the form.
- Requested service.
- Client's description of the project or business need.
- Additional information provided through the form.

### Output

- Structured client request details.
- Extracted service requirements.
- Information completeness status.
- Routing decision or recommended next action.
- Human review status, when needed.
- Processing records stored in Google Sheets.

The exact fields depend on the final form and data design.

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Google Forms | Collect client requests through an online form. |
| Google Sheets | Store request details and processing results. |
| Zapier | Connect the tools and automate the workflow. |
| AI by Zapier | Extract and structure information from client requests. |

## 🔑 Key Design Decisions

### Decision 1: Analyze the Process Before Automating

**Decision:**

Break down the business process and identify its requirements before building the workflow.

**Why:**

Automation should solve a clearly understood problem rather than reproduce an inefficient process.

### Decision 2: Combine AI with Rule-Based Logic

**Decision:**

Use AI to interpret and structure client messages, while predefined rules determine how requests should be routed.

**Why:**

AI can help process different writing styles, while explicit rules make routing decisions easier to understand and test.

### Decision 3: Include Human Review

**Decision:**

Flag incomplete, unclear, or exceptional requests for human review.

**Why:**

Not every request can be processed reliably without clarification. Human review helps prevent unsupported assumptions and inappropriate routing.

### Decision 4: Keep a Record of Processing Results

**Decision:**

Use Google Sheets to maintain structured request records and processing outcomes.

**Why:**

A consistent record makes it easier to review requests, track processing, and identify errors.

## 🧪 Testing

The following are proposed test cases. Actual results and statuses should be completed after running the workflow.

### Test 1: Complete Client Request

**Input:**

A client submits a clear request for website design and provides all required information.

**Expected Result:**

AI extracts the relevant details, the system identifies the request as sufficiently complete, and the request is recorded and routed according to the configured rules.

**Actual Result:** Pending execution.

**Status:** ⏳ Not tested.

### Test 2: Incomplete Client Request

**Input:**

A client submits a request but leaves out a required detail, such as the project objective.

**Expected Result:**

The missing information is identified, and the request is flagged for clarification or human review rather than being treated as complete.

**Actual Result:** Pending execution.

**Status:** ⏳ Not tested.

### Test 3: Unclear Client Request

**Input:**

A client submits a vague message such as, "I need help with my business website."

**Expected Result:**

The system extracts only the information supported by the message and routes the request for clarification or human review if the required details are insufficient.

**Actual Result:** Pending execution.

**Status:** ⏳ Not tested.

### Test 4: Record and Routing Verification

**Input:**

A valid form submission enters the automation workflow.

**Expected Result:**

The request details and processing outcome are recorded correctly, and the configured routing or notification steps are triggered as expected.

**Actual Result:** Pending execution.

**Status:** ⏳ Not tested.

## 📸 Evidence

### Final Result

Add a screenshot of the completed automation workflow and an example of a processed client request.

### Workflow

Add a screenshot of the Zapier workflow showing the trigger, AI processing, decision logic, and configured actions.

### Suggested Additional Evidence

- Google Forms submission example.
- Google Sheets record showing extracted information.
- Example of an incomplete request flagged for review.
- Successful Zapier test results and task history.

## ⚠️ Challenges & Failures

### What didn't work as expected?

The challenges encountered during implementation have not yet been documented. Potential areas to investigate include inconsistent AI extraction, missing form data, incorrect routing, and failures between connected tools.

### How did I solve it?

Document the actual issues encountered during testing and the changes made to resolve them. For example, if AI output does not follow the expected structure, refine the instructions and validate the output before using it in later workflow steps.

*Note: The examples above are potential challenges, not confirmed implementation failures.*

## 📚 What I Learned

### Technical Lesson

How to connect Google Forms, Google Sheets, and AI processing through Zapier to build a structured workflow.

### Problem-Solving Lesson

Why understanding the business process, data requirements, and decision points before implementation leads to a more suitable automation design.

### AI Lesson

AI can help interpret unstructured client messages, but its output needs validation, clear boundaries, and a safe path for handling uncertain cases.

## 🔮 Future Improvements

If I continued developing this project, I would:

- Add stronger validation for missing or incorrectly formatted information.
- Improve error handling and logging for failed workflow steps.
- Add request status tracking and follow-up reminders.
- Introduce a review mechanism for uncertain AI outputs.
- Measure processing time, extraction accuracy, and routing accuracy.
- Expand routing rules to support additional services and business requirements.

## 🔗 Project Links


**Workflow:** 



## 👩‍💻 Author

**Baraa Abu Watfa**

 AI & Automation


