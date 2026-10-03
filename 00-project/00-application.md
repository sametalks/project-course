---
name: Huseyin Samet Alakus
neptun: XQVC11
id: 2026-ST-05
---

# Locally Running, Privacy-Oriented Speech Recognition and Structured Logging System

## My interpretation of the brief
The project addresses the challenge of capturing and structuring spoken information from confidential conversations without compromising data privacy. Cloud-based speech processing introduces unacceptable data exposure risks and regulatory concerns (e.g., GDPR). This project designs a strictly offline, locally running system that converts spoken input to text, extracts structured log entries based on a predefined template, enforces immediate memory purge of raw audio and full transcripts, and retains only user-validated structured records. A key research dimension is identifying the minimum viable model size and hardware footprint capable of meeting accuracy and latency thresholds.

## Why I am a good fit for this project
I am focused on modern system architecture, Edge AI deployment, and data modeling. Deploying local machine learning models with constrained hardware resources requires systematic evaluation of inference trade-offs (quantisation, memory footprint, processing latency). I have practical interest in privacy-by-design software architectures and reproducible benchmarking.

## Relevant experience and background
I have practical experience developing software applications, working with Python, REST API development, containerised environments, and relational/lightweight local database schemas. I understand Git workflows, state isolation, and working with local inference frameworks on Apple Silicon unified memory architectures.

## Proposed approach
I will design a multi-stage, privacy-first processing pipeline:
1. Ingestion: In-memory volatile audio capture with Voice Activity Detection (VAD) to isolate speech segments.
2. Local ASR: Local speech-to-text inference utilizing optimized offline engines (such as whisper.cpp with Metal acceleration or faster-whisper) across varying model sizes (tiny, base, small) and quantisation levels.
3. Structured Extraction: Extraction of template-defined fields (timestamp, participants, categorical intents, action items) via schema-constrained local Small Language Models (SLMs) or deterministic rule parsers.
4. Human-in-the-Loop Review: An interface allowing the operator to inspect, edit, or reject extracted fields before committing.
5. Zero-Trace Purge: Automatic wiping of the raw audio buffer and full transcript from volatile memory once the structured record is approved and stored.

## Initial plan
1. Formalise the functional and non-functional requirements and privacy boundaries.
2. Define the structured log schema (JSON/SQLite) for a representative confidential domain (e.g., technical incident debriefs or internal consultations).
3. Design the local processing pipeline architecture and data isolation mechanism.
4. Specify the empirical evaluation framework to measure Word Error Rate (WER), extraction accuracy, inference latency, and RAM utilization across model configurations.
5. Identify or specify compliant, non-sensitive speech datasets and synthetic generation workflows for evaluation.
6. Prepare the formal specification document and Semester-1 presentations according to course standards.

## Additional information
All architectural decisions, schemas, and benchmarking protocols will be version-controlled in Git. No confidential audio, external proprietary APIs, or cloud credentials will be used.
