# LLM Security Playground

An open-source, local educational platform for practicing LLM application security through **ten interactive exercises** using only fictional data.

**Project status:** Initial MVP committed. The application has not yet been run or validated on a physical Windows 11 machine; treat it as an early version.

## [Open the playground source](playground/)

## Requirements

- Windows 11 (or any system running Python 3.10+)
- Python 3.10+ (standard library only; no pip packages required)
- [Ollama](https://ollama.com/download) for the three live-model exercises
- Suggested model: `qwen3:4b`; you can instead use an installed smaller model

## Setup — Windows PowerShell

From the repository root:

```powershell
ollama pull qwen3:4b
ollama list
python Cybersecurity/LLM-Security/playground/server.py
```

If `python` is unavailable, try `py -3`. Ollama should already be installed and running. Open **http://127.0.0.1:8765** in your browser. Choose a lesson from the navigation, enter a prompt, and run either mode. Stop the Python server with Ctrl+C.

The UI calls the Python backend on port 8765, and the backend calls the Ollama API on `http://127.0.0.1:11434/api/chat`. The browser **does not call Ollama directly**, so you do not need to change Ollama CORS configuration. The server binds to loopback only (127.0.0.1), and is not intended for LAN/internet deployment.

### Architecture

```text
Browser (HTML/CSS/JS)
   └─ HTTP 127.0.0.1:8765
        └─ Python standard-library training server
             ├─ Live lessons 01, 02, 08 → Ollama 127.0.0.1:11434 → installed model
             └─ Lessons 03–07, 09–10 → deterministic simulations (no external actions)
```

### Exercises

| ID | Exercise | Engine |
|---|---|---|
| 01 | Prompt Injection | Live model |
| 02 | Sensitive Information Disclosure | Live model (synthetic marker) |
| 03 | Excessive Agency | Safe simulation of approval check |
| 04 | Supply Chain | Safe simulation of dependency trust |
| 05 | Data and Model Poisoning | Safe simulation of tampered record |
| 06 | Unbounded Consumption | Counter simulation; **no load sent** |
| 07 | Misinformation | Safe simulation of source grounding |
| 08 | System Prompt Leakage | Live model (fictional marker) |
| 09 | Vector and Embedding Weaknesses | Safe simulation of tenant isolation |
| 10 | Improper Output Handling | Text-only simulation; **no HTML executed** |

**Important version note:** These ten exercises are a *curated learning path*, not a claim of exact 2026 OWASP numbering. OWASP updated the LLM Top 10 in August 2026, changing rankings and categories. Map risk IDs and titles against the **[official OWASP 2026 publication](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/)** when presenting them as official. Earlier course material may use 2025 names and ordering. The current lesson IDs are stable internal identifiers only.

## How to test

1. Read the lesson.
2. Run the supplied starter prompt in **Vulnerable demo**.
3. Switch to **Protected demo** and run the identical prompt, or use Compare.
4. Write down expected result, actual result, control weakness, and suggested mitigation.
5. Remember that model responses are nondeterministic: an injection prompt may fail, and a protected prompt may still produce unexpected text.

## Security limitations

- Training use only. No authentication, TLS, user accounts, persistence, sandboxing, or production hardening.
- No real credentials, customers, purchases, refunds, downloads or cross-tenant databases.
- Any output labeled SIMULATED is an illustration; it did not perform the described action.
- The live model labs intentionally contain *fictional* markers and can expose those markers.
- Neither instruction-only mitigation nor simple output text handling alone proves a model secure.
- Do not expose the server publicly or point it at actual customer data.

## Planned improvements

- Verify the application end-to-end on Windows 11 with the target hardware.
- Add realistic scenario fixtures and automated checks for each control.
- Map lessons explicitly to both OWASP 2025 and 2026 lists.
- Add reproducible, isolated tests and a report exporter.

[Cybersecurity track](../README.md) · [Main repository](../../README.md)
