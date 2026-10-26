# Day 3 — AI Agent Vulnerability Lab

## Overview
Built a simple AI agent and demonstrated **indirect prompt injection** via a malicious document.

## Files
- `simple_agent.py` — Vulnerable agent + defended version
- `report.txt` — Document containing hidden injection payload

## Findings
- Agent successfully followed injected instructions hidden inside a document
- The LLM changed its behavior and attempted to read `/etc/passwd`
- Model refused to output the actual sensitive file due to safety alignment
- Simple keyword-based defense successfully blocked the injection

## MITRE ATLAS Mapping
- AML.T0051 — LLM Prompt Injection
- AML.T0054 — Indirect Prompt Injection

## Defensive Recommendations
1. Content sanitization before passing document content to the LLM
2. Output validation — check what the agent is about to do
3. Strict tool permissions (FileReader should not access system files)
4. Human-in-the-loop for sensitive operations

## Tools Used
- Ollama (llama3.2) — local LLM
- Python 3
