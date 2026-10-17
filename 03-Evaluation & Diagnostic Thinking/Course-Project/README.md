# TaskBridge
**Turn Unclear Requests into Clear, Actionable Plans**

## 🎯 Problem

### The Context
Freelancers, recent graduates, and early-career professionals often have goals or work requests but may not know how to turn them into clear, organized steps.

### The Problem
Users may struggle to identify the required tasks, set priorities, track progress, and decide what to do next.

Without a clear plan, work can become difficult to organize and manage.

### Why It Matters
A structured planning system helps users understand their goals, organize tasks, focus on priorities, and track their progress.

## 💡 Solution

TaskBridge is a responsive web application that helps users turn work requests and personal goals into organized plans with clear tasks, priorities, and progress tracking.

### What does the system do?

- Allows users to create and manage personal plans.
- Stores a plan's title, description, goal, and optional deadline.
- Allows users to add, edit, delete, and organize tasks.
- Supports High, Medium, and Low task priorities.
- Supports To Do, In Progress, and Done task statuses.
- Calculates progress based on completed tasks.
- Saves plans and tasks in a persistent database.
- Protects user data through authentication and database-level access control.

The main workflow is:

**Goal → Plan → Tasks → Priorities → Status → Progress**

## 👤 Users

**Primary Users:**
- Freelancers managing client requests and projects.
- Recent graduates organizing professional goals.
- Early-career professionals managing their work.
- Individuals who need a clear way to organize personal goals.

**User Need:**

Users need a simple and reliable system to break goals into manageable tasks, set priorities, and track progress in one place.

The first version focuses on individual users and does not include shared plans or team collaboration.

## 🧠 How I Designed the Solution

The system follows a simple structure:

**User → Plans → Tasks**

- Each user can manage multiple plans.
- Each plan can contain multiple tasks.
- Each task belongs to one plan.
- Each plan and its tasks must belong to the same user.
- Deleting a plan should also delete its related tasks.

I separated the application into authentication, plan management, task management, progress tracking, and data access control.

The database design and security rules are important parts of the system, not just the user interface.

## ⚙️ How It Works

1. The user creates an account or signs in.
2. The user opens the My Plans page.
3. The user creates a plan and defines the desired outcome.
4. The user adds tasks and assigns priorities.
5. The user updates task statuses while working.
6. The application calculates progress from completed tasks.
7. The user can return later to review and update saved plans.

### Progress Calculation

Progress is calculated using the following formula:

**Progress Percentage = (Completed Tasks ÷ Total Tasks) × 100**

For example, if a plan contains five tasks and two are completed, progress is 40%.

If a plan has no tasks, its progress should be 0%.

## 🤖 Role of AI

AI is used as an application-building assistant through Lovable.

### What AI does
- Helps generate application structure and interface components from requirements.
- Supports faster development and iteration.
- Helps translate the system requirements into application features.

### What AI does not do
- Generate plans automatically inside the application in the first version.
- Automatically create or complete tasks.
- Replace authentication, database constraints, or security policies.
- Prove that the application is correct or secure without testing.

**Important:** TaskBridge's first version is a planning and task-management application, not an AI plan-generation tool.

## 🔄 Automation and Workflow

The application organizes work through a structured workflow:

**Create Plan → Add Tasks → Set Priorities → Update Status → Track Progress**

When a task's status changes, the displayed progress should reflect the updated number of completed tasks.

This is application logic rather than an external automation integration.

## 🗂️ Data

The application uses two main database tables.

### Plans
Stores:
- Plan ID and user ID.
- Title and description.
- Goal or desired outcome.
- Optional deadline.
- Optional deliverables and next step.
- Creation and update timestamps.

### Plan Tasks
Stores:
- Task ID and related plan ID.
- User ID.
- Task title and optional description.
- Priority and status.
- Task order and creation timestamp.

### Data Protection
- Each plan must be linked to its owner.
- Each task must belong to a valid plan.
- Task ownership must match plan ownership.
- Only allowed priority and status values should be accepted.
- Row Level Security (RLS) should restrict users to their own records.

## 🛠️ Tools & Technologies

- **Lovable:** AI-assisted application development.
- **Supabase Auth:** User authentication.
- **Supabase PostgreSQL:** Persistent data storage.
- **Supabase RLS:** Database-level access control.
- **GitHub:** Source control and project documentation.
- **Responsive Web Technologies:** User interface for different screen sizes.

## 🔑 Key Design Decisions

- **System before screen:** Focus on data structure, relationships, behavior, and security as well as the interface.
- **Relational database:** Separate plans and tasks into related tables.
- **Persistent storage:** Keep user data available after refreshing the page or signing in again.
- **Database-level security:** Enforce access rules through RLS instead of relying only on frontend restrictions.
- **Calculated progress:** Use task statuses to calculate progress consistently.
- **Focused MVP:** Build core planning features before adding AI generation or external integrations.

## 🧪 Testing

The following test cases should be verified against the running application.

### Authentication
- Create an account, sign in, and sign out.
- Confirm that private pages require authentication.

### Plan Management
- Create, view, edit, and delete plans.
- Confirm that users can access only their own plans.

### Task Management
- Add, edit, and delete tasks.
- Change task priority and status.
- Confirm that task values match the allowed database values.

### Progress and Data Persistence
- Confirm that progress updates when a task is completed.
- Confirm that progress decreases when a completed task is changed to another status.
- Confirm that a plan with no tasks displays 0%.
- Refresh the page and confirm that plans and tasks remain saved.
- Sign out and sign in again to verify saved data.

### Security
- Test with at least two different user accounts.
- Confirm that one user cannot read, modify, or delete another user's plans or tasks.
- Confirm that a user cannot attach a task to a plan owned by another user.
- Confirm that deleting a plan also deletes its related tasks.

**Testing status:** These are planned verification steps. Individual tests should be marked as passed only after their behavior has been checked in the actual application.

## 📸 Evidence

Recommended evidence to include after implementation:

- Landing page and authentication screens.
- My Plans page showing the user's plans.
- Create and Edit Plan forms.
- Plan Details page with tasks and progress.
- Task priority and status controls.
- Supabase table structure and RLS policies.
- Test results demonstrating data persistence and user isolation.

## ⚠️ Challenges & Failures

Potential challenges include:
- Maintaining the correct relationship between plans and tasks.
- Calculating progress correctly when task statuses change.
- Handling plans that contain no tasks.
- Keeping frontend values consistent with database constraints.
- Preventing unauthorized access to another user's data.
- Verifying that saved data remains available across sessions.

These are design and testing concerns, not confirmed failures. Actual bugs and fixes should be documented after testing.

## 📚 What I Learned

This project demonstrates the importance of understanding how an application works beyond its visual interface.

Key learning areas include:
- Requirements analysis and system design.
- Relational database design.
- Authentication and access control.
- CRUD operations and data persistence.
- Workflow and progress calculation.
- Functional testing and security validation.
- Using AI-assisted development tools while reviewing and verifying their output.

The main principle is:

**Build the System, Not the Screen.**

AI App Builders can speed up development, but engineers still need to understand, design, direct, evaluate, and improve what AI builds.

## 🔮 Future Improvements

Possible future features include:
- AI-powered plan generation from natural-language goals.
- AI evaluation of plan clarity, completeness, and feasibility.
- External automation integrations.
- Progressive Web App (PWA) support.
- Notifications and reminders.
- Collaboration features for teams.

These features are outside the initial MVP and should be added based on user needs and testing results.

## 🔗 Project Links

- **Database Schema:** `database-schema.md`
- **Lovable Build Prompt:** `lovable-build-prompt.md`

The repository is expected to contain the following files:

- `README.md` — Project overview, requirements, design, technologies, and testing.
- `database-schema.md` — Database tables, relationships, constraints, indexes, RLS policies, and SQL setup.
- `lovable-build-prompt.md` — Instructions for building the application with Lovable.

## 👩‍💻 Author

**Baraa Mahmoud Abu Watfa**
 AI & Automation

