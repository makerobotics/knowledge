# Agentic AI

## Landscape overview

**LLM**: The actual AI model.

**Chat/App**: End-user application.

**Coding Assistant**: Helps developers with tasks such as autocomplete and explaining code.

**Agentic system**: Can perform multi-step actions autonomously. An agent gets a goal, not a specific instruction.

**IDE**: Development environment.

**Platform**: Infrastructure for companies.

### AI Landscape Overview (2026)

| Brand | LLMs | Chat / App | Coding Assistant | Agentic System | IDE | Enterprise Platform |
| --- | --- | --- | --- | --- | --- | --- |
| OpenAI | GPT-4o, GPT-5 | ChatGPT | Codex | Codex, Operator | - | OpenAI Platform |
| Microsoft | (uses GPT + others) | Copilot | GitHub Copilot | Copilot Agents | VSC | Azure AI, Copilot Studio |
| GitHub | (uses OpenAI, Claude, Gemini models) | - | GitHub Copilot | Copilot Agent Mode | - | GitHub Enterprise |
| Anthropic | Claude Haiku, Sonnet, Opus | Claude | Claude Code | Claude Code | Lives in a terminal | Anthropic API |
| Google | Gemini Flash, Pro, Ultra | Gemini | Gemini Code Assist | Gemini Agents | - | Vertex AI |
| Cursor | Uses GPT, Claude, Gemini | Cursor Chat | Cursor AI | Cursor Agent | Cursor (VSC fork) | - |
| Codeium | Proprietary + external | Windsurf | Windsurf AI | Windsurf Agent | Windsurf | Windsurf Enterprise |
| Amazon | Nova | Q Chat | Amazon Q Developer | Amazon Q Agents | - | Bedrock |
| Alibaba | Qwen | Qwen Chat | Qwen Code | Qwen Agents | - | Alibaba Cloud AI |
| xAI | Grok | Grok | Grok Code | Grok Agent | - | xAI Platform |
| Jetbrains | - | - | - | AI assistant | IntelliJ | - |
| Cognition | (uses own + external models) | Devin App | Devin | Devin | - | Devin Platform |
| Meta | Llama | Meta AI | - | - | - | Llama Platform |
| Mistr | Mistral Large, Codestral | Le Chat | Codestral | Mistral Agents | - | Mistral Platform |

## Copilot agents

### robotdog example

**SKILL.md**: explain how to code parts of a task list, step by step, using some rules. Check the finished tasks.

**task-list.md**: List the tasks and provide checkboxes to show finished tasks (\[ \])

1. Fist attempt

Chat prompt used to start the implementation (8mn 30 sec):&nbsp;

*Implement the @task-list*

Result: skill was not used \!\!

2. Second attempt

Chat prompt used to start the implementation (1mn 30 sec):&nbsp;

*Use the @skill.md file to implement the @task-list.md*

Result: skill was used. Only one task was implemented.

## OpenAI

Create a 5€ billing and get the API key

Add the key to the .env file (secrets will be ignored by Cursor and github):

OPENAI_API_KEY=sk-proj-...

Create an OpenAI object, pass a message and get a response:

from openai import OpenAI

openai = OpenAI()

response= openai.chat.completions.create(model="gpt...", message="what time is it?")

print(response.choices[0].message.content)
