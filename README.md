# Foundry Hosted Agents

## Prepare Development Environment

Prepare your development environment to build with Microsoft Foundry. You need a supported programming language, Git, and the Foundry developer tools that fit your workflow.

### Foundry Devpack

Foundry DevPack installs the Foundry developer tools for your terminal, editor, and coding agent. Select your operating system.

> Foundry DevPack is the recommended way to install the developer tools in one command. You can also install each tool separately.

#### Install Foundry Devpack

- **Windows** - `winget install Microsoft.FoundryDevPack`
- **macOS** - `brew install --cask microsoft/foundry/devpack && foundry-devpack install`
- **Linux** - `curl -fsSL https://aka.ms/foundry-devpack-install.sh | bash`

### Azure Developer CLI

The Azure Developer CLI (azd) and its azd ai agent extension give you a single command-line workflow to go from idea to a production-ready hosted agent on Microsoft Foundry. 

#### Developer Journey

| Stage | What you do | Where to learn more |
|---|---|---|
| Install | Install `azd` and the Foundry Extensions | [Set up your dev environment](https://learn.microsoft.com/en-us/azure/foundry/how-to/develop/install-cli-sdk)
| Scaffold	 | 	Initialize a project from a template or your existing code. | [	Quickstart: Deploy a hosted agent](https://learn.microsoft.com/en-us/azure/foundry/agents/quickstarts/quickstart-hosted-agent) |
| Define | Configure the agent, model deployment dependencies, protocols, tools, and environment in `azure.yaml`. |	[Author azure.yaml for hosted agents](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/author-azure-yaml) |
| Develop | Write agent logic, add tools using a toolbox, and test locally. | [Toolbox overview](https://learn.microsoft.com/en-us/azure/foundry/agents/concepts/toolbox-overview)
| Deploy | Provision infrastructure and deploy to Foundry. | [Deploy a hosted agent](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/deploy-hosted-agent)
| Operate | Monitor logs, manage versions, and automate runs. | [Manage hosted agents](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/manage-hosted-agent)
| Evaluate | Measure agent quality and improve the prompt. | [Run agent evaluations with the azd CLI](https://learn.microsoft.com/en-us/azure/foundry/observability/how-to/azure-developer-cli-evaluation)

### Deploy your first hosted agent

#### Azure CLI

```bash
azd auth login
```
#### Initialize Sample Agent

```bash
azd ai agent init -m "https://github.com/microsoft-foundry/foundry-samples/blob/main/samples/python/hosted-agents/agent-framework/responses/01-basic/azure.yaml" --deploy-mode code
```
The interactive flow guides you through configuring an AI agent by specifying the agent name, Foundry project (new or existing), Azure tenant, subscription, and region, and the model and deployment settings. You can use the defaults for most options, including gpt-5.4-mini, the default model version, Standard/GlobalStandard SKU, 10 deployment capacity, and the default deployment name. Once the configuration is complete, the flow confirms that the AI agent definition was successfully added to your azd project, after which you can change into the newly created agent folder.

> **Important:** A hosted agent project uses one ```azure.yaml``` configurations file at the project root to declare both the agent and its provisioning and deployment model. The file uses a split-service model, where each named service has a host value such as ```azure.ai.project```, ```azure.ai.agent```, ```azure.ai.connection```, ```azure.ai.toolbox```, ```azure.ai.skill```, or ```azure.ai.routine```.

### Run the agent locally

```bash
azd ai agent run
```

**If you get an error while running ```azd ai agent run``` locally, you might need to install ```uv``` using below command**

> ``` winget install --id=astral-sh.uv -e``` 

```uv``` is a fast Python package and environment manager created by Astral.It is commonly used to - create virtual environments, install dependencies, lock dependency versions,
run Python scripts inside the project environment




