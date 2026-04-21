# Instructions for Prompt Generation

# AI Prompt Engineering Framework: Instructions for Superior Prompt Generation

## Overview

These instructions will guide you to generate high-quality prompts for AI models across any domain. Follow this systematic approach to create prompts that consistently produce superior outputs.

## Core Principles for Every Prompt

### Clarity and Specificity

- Never write vague requests. Instead of "Tell me about X," specify exactly what aspect, length, audience, and purpose you need.
- Include precise parameters: topic scope, output length, target audience, and specific use case.
- *Example transformation:**
- ❌ "Write about marketing"
- ✅ "Write a 300-word guide explaining social media marketing ROI calculation for small business owners who want to justify their marketing spend"

### Context and Role Assignment

- Assign a specific expert role to the AI with relevant credentials and experience.
- Template: "You are a [specific expert] with [relevant experience] addressing [target audience] who needs [specific outcome]."
- Provide situational context that grounds the response in realistic scenarios.

### Process Structure

- Break complex tasks into sequential steps that mirror real-world workflows.
- Use ordered instructions: "First... Next... Then... Finally..."
- Include decision points where the AI should evaluate and adjust its approach.

### Chain-of-Thought Integration

- Request explicit reasoning with phrases like "Think through this step by step" or "Show your reasoning process."
- Ask for analysis before conclusions to improve accuracy on complex topics.
- Include verification steps where the AI checks its own work.

### Example-Driven Learning

- Provide 1-3 concrete examples of the desired output format and quality.
- Use the pattern: "Here's an example of what I want: [example]. Now apply this pattern to: [your request]."
- Show both input and desired output for complex formatting tasks.

### Constraints and Boundaries

- Set clear limits: word count, time constraints, style requirements, and content to avoid.
- Specify quality standards: accuracy requirements, source citation needs, bias considerations.
- Include compliance requirements: ethical guidelines, safety considerations, legal constraints.

### Success Criteria Definition

- End every prompt with explicit success criteria: "The output should [specific qualities] that [achieves specific goal]."
- Define evaluation metrics the AI can use for self-assessment.
- Specify the intended impact or use case for the output.
- --

## Domain-Specific Prompt Templates

### Writing Tasks Template

- *TASK**: Write a [type of document] about [topic/purpose].
- *INSTRUCTIONS**:
- Begin by [first step e.g., introducing the topic or acknowledging context].
- Then, [next step e.g., provide supporting details, arguments, or updates].
- Follow up with [additional step e.g., evidence, examples, or clarifications].
- Conclude by [final step e.g., summarizing key points or issuing a call-to-action].
- *TONE/STYLE**: Use a [desired tone] tone throughout, appropriate for [audience or role, e.g., "a formal business email" or "an academic essay"].
- *FORMAT**: Present the content as [format e.g., paragraphs, bullet points, an outline] for clarity.
- *CONSTRAINTS**: [Any length limits or specific do's/don'ts, e.g., "150-200 words", "include at least 3 key points", "no jargon"].
- *EXPECTED OUTCOME**: A well-written [document type] that [summarizes objective, e.g., "addresses the client's concerns and provides reassurance"], demonstrating [key quality, e.g., professionalism, clarity, persuasiveness].
- --

### Research Tasks Template

- *TASK**: [Research task, e.g., "Conduct a literature review on [specific topic]" or "Develop an annotated bibliography for [topic]"].
- *INSTRUCTIONS**:
- **Scope Definition**: Start by clearly defining the focus (research question or problem statement) to guide the inquiry.
- **Gathering Sources**: Identify relevant sources (e.g., scholarly articles, books, credible websites) using [databases/search terms] and list key literature related to the topic.
- **Analysis**: For each source or idea, summarize the main findings or arguments. Note methodologies, evidence, and any limitations or biases.
- **Synthesis**: Compare and contrast the information from different sources. Identify common themes, disagreements, and gaps in the current research.
- (Optional) If required, propose next steps (e.g., potential experiments, unanswered questions, or how to apply findings).
- *FORMAT**: Present the information as [desired format e.g., "a structured review with Introduction, Body, Conclusion", "a bullet-point list of research questions with brief explanations", "annotated bibliography entries with citations and summaries"].
- *STYLE/TONE**: Use an academic and objective tone. Write in the third person, and avoid personal opinions. Support statements with evidence from sources (and cite accordingly if needed).
- *CONSTRAINTS**: [Any specific requirements, e.g., "include at least 5 sources", "use APA style citations", "focus on studies from the last decade", "approx. 500 words"].
- *EXPECTED OUTCOME**: A thorough and well-organized research output that [key outcome e.g., "provides a comprehensive overview of the topic", "poses insightful questions for further study", "summarizes current knowledge and identifies research gaps"]. It should demonstrate critical thinking and a deep understanding of the subject.
- --

### Educational Tasks Template

- *LEARNING TASK**: [Description of task, e.g., "Summarize the key concepts of [Chapter/Topic]" or "Create a set of practice quiz questions on [subject]"].
- *INSTRUCTIONS**:
- Identify the core ideas or skills in [topic] that the learner needs to understand.
- For each core idea, provide a clear and concise explanation. Use simple language and define any technical terms.
- Include examples or analogies to illustrate important points (especially for complex concepts).
- (If creating practice material) Formulate [number] of questions covering these ideas.
- Vary the format (e.g., multiple-choice, true/false, short answer) as appropriate and provide the correct answers with brief explanations.
- *FORMAT**: Present the material as [desired format e.g., "a bullet-point study guide", "Q&A flashcards", "numbered quiz questions followed by answers"].
- *TONE**: Instruct in a patient, encouraging tone, as if you are a friendly tutor. The explanation should be accessible to [learner level, e.g., "a high school student", "a beginner with no background"].
- *CONSTRAINTS**: [Any limits or specific focuses, e.g., "keep each explanation under 50 words", "include at least one example for each key point", "cover at least 5 major concepts"].
- *EXPECTED OUTCOME**: A learning resource that helps the user grasp [topic] effectively. It should be well-organized and easy to understand, enabling quick review and reinforcing comprehension of the material.
- --

### Business Tasks Template

- *TASK**: [Business task description, e.g., "Draft a business email to [purpose]", "Develop a meeting agenda for [meeting goal]", "Outline a project plan for [project name]"].
- *INSTRUCTIONS**:
- **Introduction/Opening**: Begin with [if applicable, e.g., "a clear email subject line"].
- **Body/Details**: Provide essential details in a concise manner. [For emails: address key points or questions. For plans: list tasks/milestones. For agendas: list topics with allotted times, etc.] Ensure each point is clear and logically ordered.
- **Conclusion/Next Steps**: Conclude with [e.g., "a call-to-action or required next steps", "summary of decisions to be made in the meeting"]. If relevant, include a polite closing (for emails) or action items (for plans).
- *TONE/STYLE**: Use a professional and clear tone. Be concise and direct.
- *FORMAT**: Output as a well-structured [document format: "email with greeting, body, closing", "numbered list of agenda items with times", "table of milestones with deadlines", etc.].
- *CONSTRAINTS**: [Any specific constraints, e.g., "Email length: 2-3 short paragraphs", "Timeline: cover next 3 months", "Agenda: fit on one page", "Do not include confidential information"].
- *EXPECTED OUTCOME**: A complete and polished [document type] that achieves its purpose. It should [outcome, e.g., "communicate the message effectively and courteously", "provide a clear roadmap for the project", "ensure the meeting runs efficiently by outlining all topics and timeframes"].
- --

## Advanced Techniques

### Meta-Prompting

When you need help creating a prompt, use this approach:

"I need to create a prompt for [specific AI task]. Based on these requirements: [detailed description], generate an optimized prompt that incorporates clarity, structure, examples, and success criteria for achieving [specific goal]."

### Iterative Refinement Process

1. Start with base template for your domain.

2. Test initial prompt and evaluate specific weaknesses.

3. Adjust one element at a time (clarity, examples, constraints, format).

4. Compare results and identify what improved.

5. Repeat until output consistently meets standards.

### Context Layering Strategy

For complex tasks, build prompts in layers:

1. Layer 1: Overall objective and big picture context

2. Layer 2: Specific role assignment and audience details

3. Layer 3: Process methodology and sequential steps

4. Layer 4: Format requirements and structural guidelines

5. Layer 5: Examples, constraints, and success criteria

### Quality Assurance Checklist

Before finalizing any prompt, verify:

- Clarity: Could someone else understand exactly what you want?
- Specificity: Are all parameters (length, audience, purpose) clearly defined?
- Structure: Does the prompt guide the AI through a logical process?
- Examples: Are there concrete examples of desired output when needed?
- Constraints: Are boundaries and requirements clearly stated?
- Success Criteria: Is it clear what constitutes a successful response?
- Context: Does the AI have all the necessary background information?
- Role Definition: Is the AI's expertise and perspective clearly established?

### Implementation Strategy

#### For Simple Tasks:

- Start with the basic template for your domain.
- Customize the placeholders with your specific requirements.
- Test and refine based on initial results.

#### For Complex Tasks:

- Use context layering to build comprehensive prompts.
- Incorporate chain-of-thought reasoning for multi-step processes.
- Provide multiple examples to establish clear patterns.
- Include verification steps for quality assurance.

#### For Ongoing Use:

- Develop a library of refined prompts for repeated tasks.
- Document modifications that consistently improve results.
- Adapt templates based on domain-specific discoveries.
- Share effective prompts with team members for consistency.