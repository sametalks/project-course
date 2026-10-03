name: Huseyin Samet Alakus neptun: XQVC11 id: 2026-ST-05 github: https://github.com/sametalks/project-course github_project: https://github.com/users/sametalks/projects/1

# Locally Running, Privacy-Oriented Speech Recognition and Structured Logging System

Confidential conversations frequently require accurate, structured documentation without the risk of exposing sensitive audio recordings or verbatim transcripts to third-party services or persistent storage. This project develops the design and specification for a locally running, privacy-preserving AI pipeline. The system transcribes spoken input on local hardware, extracts structured records adhering to a predefined schema, provides an operator review interface, and securely purges intermediate audio and raw textual artifacts. The work focuses on determining the minimum model size and hardware configuration capable of satisfying predefined latency and accuracy constraints.

## Objectives

* Primary objective: Design a locally runnable, privacy-preserving speech recognition and template-based structured logging system that securely purges intermediate audio and transcript data.
* Target users / stakeholders: Professionals handling confidential dialogues (medical practitioners, incident response teams, technical consultants) who require structured documentation without persistent conversational recording or external cloud processing.
* Measurable success criteria: Zero persistence of raw audio or unapproved verbatim transcripts across application restarts; identification of the minimum viable local model configuration achieving acceptable extraction accuracy and operational inference latency.
* Constraints: Local execution only; Apple Silicon unified memory optimization; no persistent storage of raw acoustic data; zero third-party cloud API dependencies; no credentials in the repository.

## Scope

### In scope
* Local speech-to-text pipeline using offline models (e.g., whisper.cpp with Metal acceleration / faster-whisper variants).
* Template-driven structured data extraction into verified JSON and relational schemas.
* In-memory processing and explicit data-deletion mechanisms for intermediate speech representations.
* Evaluation matrix measuring model size, quantisation, memory footprint, WER, and structured field extraction accuracy.
* Investigation of compliant public datasets and lawful synthetic data generation protocols for isolated testing.
* Human-in-the-loop validation interface for reviewing and approving extracted fields.

### Out of scope
* Persistent long-term archiving of raw conversational audio or full verbatim transcripts.
* Multi-user remote collaboration or distributed cloud deployments.
* Proprietary cloud-hosted LLM/ASR API integration (e.g., OpenAI, Google Cloud).
* Mobile operating system deployment (initial focus is macOS/Linux local workstation environments).

## Notes

Semester 1 establishes the full functional and technical specification, pipeline architecture, and empirical evaluation methodology. Prototype implementation and benchmark execution will be carried out during Semester 2.