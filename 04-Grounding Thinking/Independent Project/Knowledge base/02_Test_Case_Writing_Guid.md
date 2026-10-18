# Test Case Writing Guide

# دليل كتابة حالات الاختبار البرمجية

| | |
|---|---|
| **Project** | QA Knowledge Assistant |
| **Purpose** | Teach the AI assistant how to understand test scenarios and write clear, structured, and verifiable test cases. |
| **Languages** | Arabic and English |

---

## Table of Contents

1. [What Is a Test Case?](#1-what-is-a-test-case)
2. [Test Scenario vs. Test Case](#2-test-scenario-vs-test-case)
3. [Test Case Fields](#3-test-case-fields)
4. [Recommended Test Case Template](#4-recommended-test-case-template)
5. [Example Test Case: Successful Login](#5-example-test-case-successful-login)
6. [Types of Test Cases](#6-types-of-test-cases)
7. [How the AI Assistant Should Handle Missing Information](#7-how-the-ai-assistant-should-handle-missing-information)
8. [Bilingual Terminology](#8-bilingual-terminology)
9. [Quality Checklist](#9-quality-checklist)
10. [Source Authority](#10-source-authority)

---

## 1. What Is a Test Case?

A **Test Case** is a documented set of preconditions, test steps, test data, and expected results used to verify a specific behavior of a software application.

**حالة الاختبار** هي مجموعة من الشروط المسبقة وخطوات الاختبار وبيانات الاختبار والنتائج المتوقعة، تُستخدم للتحقق من سلوك محدد في التطبيق.

A good test case should be:

- Clear and easy to understand.
- Specific and focused on one behavior.
- Repeatable by another tester.
- Verifiable using observable results.
- Based on requirements or documented expected behavior.

> **Important:** Never invent requirements or claim that a test has been executed when no execution evidence exists.

---

## 2. Test Scenario vs. Test Case

### Test Scenario

A Test Scenario describes, at a high level, what should be tested.

It answers: **What should we test?**

Example:

- **Scenario:** Verify that a registered user can log in.
- **السيناريو:** التحقق من قدرة المستخدم المسجّل على تسجيل الدخول.

### Test Case

A Test Case describes the detailed steps, data, and expected results needed to test a scenario.

It answers: **How do we test it, and what should happen?**

Example:

- Enter a registered email.
- Enter the correct password.
- Click the Login button.
- Verify the result against the documented requirement.

One scenario can contain multiple test cases, such as valid login, invalid password, empty fields, and locked accounts.

> **Key difference:** A Test Scenario is a high-level testing idea, while a Test Case is a detailed, executable test procedure.

---

## 3. Test Case Fields

### 3.1 Test Case ID

A unique identifier for each test case.

Examples:

- `TC-LOGIN-001`
- `TC-REG-002`
- `TC-PROFILE-003`

Use a consistent naming convention. If the project has no convention, suggest one and label it as a proposed format.

### 3.2 Title

A short description of the behavior being tested.

Good examples:

- Verify login with valid credentials.
- Verify an error message appears for an incorrect password.
- التحقق من منع إدخال عمر أقل من الحد المسموح.

Avoid vague titles such as "Test Login" or "Check Button".

### 3.3 Preconditions

Conditions that must be true before testing begins.

Examples:

- The application is available.
- A registered test account exists.
- The account is active.
- The tester is on the login page.

If there are no special preconditions, write `None`.

Do not invent account details or setup requirements.

### 3.4 Test Steps

A numbered list of actions performed by the tester.

Example:

1. Open the login page.
2. Enter the registered email.
3. Enter the correct password.
4. Click Login.
5. Observe the result.

Steps should be clear, ordered, and repeatable.

### 3.5 Test Data

The values used during testing.

Example:

- Email: `qa.user@example.com`
- Password: `[valid test password]`

Use fictional test data. Never include real passwords, production secrets, or unnecessary personal information.

If data is unknown, identify it as missing or use a clearly labelled placeholder.

### 3.6 Expected Result

The behavior that should occur, based on a documented requirement or approved specification.

Example:

- The user is authenticated and redirected to the specified dashboard.
- A validation message appears, and the user remains unauthenticated.

Expected results must be specific and observable.

If the expected behavior is unknown, write `Needs clarification` and explain what must be confirmed.

### 3.7 Actual Result

The behavior observed after executing the test.

Examples:

- The dashboard opened successfully.
- The page displayed an error.
- Not executed yet.

> **Important:** Actual Result must not be invented. Before execution, use `Not executed yet`.

### 3.8 Status

The execution status of the test case.

Use these default definitions unless the project has its own approved definitions:

| Status | Definition |
|---|---|
| **Not Run** | The test has not been executed. |
| **Pass** | The actual result matches the expected result. |
| **Fail** | The actual result differs from the expected result. |
| **Blocked** | Testing cannot continue because of an obstacle. |
| **Not Applicable** | The test does not apply to the current scope, with a reason recorded. |

A newly written test case should normally have the status `Not Run`.

> **Never** mark a test as Pass or Fail without execution evidence.

---

## 4. Recommended Test Case Template

```text
Test Case ID:
Title:
Related Requirement:
Preconditions:
Test Steps:
1.
2.
3.

Test Data:
Expected Result:
Actual Result: Not executed yet.
Status: Not Run.
Notes / Evidence:
```

---

## 5. Example Test Case: Successful Login

**Test Case ID:** `TC-LOGIN-001`

**Title:** Verify login with valid credentials.

**Related Requirement:** Registered, active users can sign in using valid credentials. This example requirement must be confirmed against the actual product specification.

**Preconditions:**

- The application is available.
- A registered, active test account exists.
- The tester is on the login page.

**Test Steps:**

1. Enter the registered email.
2. Enter the correct password.
3. Click Login.
4. Observe the result.

**Test Data:**

- Email: `qa.user@example.com`
- Password: `[valid test password]`

**Expected Result:** If the stated requirement is confirmed, the user is authenticated and redirected to the specified post-login page.

**Actual Result:** Not executed yet.

**Status:** Not Run.

**Notes:** Record the actual behavior and supporting evidence after execution.

---

## 6. Types of Test Cases

### Positive Testing

Verifies expected behavior with valid inputs.

Example: Login using valid credentials.

### Negative Testing

Verifies how the application handles invalid inputs or disallowed actions.

Example: Login using an incorrect password.

### Boundary Testing

Checks values at, below, and above a defined limit.

Example: If the minimum allowed age is confirmed as 18, test 17, 18, and 19.

> Never assume a limit that has not been documented.

---

## 7. How the AI Assistant Should Handle Missing Information

When the user asks for a test case but does not provide enough information, the assistant should:

1. Identify what information is available.
2. Create only the parts supported by the available information.
3. Mark missing fields as `Not provided`.
4. Label assumptions clearly.
5. Ask focused clarification questions.
6. Never invent actual results or execution status.
7. Distinguish a proposed test case from an executed test.

**Example:**

**User:** "Test the Save button."

**Expected assistant response:**

> "I can draft a preliminary test case, but I need to know what should be saved and what should happen after clicking Save. Which page or form contains the button?"

If a preliminary test case is useful, mark its expected result as `Needs clarification` and its status as `Not Run`.

---

## 8. Bilingual Terminology

| English | العربية |
|---|---|
| Test Scenario | سيناريو اختبار |
| Test Case | حالة اختبار |
| Preconditions | الشروط المسبقة |
| Test Steps | خطوات الاختبار |
| Test Data | بيانات الاختبار |
| Expected Result | النتيجة المتوقعة |
| Actual Result | النتيجة الفعلية |
| Status | الحالة |
| Requirement | متطلب |
| Evidence | دليل أو إثبات |
| Not Run | لم يُنفّذ |
| Pass | ناجح |
| Fail | فاشل |
| Blocked | متعذّر التنفيذ |
| Needs Clarification | يحتاج إلى توضيح |

---

## 9. Quality Checklist

Before returning a test case, verify:

- [ ] The ID is unique or labelled as a suggestion.
- [ ] The title describes a specific behavior.
- [ ] Preconditions are explicit.
- [ ] Steps are numbered and executable.
- [ ] Test data is provided or marked as missing.
- [ ] The expected result is based on a requirement.
- [ ] The actual result is not invented.
- [ ] The status reflects execution evidence.
- [ ] Assumptions are clearly labelled.
- [ ] The response follows the user's requested language.

---

## 10. Source Authority

This document is a general QA working guide.

If an approved product requirement or team policy conflicts with an illustrative example in this document, follow the applicable approved requirement and explain unresolved conflicts.

---

*End of document*
