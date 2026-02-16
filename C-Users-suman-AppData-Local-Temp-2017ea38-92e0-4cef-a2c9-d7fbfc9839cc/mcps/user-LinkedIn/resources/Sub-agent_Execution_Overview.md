# Sub-agent Mode

Each tool corresponds to a component but accepts a single `instruction` input. The MCP server forwards that instruction to Pipedream's server-side agent that:

1. Selects the correct sequence of configuration helpers and tools.
2. Retrieves remote options when needed (Slack Channel, Google Sheets Spreadsheets, Linear Teams, etc.).
3. Configures required and optional props.
4. Reloads dynamic props when dependencies change.
5. Executes the action and returns the results to the top-level LLM.

Because another LLM is used to handle the actual tool configuration, keep instructions precise, and realize that Pipedream's server-side sub-agents may return additional questions or asks from the user (ie, "Which Linear team do you want to create the ticket in?").