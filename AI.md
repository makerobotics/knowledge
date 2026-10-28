# Landscape overview

**LLM**: The actual AI model.

**Chat/App**: End-user application.

**Coding Assistant**: Helps developers with tasks such as autocomplete and explaining code.

**Agentic system**: Can perform multi-step actions autonomously. An agent gets a goal, not a specific instruction.

**IDE**: Development environment.

**Platform**: Infrastructure for companies.

## AI Landscape Overview (2026)

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

## Benchmark LLMs

[artificialanalysis](https://artificialanalysis.ai/)

# General information

## Definitions

### Basics

**Skill**: Cookbook for a special activity. Can use own scripts for his tasks  
**Agent**: team member supporting you for a task  
**Prompt**: specific instruction (like: /create-readme)  
**React prompting**: Use the LLM to simulate thoughts  

### Design patterns (by Anthropic)

**LLM router**: directs input to a specialized sub-task (LLM)  
**Prompt chaining**: decompose into fixed sub-tasks. Use a coordinator at input and an aggregator at output  
**Parallelization**: breaking down tasks and running multiple subtasks concurrently
**Orchestrator worker**: complex tasks are broken down dynamically and combined(all are LLM)  
**Evaluator-optimizer**: LLM output is validated by another  
In contrast:  
Agent is a an LLM in a loop with tools to achieve a goal  
Risks: unpredictable path, costs and output. Needs some monitoring to evaluate the result depending on the goal. LLM as a judge. Guardrails (tests) are used to check the safety.  
Always start on a business problem (not "I need an agent"). KPI are necessary to evaluate the success.  
Anthropomorphizing: Agents are not people. They generate text. Don't plan persons in boxes. Start simple and add complexity.  

### Different types of offerings concerning AI agents

**Agent builders**: n8n, ElevenLabs (for non technical people to **build** agents)  
**Products**: Claude code, Cowork, OpenClaw (for non technical people to **use** agents)  
**Runtimes**: AWS Lambda (Technical people can **execute** their agents)  
**Frameworks**: OpenAI Agents SDK, Langgraph/Lagchain (Technical people can **develop** agents)


# MCP (Model Context Protocol)
 
Firecrawl: web server for MCP services

Create an MCP server in Python (details in modelcontextprotocol):
- Add [Python](https://github.com/modelcontextprotocol/python-sdk) and [MCP](https://modelcontextprotocol.io) sdk to the chat (paste the links)
- Use the context of both websides to generate some dummy mcp server. Use FastMCP instead of the low level abstractions.
- Generate a local mcp (stdio) or a web based (http)
- debug interface (see training)
- Use IDE to create a new MCP server (adds config to mcp.json)

Install an MCP server in vscode:
- Add json string to .vscode/mcp.json
- Add API key for access
- Click "start" in the json file to start the MCP server

# Copilot

## Agent handling

[awesome templates](https://github.com/github/awesome-copilot)

## robotdog example

**SKILL.md**: explain how to code parts of a task list, step by step, using some rules. Check the finished tasks.

**task-list.md**: List the tasks and provide checkboxes to show finished tasks (\[ \])

1. Fist attempt

Chat prompt used to start the implementation (8mn 30 sec):

`Implement the @task-list`

Result: skill was not used \!\!

2. Second attempt

Chat prompt used to start the implementation (1mn 30 sec):&nbsp;

`Use the @skill.md file to implement the @task-list.md`

Result: skill was used. Only one task was implemented.

# OpenAI

Create a 5€ billing and get the API key.  
Add the key to the .env file (secrets will be ignored by Cursor and github):

`OPENAI_API_KEY=sk-proj-...`

Create an OpenAI object, pass a message and get a response:
```from openai import OpenAI
openai = OpenAI()
response= openai.chat.completions.create(model="gpt...", message="what time is it?")
print(response.choices[0].message.content)
```