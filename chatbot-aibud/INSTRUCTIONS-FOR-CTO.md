# Instructions for CTO — AI Buddy Website Chatbot

**To:** CTO (aukik@aibud.ca)  
**Re:** Chatbot content pack for aibud.ca (customer-facing, sales + FAQ)

---

## What this is

This folder contains everything needed to power a **website chatbot** for [aibud.ca](https://aibud.ca/): copy, tone rules, FAQ, suggested questions, and one importable JSON. Visitors use it to learn about AI Buddy, our products (e.g. DocDirector), and how to get started.

**Tone:** Friendly, with optional light 80s/90s pop-culture references (Hollywood/Bollywood blockbusters, rock/pop/world hits). Clarity and helpfulness come first; references are optional seasoning.

---

## Files in this folder

| File | Purpose |
|------|--------|
| **TONE.md** | Voice and style guide. Use in the **system prompt** (or equivalent) so the LLM stays on-brand. Also for anyone editing bot answers. |
| **KNOWLEDGE-BASE.md** | Full reference: company summary, products, FAQ, suggested questions, handoff rules. Use as context for RAG, or as the source of truth when tuning answers. |
| **aibud-chatbot-import.json** | Single importable payload: `tone`, `company_summary`, `suggested_questions`, `faq` (Q&A array), `products`, `cta`. Feed this into your chatbot platform, vector DB, or custom backend. |
| **README.md** | Short overview of the pack. |
| **INSTRUCTIONS-FOR-CTO.md** | This file. |

---

## What you need to do

1. **Choose how the bot runs**  
   - Use a platform (e.g. Intercom, Crisp, Chatbase, Botpress, Tidio) that supports FAQ + optional “ask anything” LLM, or  
   - Build a small custom stack: chat UI → your backend → LLM API (OpenAI, Anthropic, etc.) with this content as context.

2. **Load the content**  
   - **Suggested questions:** Use the 8 questions in `aibud-chatbot-import.json` → `suggested_questions` (or from KNOWLEDGE-BASE.md) as the **clickable prompts** in the widget so visitors see what to ask.  
   - **FAQ / knowledge:** Ingest `aibud-chatbot-import.json` (e.g. `faq` + `company_summary` + `products`) into your RAG/knowledge base or use as static context in the system prompt.  
   - **Tone:** Put the short `tone` description from the JSON (or the “Do / Don’t” section from TONE.md) into the **system prompt** so the model stays friendly and on-brand.

3. **Wire the widget to the site**  
   - Add the chatbot widget/script to aibud.ca (all pages or key pages: home, product, pricing, contact).  
   - Ensure “Book a call” and “Join waitlist” (DocDirector) are easy to reach from the bot (e.g. in answers or as quick replies).

4. **Handoff**  
   - When the bot can’t answer or the user asks for pricing/proposal/demo, point to **Book a call** (aibud.ca).  
   - For DocDirector access, point to **Join the waitlist** and/or **Book a call**.

5. **Go live and iterate**  
   - Soft launch, monitor top questions and drop-off, then refine FAQ and suggested questions as needed.  
   - Keep content in this folder (or a single source of truth) and re-import after updates.

---

## Quick reference: suggested questions (widget)

Use these as the clickable options in the chat widget:

1. What does AI Buddy do?
2. Who is it for?
3. What is DocDirector?
4. How much does it cost?
5. How do I get started?
6. What integrations do you support?
7. How are you different from other agencies?
8. How can I contact you?

---

## Technical notes

- **Token usage:** The JSON and KNOWLEDGE-BASE are kept concise so they fit comfortably in typical context windows or RAG chunks.  
- **Updates:** When product/copy changes, update KNOWLEDGE-BASE.md and regenerate or edit `aibud-chatbot-import.json` so the bot and docs stay in sync.  
- **Privacy / compliance:** Ensure conversation data handling and storage match your policies (e.g. GDPR if you have EU visitors).

---

## Questions

If anything is unclear or you need a different format (e.g. CSV, different JSON schema, or copy in another structure), reply to the team or aukik@aibud.ca and we can adjust.

— AI Buddy team
