# LLM Security Lab

**Status:** Planned — no application or test findings are claimed yet.

## Goal
Build a simple fictional store support chatbot with HTML/JavaScript, a small model running locally through Ollama, and a minimal local backend. Use only synthetic demo data.

## Proposed exercises
1. Establish expected assistant behavior and system rules.
2. Test prompt-injection attempts and record actual model responses.
3. Explore sensitive information disclosure and output handling in a controlled demo.
4. Add mitigations and rerun the same tests.
5. Document scenario, expected behavior, actual result, impact and mitigation.

## Planned layout
```text
LLM-Security/
├── README.md
└── chatbot-store-lab/         # To be added when implemented
    ├── index.html
    ├── app.js
    ├── server.py
    └── test-cases.md
```

**Note:** Do not put real credentials or personal data in example files.

[Cybersecurity track](../README.md) · [Main index](../../README.md)
