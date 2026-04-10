# 🚀 AutoGen vs CrewAI vs LangGraph  
### With Architecture Diagrams + Code Examples

---

## 📌 Overview

This repository compares three powerful AI agent frameworks:

- 🔹 AutoGen  
- 🔹 CrewAI  
- 🔹 LangGraph  

---

## 🧠 Architecture Diagrams

### 🗣️ AutoGen (Conversation Flow)

User
  ↓
Agent A ↔ Agent B ↔ Agent C
  ↓
Final Response

👉 Agents communicate via messages dynamically.

---

### 👥 CrewAI (Role-Based Pipeline)

User Task
   ↓
[Researcher] → [Writer] → [Reviewer]
   ↓
Final Output

👉 Structured pipeline with defined roles.

---

### 🔗 LangGraph (Workflow Graph)

        ┌──────────┐
        │  Planner │
        └────┬─────┘
             ↓
        ┌──────────┐
        │   Tool   │
        └────┬─────┘
             ↓
        ┌──────────┐
        │ Validator│
        └────┬─────┘
             ↓
        (Loop / Retry if needed)

👉 Explicit control over flow and state.

---

## ⚙️ Code Examples

---

### 🔹 AutoGen Example

```python
from autogen import AssistantAgent, UserProxyAgent

assistant = AssistantAgent("assistant")
user_proxy = UserProxyAgent("user")

user_proxy.initiate_chat(
    assistant,
    message="Write a Python function to calculate factorial"
)
```

---

### 🔹 CrewAI Example

```python
from crewai import Agent, Task, Crew

researcher = Agent(role="Researcher", goal="Find information")
writer = Agent(role="Writer", goal="Write article")

task = Task(description="Write blog on AI agents")

crew = Crew(
    agents=[researcher, writer],
    tasks=[task]
)

result = crew.run()
print(result)
```

---

### 🔹 LangGraph Example

```python
from langgraph.graph import StateGraph

def step1(state):
    return {"data": state["data"] + " processed"}

graph = StateGraph(dict)
graph.add_node("step1", step1)
graph.set_entry_point("step1")

app = graph.compile()
result = app.invoke({"data": "input"})
print(result)
```

---

## ⚖️ Pros & Cons

### AutoGen
✅ Flexible conversations  
❌ Hard to debug  

### CrewAI
✅ Easy to use  
❌ Limited flexibility  

### LangGraph
✅ Full control  
❌ Complex  

---

## 🎯 When to Use What

| Use Case | Framework |
|---------|----------|
| Research Agents | AutoGen |
| Content Pipelines | CrewAI |
| Production AI Systems | LangGraph |

---

## 🔥 Final Recommendation

- Beginner → CrewAI  
- Intermediate → AutoGen  
- Advanced → LangGraph  

---

## ⭐ Contribute

Feel free to improve this repo!
