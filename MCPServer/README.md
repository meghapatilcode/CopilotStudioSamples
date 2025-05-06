
# MCP Server for Copilot Studio Agents

In this exercise, you will explore how to connect Copilot Studio agents to MCP (Model Context Protocol)-compatible clients using a custom-built MCP server. You will set up a Copilot Studio agent, configure it for DirectLine communication, and run an MCP server that acts as a bridge between the agent and any MCP-compatible client. You will learn to run the MCP server locally using MCP Inspector and use it with a client like Claude Desktop.

## Steps

### Setting Up Copilot Studio Agent
Follow these steps to set up the Copilot Studio agent:

1. Download the [`CopilotAgentsSemanticKernelDemo_1_0_0_1.zip`](../SemanticKernelOrchestration/CopilotAgentsSemanticKernelDemo_1_0_0_1_managed.zip) file. This is a Power Platform solution that contains a Copilot Studio agent called **TaglineGenerator agent** which creates taglines for products based on descriptions.
2. Follow the steps in the "How to Import an Agent Developed in Copilot Studio" section of [this documentation](https://techcommunity.microsoft.com/blog/modernworkappconsult/how-to-export-an-agent-developed-in-copilot-studio/4391562) to import the agent into your Power Platform environment. After importing, you will see the TaglineGenerator agent in the list of Copilot Studio agents in your environment.
3. Configure the agent for DirectLine communication:
    -   Turn off default authentication under the agent Settings > Security > Authentication.
    ![Turn off default authentication](../SemanticKernelOrchestration/images/authentication.png)  
    -    [Enable web channel security](https://learn.microsoft.com/en-us/microsoft-copilot-studio/configure-web-security) under agent Settings > Security > Web channel security > Require secured access. This enables secured access to copilot agents using DirectLine secrets or tokens. Copy the secret for the agent and save it for later use.
    ![Enable web channel security](../SemanticKernelOrchestration/images/web_channel_security.png)
    -    [Publish the agents](https://learn.microsoft.com/en-us/microsoft-copilot-studio/publication-fundamentals-publish-channels?tabs=web#publish-the-latest-content) to start using them.

### Setting Up MCP Server Repository

1. Clone the `mcp-server-for-copilot` repository:
```bash
git clone https://github.com/CrewAakash/mcp-server-for-copilot.git
```

2. Follow the steps in the [README](https://github.com/CrewAakash/mcp-server-for-copilot?tab=readme-ov-file#-mcp-server-for-copilot-studio-agents) to set up the MCP server and run it.

    1. Add environment variables required for DirectLine communication in `.env` file. Use the agent secret copied earlier to your `.env` file.
    2. Configure agent definition in `agent_definitions.json` file. The agent definition is used by the MCP client to identify the agent and its capabilities, so it can route the queries correctly.
    3. Setup the Python environment to run the MCP server locally.
    4. Run the MCP server locally using [`MCP Inspector`](https://modelcontextprotocol.io/docs/tools/inspector#python).
    5. Use the MCP server in Claude Desktop.