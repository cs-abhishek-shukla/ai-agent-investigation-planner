# Release Information

- **Version**: 1.0.0

- **Certified**: Yes

- **Publisher**: Fortinet

- **Scope**: Analysis and Investigation

- **Verified with Models**: Fortinet FortiAI (AI model Medium)

# Investigation Planner

Generates investigation plans and structured methodologies for security alerts. Outlines investigation steps, recommends investigation direction, and provides approach based on alert complexity and investigation scope.

## Installation

This agent installs along with the FortiAI solution pack.

## Configuration

**Required MCP Servers**: NA

<!-- > [!Note]
>
> Refer to [Configuring MCP Servers](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/823139/mcp-servers#Configure_MCP_Servers) on FortiSOAR platform documentation for information on configuring a custom MCP server.
>  -->

### Prerequisites

- The FortiAI solution pack must be installed and configured with the Fortinet FortiAI connector.

  - To configure the FortiAI solution pack, refer to the [FortiAI](https://github.com/fortinet-fortisoar/solution-pack-fortinet-advisor/) solution pack documentation.
  - To configure the Fortinet FortiAI connector, refer to the [Fortinet FortiAI](https://docs.fortinet.com/fortisoar/connectors/fortinet-fortiai) connector documentation.

> [!Note]
>
> FortiAI solution pack and Fortinet FortiAI connector are preconfigured out-of-the-box with FortiSOAR `v8.0.0`.
> 


## Input Parameters

The input must be provided as a JSON object.

| Parameter    | Description                                                           |
|--------------|-----------------------------------------------------------------------|
| `data`       | Raw alert data containing initial alert details and context.          |
| `indicators` | List of identified indicators of compromise extracted from the alert. |
| `hypotheses` | List of generated investigation hypotheses based on alert analysis.   |
| `agents`     | List of agents assigned to execute investigation tasks.               |

## Response

The output is returned as a JSON object.

| Parameter                  | Description                                                                                 |
|----------------------------|---------------------------------------------------------------------------------------------|
| `status`                   | Response status ('success' or 'failure').                                                   |
| `plan`                     | Array of investigation steps with the following properties:                                 |
| `question`                 | Investigation question to be answered.                                                      |
| `primary_information_type` | List of information types required to answer the question.                                  |
| `agent_hint`               | Assigned agent responsible for executing the step (e.g., ThreatIntelAgent, AssetCMDBAgent). |
| `params`                   | Additional parameters and configuration for the investigation step.                         |
| `supports`                 | List of hypothesis IDs supported by this investigation step.                                |
| `weakens`                  | List of hypothesis IDs weakened by this investigation step.                                 |
| `tactics`                  | MITRE ATT&CK tactics relevant to the investigation.                                         |
| `techniques`               | MITRE ATT&CK technique IDs relevant to the investigation.                                   |
| `yes_path`                 | Next step IDs if the answer is affirmative.                                                 |
| `no_path`                  | Next step IDs if the answer is negative.                                                    |
| `message`                  | Status message providing additional context or details.                                     |


