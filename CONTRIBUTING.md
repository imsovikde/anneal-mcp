# Contributing to Anneal MCP

Contributions to client configurations, documentation, prompt recipes, and integration guides are welcome.

## Development Workflow

1. Fork this repository.
2. Ensure manifest changes validate against the official schema:
   ```bash
   node -e 'JSON.parse(require("fs").readFileSync("server.json"))'
   ```
3. Test your configuration locally using the MCP Inspector or direct client configuration.
4. Submit a Pull Request detailing your changes.