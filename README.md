# Weather MCP Server

A Model Context Protocol (MCP) server implementation that provides weather alerts for US states, built using the MCP Python SDK. This project demonstrates how to create an MCP server with tools, resources, and Docker integration.

[![MCP SDK](https://img.shields.io/badge/MCP-SDK-blue)](https://github.com/modelcontextprotocol/python-sdk)
[![Docker](https://img.shields.io/docker/v/ksharma9719/weather-mcp-server?label=Docker)](https://hub.docker.com/r/ksharma9719/weather-mcp-server)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## Features

- Weather alerts for US states using the National Weather Service API
- Support for both stdio and SSE (Server-Sent Events) transport
- Docker containerization
- Integration with Claude Desktop and Cursor IDE
- LLM-powered CLI client using Groq
- Built-in conversation memory support

## Project Structure

```
Creating-MCP-server/
├── server/
│   ├── weather.py        # Main MCP server implementation
│   ├── client.py         # LLM-powered CLI client
│   └── weather.json      # Server configuration
├── mcpserver/
│   ├── Dockerfile        # Docker configuration
│   ├── requirements.txt  # Python dependencies
│   ├── client-stdio.py   # Standard I/O client example
│   ├── client-sse.py     # SSE client example
│   └── server.py         # Containerized server
```

## Installation

### Local Setup

1. Clone the repository:
```bash
git clone <repository-url>
cd Creating-MCP-server
```

2. Install dependencies:
```bash
pip install -r mcpserver/requirements.txt
```

### Docker Setup

Pull the pre-built image:
```bash
docker pull ksharma9719/weather-mcp-server
```

Or build locally:
```bash
cd mcpserver
docker build -t weather-mcp-server .
```

## Usage

### Running the Server

#### Local Development
```bash
cd server
python weather.py
```

#### Using Docker
```bash
docker run -p 8000:8000 ksharma9719/weather-mcp-server
```

### Client Examples

#### CLI Client with LLM Integration
```bash
cd server
python client.py
```

#### Standard I/O Client
```bash
cd mcpserver
python client-stdio.py
```

#### SSE Client
```bash
cd mcpserver
python client-sse.py
```

## Available Tools

### get_alerts
Get weather alerts for a US state.

**Parameters:**
- `state`: Two-letter US state code (e.g., CA, TX, NY)

**Example:**
```python
result = await session.call_tool("get_alerts", arguments={"state": "CA"})
```

## Integration with Claude Desktop

1. Install the server in Claude Desktop:
```bash
mcp install weather.py
```

2. Optional: Specify a custom name:
```bash
mcp install weather.py --name "Weather Alerts Server"
```

## Development

### Prerequisites

- Python 3.11 or higher
- uv package manager
- Docker (optional)

### Environment Variables

Create a `.env` file in the server directory:
```
GROQ_API_KEY=your_groq_api_key
```

## Documentation

- [Model Context Protocol SDK Documentation](https://github.com/modelcontextprotocol/python-sdk)
- [MCP Use Documentation](https://github.com/mcp-use/mcp-use)

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Model Context Protocol team for the excellent SDK
- National Weather Service for their public API
- Groq for their LLM API
