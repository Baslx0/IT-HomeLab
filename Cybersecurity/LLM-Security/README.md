# LLM Security Playground

A local, fictional DemoCart lab for exploring ten LLM application risks. Each guided scenario has a role, a concrete situation, a test objective, and a starter prompt. **Free roam** lets you continue a conversation and try your own prompts.

## Run

Install Python 3.10+, Ollama, and an Ollama model such as `qwen3:4b`. From the repository root:

```powershell
ollama pull qwen3:4b
python Cybersecurity/LLM-Security/playground/server.py
```

Open http://127.0.0.1:8765. If `python` is unavailable, try `py -3`. Ollama must be running locally at `127.0.0.1:11434`.

## Use the lab

Select a scenario or Free roam. Send a message, inspect the actual local model reply and the observation panel, then send a follow-up. Select **New conversation** to reset. Changing between Vulnerable demo and Protected demo also resets the conversation, so you can repeat an attempt under each configuration.

All ten guided labs and Free roam use the local Ollama model. Responses vary by model and prompt. The observation panel flags a few fictional marker leaks or suspicious claims; it is not a complete security assessment. No real refunds, installations, batch requests, purchases, or cross-tenant access occur. Markup in replies is displayed as text.

The server binds to loopback only. Lesson IDs are internal and are not a claim of exact OWASP version numbering. This is a teaching lab, not a production security control.

## Real project test cases

- [Case Study 001 — Instruction Override in a Local IT Assistant](case-studies/001-it-agent-instruction-override.md): an observed prompt-injection test against the separately maintained [Building-Agents](https://github.com/Baslx0/Building-Agents) learning project. The original source code and repository path were not altered.
