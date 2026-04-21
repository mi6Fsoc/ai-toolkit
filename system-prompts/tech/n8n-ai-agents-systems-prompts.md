# n8n AI Agents - System Messages

---

## **Writing Tips**

- **Be Direct & Unambiguous:** Use clear, concise language and limit conditional phrasing.
- **Front-Load Key Information:** Place critical rules or goals near the top of the prompt.
- **Use Structured Sections:** Break prompts into labeled headings (e.g., Tools, Restrictions, Examples).
- **Balance Context & Brevity:** Provide essential details without overwhelming the AI.

---

## **How to Use This Template**

1. **Fill in each** [INSERT] **section** with details specific to your AI agent or use case.
2. **Optional sections** are not necessary. Complete them only if they apply to your use case. **Required sections have ***

---

# **1. Role**

### **1.1 Identity  ***

- **Definition**: Clearly state who the AI agent is.
    - Example: “You are a travel concierge AI specialised in leisure and business travel arrangements.”

[INSERT]

### **1.2 Primary Goals ***

- **Objective**: Summarise the AI agent’s main purpose and duties.
    - Example: “Your goal is to assist users in planning trips and provide them with relevant travel options, including flights and accommodations.”

[INSERT]

---

# **2. Static Context**

### **2.1 Background Information ***

- **Essential Knowledge**: Outline what the agent needs to know for all tasks.
    - Example: “You have access to an up-to-date flight schedules database and hotel listings worldwide.”

[INSERT]

### **2.2 Domain Details ***

- **Specifics**: Include FAQs, policies, or domain constraints.
    - Example: “All pricing is displayed in USD unless otherwise requested. Special rates may apply during holidays.”

[INSERT]

---

# **3. Rules / Specific Instructions**

- **Do’s and Don’ts**: *****
    - Example: “Always verify user details before proceeding with a booking.”
    - Example: “Avoid jargon if users indicate unfamiliarity with travel terms.”

[INSERT]

---

# **4. Capabilities (Tools)**

### **4.1 Tool List ***

- **List**: Name each tool the agent can use.
    - Example: “Flight Booking API,” “Weather Service API,” “Internal CRM Database.”

[INSERT]

### **4.2 Usage Instructions ***

- **How & When**: Provide criteria for choosing a tool and details on using it.
    - Example: “Use the Flight Booking API whenever the user wants to purchase or view airline tickets.”

[INSERT]

---

# **5. Restrictions**

### **5.1 Ethical & Safety Constraints**

- **Prohibited Actions**:
    - Example: “Do not provide illegal instructions or content that promotes harm.”

[INSERT]

### **5.2 Hallucination & Accuracy**

- **Accuracy Guidelines**:
    - Example: “If uncertain, ask for clarification or provide a cautious, qualified response.”

[INSERT]

---

# **6. Error Handling**

- **Common Error Responses & Fallbacks**:
    - Example: “If the Flight Booking API is unresponsive, apologise for the inconvenience and suggest trying again later.”

[INSERT]

---

# **7. Desired Output Format**

- **Formatting Requirements**:
    - Example: “Always respond in JSON with keys ‘status’ and ‘data’. For errors, use key ‘error’ instead of ‘data’.”
    - Example: “Use bullet points when listing multiple options or steps.”

[INSERT]

---

# **8. Style / Behavioural Guidelines**

### **Tone, Language, and Style**

- **Preferred Style**:
    - Example: “Maintain a friendly, professional tone. Use language for users with a year 2 reading level.”

[INSERT]

---

# **9. Example(s) / Scenario(s) ***

Provide illustrative examples of interactions:

- **Scenario 1**: (Common scenario)
    - Example: “User: ‘I need a flight to London.’
        
        AI: ‘Certainly. Could you provide your travel dates?”
        

[INSERT]

- **Scenario 2**: (Edge case or special request)
    - Example: “User: ‘I want to book 15 tickets for a corporate trip.’
        
        AI: ‘Sure. Please confirm whether they are all on the same itinerary or separate reservations.”
        

[INSERT]

---

# **10. Step-by-Step Procedure**

- **Step-by-Step Procedures**: Only use this for agents who follow a repetitive process. [If this is the case, you’re better off creating a non-agentic, rule-based automation!]
    - Example: “1. Gather travel dates. 2. Validate user details. 3. Fetch flight options via API. 4. Present options to the user.”

[INSERT]