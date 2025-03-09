# MCP Servers

This repository contains configuration and setup for Model Context Protocol (MCP) servers, including GitHub and Puppeteer integrations.

## Overview

MCP (Model Context Protocol) servers provide various functionalities for interacting with different services:
- GitHub MCP Server: For GitHub API interactions
- Puppeteer MCP Server: For web browser automation

## Setup Instructions

### Prerequisites
- Node.js and npm installed
- GitHub Personal Access Token (for GitHub MCP server)

### Installation

1. Install the required MCP servers:

```bash
# Install GitHub MCP Server
npx -y @modelcontextprotocol/server-github

# Install Puppeteer MCP Server
npx -y @modelcontextprotocol/server-puppeteer
```

### Configuration

The MCP servers are configured in the following structure:

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-github"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "your-token-here"
      }
    },
    "puppeteer": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-puppeteer"
      ],
      "env": {}
    }
  }
}
```

### Running the Servers

To run the GitHub MCP server:
```bash
GITHUB_PERSONAL_ACCESS_TOKEN="your-token" npx -y @modelcontextprotocol/server-github
```

To run the Puppeteer MCP server:
```bash
npx -y @modelcontextprotocol/server-puppeteer
```

## Features

- GitHub Integration
  - Repository management
  - Issue tracking
  - Pull request handling
  - Code search
  - And more...

- Puppeteer Integration
  - Web automation
  - Screenshot capture
  - Page navigation
  - Form interaction
  - And more...

## License

MIT

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.