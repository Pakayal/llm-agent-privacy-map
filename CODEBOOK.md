# Codebook

A value is recorded when the full text states it or the evaluation measures it. A privacy notion is recorded when the study states that requirement or evaluates it. A surface is recorded when the study names that location in the problem or uses it in the experiment. Text that exists only in the current prompt is context. A memory store is a store the agent keeps for a later step or a later run. A database is a store the agent queries as structured data. An external service is a web site, an API, an application, or a cloud service. Another agent is recorded as its own surface. Deletion means the study checks that a copy is gone. Redaction before a value is sent is recorded as a control on disclosure.

Each value except the cases noted below is stored with the passage that supports it.

## Fields

**Privacy problem.** One sentence stating the question in the study's own terms, with the passage it rests on.

**Data subject.** One or more of: invoking person; person named in a record; organization; another user of a shared system.

**Privacy notion.** One or more of:

- Confidentiality: the study states or tests that information should not be disclosed to an unauthorized party.
- Contextual integrity: the study names contextual integrity or privacy norms and evaluates whether a flow fits the context.
- Purpose limitation: the study states or tests that a later use must match a specified purpose.
- Data minimization: the study states or tests that the agent should access, disclose, or retain no more than the task needs.
- Consent: the study states or tests consent of the person whose information is used.
- Formal privacy: the study specifies a mathematical guarantee, such as differential privacy or a proved bound, and evaluates it. Cryptography or anonymization without that guarantee is not formal privacy.

**Surfaces in the problem.** Locations the study's question depends on. **Surfaces in the evaluation.** Locations the reported experiment uses. A location mentioned only as motivation or related work stays out. The values are: records and files; databases; external services; memory stores; other agents; logs.

Records and files include emails, documents, code repositories, configuration files, and meeting notes. Logs are execution, audit, or debug records.

**Observed channel.** An artifact the evaluation inspects: final answer; query; tool arguments; tool response; memory write; message between agents; log entry.

**Adversary.** The party the study treats as able to observe the data: person receiving the answer; another user; external service; another agent; reader of memory or logs; attacker who supplies content the agent reads. The list is empty when the text does not identify one.

**Enforcement.** Model-level means instructions or training meant to shape what the model reveals. Runtime-level means a component outside the generated text inspects, blocks, rewrites, or withholds an action or a write. Both, when the study describes both. No control described, when the study measures an agent and does not describe a control.

**Time span.** One step; the same run; a later run. A later run is recorded when the text says a later session, or a persisted memory, is used after the original run. Not reported, when the text does not say. The passage may be absent for not reported.

**Utility.** Assessed, when the study reports whether the task still succeeds. Otherwise not assessed. The passage may be absent for not assessed.

**Deletion.** The copies the study checks for removal, among memory, logs, and another copy made during the run. An empty list means deletion was not assessed, and the passage may be absent.

**Database, memory, and agent path.** True only when the evaluation follows one fact from a database read, into a memory write, and then to another agent. Otherwise false, with no passage.

## Exclusion rules

A study in `data/studies.json` with `included` set to false was read and then excluded. The first matching rule is recorded.

- E1. The study only targets a fact in the model's training parameters, by extraction or by unlearning. A fact held in an agent store, such as a retrieval index or a memory, stays eligible.
- E4. The system only produces an answer. The task includes no tool call, file or database operation, memory write, log, or message to another agent.

`data/not_obtained.json` uses E5: a full text in English could not be obtained.
