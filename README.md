# 🚀 Groq API Experiments — Assignment

Hi! I'm a QA Automation learner who explored the **Groq API** and experimented with 15 different use cases to understand how Large Language Models (LLMs) behave when you tweak parameters like `temperature`, `top_p`, `max_tokens`, `stop`, and more.

This repository contains my Postman collection and documented observations from each experiment.

---

## 🧠 What I Learned

- Different models give different output quality, format and speed for the same prompt
- Parameters like `temperature` and `top_p` control how creative or predictable the AI is
- `max_tokens` limits output length — too low and the response gets cut off mid-sentence
- The `stop` parameter lets you control exactly where the model should stop generating
- Vision models can extract and translate text from real images
- Guard models classify content as safe or unsafe — they don't generate text
- Few-shot prompting teaches the AI your preferred format using examples
- Prompt injection attacks can be defended using a strong system prompt
- Web-enabled models like `groq/compound-mini` fetch real-time data from the internet

---

## 📋 Experiments Summary

| # | Case | Model Used | What I Did | Key Observation |
|---|------|-----------|------------|-----------------|
| 1 | Model Comparison | Qwen-32b vs GPT-oss-20b | Asked both for Google.com test cases | GPT-oss gave a clean table in 1.02s, Qwen gave plain text in 1.8s |
| 2 | No Token Limit | GPT-oss-20b | Asked for 5 test cases freely | Got all 5 test cases, 831 completion tokens |
| 3 | Max Tokens 250 | GPT-oss-20b | Limited output to 250 tokens | Only 2/5 test cases generated, response cut off |
| 4 | Max Tokens 500 | GPT-oss-20b | Limited output to 500 tokens | Got 3/5 test cases — more tokens = more output |
| 5 | Temperature 0.0 | llama-3.1-8b-instant | Asked same question twice | Got identical response both times — robot mode |
| 6 | Temperature 2.0 | llama-3.1-8b-instant | Asked same question twice | Got unique creative response every time |
| 7 | Temperature 2.0 No Limit | llama-3.1-8b-instant | Removed token limit with high temperature | Response still unique and creative each time |
| 8 | Stop Parameter | llama-3.3-70b-versatile | Told model to stop at Test Case 3 | Model stopped exactly before writing TC003 |
| 9 | Image to Text | llama-4-scout-17b | Sent Flipkart image, asked for Hindi translation | Extracted English text and translated to Hindi perfectly |
| 10 | top_p Comparison | llama-3.1-8b-instant | top_p 0.01 vs 1.0 for tagline | Low top_p gave same answer, high top_p gave different creative answers |
| 11 | Guard Model | llama-prompt-guard-2-86m | Asked offensive content | Returned safety score — classified as unsafe |
| 12 | Prompt Injection | llama-3.3-70b-versatile | Tried to trick banking assistant to reveal account details | Model refused and stayed loyal to system policy |
| 13 | Few Shot Prompting | llama-3.3-70b-versatile | Gave 2 bug format examples, asked for a 3rd | Model followed exact [BUG-00X] format and suggested a realistic bug |
| 14 | Real Time Data | groq/compound-mini | Asked current temperature in Delhi | Fetched live data from web with source link |
| 15 | Text to Voice | canopylabs/orpheus-v1-english | Converted text to audio with emotion tags | TTS model produces wav/mp3 audio output |

---

## 🤖 Models Used

| Model | Owner | Best For |
|-------|-------|----------|
| `qwen/qwen3-32b` | Alibaba | Code generation, detailed output |
| `openai/gpt-oss-20b` | OpenAI | Fast structured output |
| `llama-3.1-8b-instant` | Meta | Fastest responses, lightweight tasks |
| `llama-3.3-70b-versatile` | Meta | General purpose, high quality |
| `meta-llama/llama-4-scout-17b-16e-instruct` | Meta | Vision / Image to text |
| `meta-llama/llama-prompt-guard-2-86m` | Meta | Content safety classification |
| `groq/compound-mini` | Groq | Real time web search |
| `canopylabs/orpheus-v1-english` | Canopy Labs | Text to speech |

---

## 🔑 Key Parameters Learned

| Parameter | What it controls |
|-----------|-----------------|
| `temperature` | How random/creative the response is — 0.0 = same every time, 2.0 = unique every time |
| `top_p` | How many word choices AI considers — 0.01 = very focused, 1.0 = full vocabulary |
| `max_tokens` | Maximum length of response — lower value cuts output short |
| `stop` | Keyword where model stops generating — great for controlling output length |
| `stream` | Whether response comes all at once or token by token |

---

## 📁 Repository Contents

```
├── README.md               → This file
├── GROQ_API.docx           → Full assignment document with all observations
└── Groq_Collection.json    → Postman collection with all 15 API calls
```

---

## 🛠️ How to Use the Postman Collection

1. Download `Groq_Collection.json` from this repo
2. Open Postman
3. Click **Import** → Upload the JSON file
4. Add your Groq API key in the Authorization header:
```
Authorization: Bearer YOUR_GROQ_API_KEY
```
5. Hit any request and observe the response!

---

## 💡 Biggest Learnings

> *Same prompt + different model = completely different output style, speed and quality*

> *Temperature 0.0 is your best friend for consistent code generation*

> *Few shot prompting is the easiest way to control AI output format*

> *Guard models are the first line of defence against harmful content in real world apps*

---

## 🙋 About

This assignment was done as part of exploring Groq API capabilities for AI automation testing.
Built with curiosity, one API call at a time! 🚀
