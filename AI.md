# Agentic AI

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

Create a 5€ billing
Get the API key
Add the key to the .env file (secrets will be ignored by Cursor and github):
OPENAI_API_KEY=sk-proj-...
Create an OpenAI object, pass a message and get a response:
from openai import OpenAI
openai = OpenAI()
response= openai.chat.completions.create(model="gpt...", message="what time is it?")
print(response.choices[0].message.content)
