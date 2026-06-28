# Project 2 – Diagnose the Failure Twice

**Student Name:** Yamini

**Course:** System Administration and Maintenance – Administering the AI-Era Enterprise

**Chapter:** Chapter 2 – The Machine Underneath: Operating System Architecture

**Tier Targeted:** Hard Tier

---

## Repository Contents

This repository contains all artifacts required for Project 2. Each file was prepared according to the assignment requirements and supports the diagnosis of operating system incidents using both manual analysis and AI-assisted analysis.

### Included Files

**REPORT.docx**

Contains the complete project report, including the manual diagnosis, AI-assisted diagnosis, comparison of both analyses, verified verdict, runbook-ready corrective action, AI usage declaration, and project conclusion.

**ai-transcript.txt**

Contains the complete prompt provided to the AI model together with the AI's verbatim response. The transcript demonstrates the cite-and-verify approach required by the assignment.

**SIZING.txt**

Provides a detailed memory-sizing analysis using the supplied sizing worksheet. The calculations explain why the Out-of-Memory event occurred and compare FP16, INT8, and INT4 model deployments.

**MEMO.docx**

Contains a professional recommendation to the organization's director regarding the appropriate level of autonomy that should be granted to an AIOps assistant. The memo evaluates AI strengths, limitations, and operational guardrails.

**evidence/**

Contains the original incident evidence supplied for the project.

Files included:

* sample-incident.log
* sample-dmesg.log
* sample-ps.txt
* sample-iostat.txt
* sample-journal.log

The evidence files remain unmodified so that every conclusion in the report can be verified directly against the original operating system logs.

---

## Project Summary

### Incident Type

Linux Out-of-Memory (OOM) termination of a local AI model server.

### Operating System Subsystem

Memory Management

### Verified Root Cause

The Linux kernel invoked the Out-of-Memory (OOM) killer because the Ollama process exceeded the available physical memory while hosting a DeepSeek-7B FP16 model together with a large KV cache allocation. Systemd repeatedly restarted the service, but the restart attempts failed because the underlying memory limitation remained unresolved.

### Corrective Action

The permanent solution is to reduce the workload memory requirements by deploying a quantized model, decreasing the context length or batch size, configuring appropriate memory limits, or increasing the available physical memory. Restarting the service alone is only a temporary recovery action and does not eliminate the root cause.

---

## AI Usage Summary

**AI Model Used**

ChatGPT (GPT-5.5)

### Where AI Assisted

* Summarized kernel and service logs.
* Organized the incident timeline.
* Explained Linux memory management concepts.
* Assisted in structuring technical documentation.

### Human Responsibilities

All incident evidence was reviewed manually before AI analysis. Every quoted log entry was verified against the original evidence files, and the final diagnosis was determined through independent evaluation rather than relying solely on AI-generated conclusions.

---

## Learning Reflection

This project strengthened my understanding of Linux operating system troubleshooting by emphasizing the importance of evidence-based diagnosis. Rather than assuming that application crashes originate from software defects, I learned to investigate process information, kernel messages, service logs, and resource utilization together before identifying the actual root cause. Comparing my manual diagnosis with AI-generated analysis demonstrated that AI can greatly improve efficiency when interpreting large volumes of technical information; however, professional judgment remains essential for validating evidence, selecting appropriate corrective actions, and ensuring that production systems are managed safely and responsibly.
