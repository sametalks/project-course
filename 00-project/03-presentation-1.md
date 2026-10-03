project_outline: "[[00-project/01-project-outline]]"

# PROJECT TITLE
Locally Running, Privacy-Oriented Speech Recognition and Structured Logging System

Author: Huseyin Samet Alakus  
Neptun: XQVC11  
Supervisor: Tamás STORCZ  
Project ID: 2026-ST-05
---


# Problem
- Confidential spoken sessions (medical consults, legal debriefs, technical triage) require accurate structured logs.
- Cloud-hosted speech recognition APIs introduce strict compliance barriers, third-party data retention, and external leak risks.
- Storing unencrypted raw audio or full verbatim transcripts on local persistent storage leaves an unnecessary audit footprint.
- **Core Dilemma:** How to automate speech-to-structured-log workflows locally while guaranteeing zero persistent trace of raw conversations?
---

# Target users
- **Incident Response & Security Teams**: Operators coordinating sensitive post-mortem and breach investigations without recording leakage.
- **Medical Practitioners & Legal Consultants:** Professionals who need compliant session logs without external cloud processing.
- **System Auditors & Privacy Officers:** Stakeholders requiring auditable zero-trace workflows and deterministic template schemas.
---

# Planned scope
- **In Scope**:
  - Local speech-to-text pipeline using offline models (`whisper.cpp` with Metal acceleration / `faster-whisper`).
  - Volatile in-memory audio buffering with Voice Activity Detection (VAD).
  - Grammar-constrained Small Language Models (SLMs) for deterministic structured schema extraction.
  - Interactive human-in-the-loop validation workspace before committing records.
  - Enforced zero-trace memory wipe for transient audio buffers and raw transcripts upon approval.
---

- **Out of Scope**:
  - Persistent storage of raw acoustic recordings or unapproved verbatim transcripts.
  - Multi-tenant cloud or remote collaboration infrastructure.
  - Proprietary third-party cloud APIs (OpenAI Whisper API, Google Speech API).
 ---
 
# Initial user journeys: Architecture

1. **Audio Ingestion:** Audio streams strictly to volatile RAM buffer with WebRTC VAD.
2. **Local ASR:** `whisper.cpp` transcribes speech offline into transient text.
3. **Structured Extraction:** Constrained SLM extracts predefined JSON/SQLite schema.
4. **Human Review:** Operator verifies, edits, and commits structured fields.
5. **Zero-Trace Purge:** Buffer and volatile text are immediately wiped upon commit.

* **Operator Review Journey:** The reviewer initiates audio capture, inspects extracted structured fields, makes inline corrections, and confirms the log.
* **Enforced Security Flow:** Once committed (or upon session discard), raw audio and verbatim transcripts are wiped from volatile memory.
---

# Next steps
- **Semester 1 Closure:** Finalize functional specification, system boundary definitions, and formal evaluation criteria.
- **Semester 2 Milestones:**
  - Implement pipeline prototype integrating `whisper.cpp` and local schema-guided SLM extraction.
  - Empirical benchmarking across model quantization levels (`Q4_0`, `Q8_0`, `FP16`) for latency, memory footprint, and WER.
  - Validate volatile memory zeroing mechanisms and verify zero disk residue.
