# EXPLAINABILITY — Hugging Face Agents Course Mentor

> **Admissibility & Transparency Report for OpenGAP / Agent Passport**  
> *Agent Name:* Hugging Face Agents Course Mentor (`hf-agents-course-mentor`)  
> *Specification:* OpenGAP v0.1.0  
> *Domain:* Education / Autonomous Agents & Tool Use Curriculum  

---

## 1. Overview & Operational Purpose

The **Hugging Face Agents Course Mentor** (`hf-agents-course-mentor`) serves as an interactive instructional and pedagogical agent engineered for the official Hugging Face Agents Course. It assists learners in mastering autonomous agent fundamentals, the ReAct reasoning paradigm, the `smolagents` framework, multi-agent collective orchestration, and capstone evaluation benchmarks.

By providing structured curriculum navigation, real-time code linting, diagnostic quiz evaluation, and project rubrics, the mentor accelerates learning while enforcing rigorous standards of software craftsmanship and agent safety.

---

## 2. How the Agent Decides (Decision-Making Logic)

Hugging Face Agents Course Mentor operates across a deterministic, multi-stage decision pipeline:

```
[Stage 1: Learning Query Ingestion] ──> [Stage 2: Unit & Concept Alignment] ──> [Stage 3: Pedagogical Synthesis]
                                                                                                 │
                                                                                                 ▼
[Stage 6: Multi-Format Course Export] <── [Stage 5: Safety & Rubric Verification] <── [Stage 4: Code & Tool Tutoring]
```

### 2.1 Ingestion & Knowledge Level Assessment
- **Decision:** Analyzes incoming learner questions, code snippets, or quiz answers to identify current progress and prerequisite mastery.
- **Rules:** If foundational prerequisites are missing (e.g., asking about multi-agents before understanding tool calling), gently direct the student to preceding units.

### 2.2 Concept Retrieval & Alignment
- **Decision:** Maps questions to official curriculum chapters and verified code examples from the course repository.
- **Rules:** Ground explanations in course documentation and official `smolagents` patterns. Avoid unverified third-party libraries.

### 2.3 Code Analysis & Linting
- **Decision:** Evaluates student Python implementations of `CodeAgent`, `ToolCallingAgent`, and custom `@tool` functions.
- **Rules:** Check for docstrings, type annotations, and AST sandboxing rules. Flag insecure imports or unbounded loops immediately.

### 2.4 Diagnostic Feedback Generation
- **Decision:** Formulates pedagogical responses that explain the underlying reasoning mechanisms, guiding the student toward the solution.
- **Rules:** Emphasize Socratic questions and conceptual clarity over copy-paste solutions to preserve academic learning objectives.

---

## 3. Data & Privacy

| Category | Policy / Handling |
|---|---|
| **Input Data** | In-memory evaluation of student code snippets, questions, and quiz answers. |
| **Output Artifacts** | Educational explanations, code reviews, and structured curriculum progress reports. |
| **Telemetry & Logging** | Local deterministic console logging; zero transmission of personal student data to third-party endpoints. |
| **Third-Party APIs** | Model inference routed solely through student-configured or course-provided API endpoints. |

Hugging Face Agents Course Mentor complies with operational security and privacy standards:
- **No Cloud Data Exfiltration:** Operates within local or approved course environments without transmitting student homework or private code externally.
- **Epistemic Isolation:** Session memory is isolated per user interaction to guarantee no cross-student data sharing or quiz answer leakage.
- **Sanitized Model Payloads:** Prompts and code snippets are stripped of potential API keys and personal identifiers before LLM inference.
- **Data Minimization:** Only code directly related to the current exercise or unit is analyzed and retained in active context.

---

## 4. Known Limitations & Failure Modes

Reviewers, auditors, and users should note the following operational constraints:

1. **Evolving smolagents Library APIs**
   - *Limitation:* The `smolagents` library receives active updates, which may cause minor syntax differences between library versions.
   - *Mitigation:* The mentor cites exact library versions and pins compatibility requirements to match official course releases.

2. **Complex Multi-Turn Debugging**
   - *Limitation:* Debugging highly customized multi-agent distributed architectures with remote tools may exceed static code inspection capabilities.
   - *Mitigation:* The agent guides students through structured logging and step-by-step local execution traces to isolate failures.

3. **Arbitrary Code Execution Safety**
   - *Limitation:* The mentor cannot execute untrusted arbitrary student code on the host machine.
   - *Mitigation:* The agent performs static AST analysis and recommends running code inside isolated Google Colab or Hugging Face Spaces environments.

4. **Multi-Language Translation Disparities**
   - *Limitation:* Course units translated into community languages (es, fr, ko, ru, vi, zh) may have slight wording variations from the English master.
   - *Mitigation:* The mentor indexes the English reference as the canonical source while acknowledging and cross-referencing translation paths.

---

## 5. Verification, Safety & Human Oversight

The agent implements comprehensive oversight mechanisms:
- **Real-Time Human Approval Gate:** Explicit student confirmation is required before scaffolding new files or submitting capstone project repositories for scoring.
- **Emergency Session Interrupt:** Students can instantly halt long explanations or review routines via standard cancellation commands (`Ctrl+C`).
- **Step Quota Guardrails:** Interactive problem-solving walkthroughs enforce a 10-turn dialogue quota to prevent circular discussions.
- **Structured Audit Logging:** Every quiz evaluation, code recommendation, and syllabus search is deterministically logged with timestamped traces.
