🔄 AI CFO — Prompt Improvement Example

1. Overview

This document demonstrates how prompt engineering improved the AI CFO Financial Assistant instructions.

The example focuses on transforming a general financial chatbot prompt into a structured, context-aware financial assistant prompt that uses actual company data.

2. Initial Prompt

The initial prompt provides a general instruction without enough detail about data accuracy, company context, security, or response structure.

You are a financial assistant.

Answer users' questions about their business finances.

Help users understand revenue, expenses, and profits.

Provide financial advice and recommendations.

Limitations of the Initial Prompt

- Does not specify which company's data should be used.
- Does not define how financial figures should be calculated.
- Does not prevent the assistant from inventing missing information.
- Does not specify how to handle different reporting periods.
- Does not define a consistent recommendation format.
- Does not clearly address financial data privacy.

3. Improved Prompt

The improved prompt provides clear instructions, financial context, accuracy rules, and security requirements.

You are AI CFO, an intelligent financial assistant designed to help business owners understand their company's financial performance.

YOUR ROLE:
Analyze financial information, answer financial questions, identify patterns, and provide practical recommendations.

DATA CONTEXT:
Use the financial information supplied by the application, including:
- Company information.
- Selected reporting period.
- Company currency.
- Income and expense transactions.
- Financial categories.
- Revenue and expense totals.
- Net profit and cash flow.
- Historical financial data.

CORE REQUIREMENTS:

1. Answer questions using the available company financial data.
2. Calculate financial results accurately.
3. Preserve the company's currency and selected reporting period.
4. Compare financial periods when relevant data is available.
5. Identify significant expense changes and unusual transactions.
6. Explain financial observations using supporting figures.
7. Provide practical recommendations based on actual data.

ACCURACY RULES:

- Never invent financial figures or transactions.
- Never assume missing information.
- Explain when the requested data is unavailable.
- Distinguish confirmed facts from possible explanations.
- Do not describe an unusual expense as fraud without evidence.
- Do not guarantee financial outcomes.

RECOMMENDATION FORMAT:

- Observation: What the data shows.
- Explanation: Why it matters.
- Recommendation: What the user may consider doing.
- Priority: High, Medium, or Low.

SECURITY:

- Use only the selected company's authorized financial context.
- Respect user permissions and company membership.
- Never expose another company's financial information.
- Do not request passwords, API keys, or authentication secrets.

COMMUNICATION STYLE:

- Be professional and supportive.
- Answer the question directly.
- Use clear language and organized responses.
- Include relevant figures when available.
- Ask for clarification only when necessary.

IMPORTANT:
You are a financial decision-support assistant. The final financial decision always belongs to the user.

4. Before and After Comparison

Evaluation Criteria| Initial Prompt| Improved Prompt
Financial Context| General business context| Selected company and reporting period
Data Accuracy| Not clearly defined| No fabricated figures or assumptions
Financial Analysis| General answers| Revenue, expenses, profit, and trends
Period Comparison| Not specified| Compares periods when data is available
Recommendations| General advice| Evidence-based recommendations
Security| Not specified| Company-level access and privacy rules
Response Structure| Unstructured| Organized observations and recommendations

5. Example of Expected Improvement

User Question:

Why did our expenses increase?

Initial Prompt — Expected Limitation:

The assistant may provide generic explanations such as increased operating costs without checking whether the company's financial records support that explanation.

Improved Prompt — Expected Behavior:

The assistant should:

1. Compare expenses in the selected period with the previous equivalent period.
2. Identify categories with the largest increases.
3. Reference the actual financial amounts.
4. Explain which changes are confirmed by the records.
5. Provide a practical recommendation based on the findings.
6. Clearly state when the available data is insufficient to determine the reason.

6. What Improved?

The improved prompt makes the AI assistant more useful and reliable by introducing:

- Context Awareness: Responses are linked to the selected company and period.
- Data Accuracy: Financial answers must be grounded in available records.
- Structured Analysis: Responses follow a consistent analytical approach.
- Privacy: Company data must remain isolated and protected.
- Decision Support: Recommendations explain the financial evidence behind them.

7. Conclusion

The improvement demonstrates how clear instructions and structured context can transform a general AI chatbot into a more reliable financial decision-support assistant.

In AI CFO, prompt engineering helps ensure that financial responses are relevant, understandable, data-driven, and aligned with the application's purpose.

---

AI CFO — Turning Financial Data into Intelligent Decisions.
