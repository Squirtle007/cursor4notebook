Using Cursor to create and modify Jupyter notebooks through MCP (Model Context Protocol).

## References
- [cursor-notebook-mcp GitHub Repository](https://github.com/jbeno/cursor-notebook-mcp)
- [Tutorial Video by Jim Beno](https://www.youtube.com/watch?v=VOVMH-tle14&ab_channel=JimBeno)

## Setup Instructions

### 1. Initialize Conda Environment
Before starting, activate conda environment (optional):
```bash
source ~/miniconda3/etc/profile.d/conda.sh
```

### 2. Install cursor-notebook-mcp
```bash
pip install cursor-notebook-mcp==0.2.2
```

### 3. Start the MCP Server
```bash
cursor-notebook-mcp --transport sse --allow-root "$PWD" --host 127.0.0.1 --port 8080
```

### 4. Configure Cursor IDE
1. Go to **Settings** → **Tools & Integration** → **Add Custom MCP**
2. Add the following configuration:
```json
{
  "mcpServers": {
    "notebook_mcp": {
      "url": "http://127.0.0.1:8080/sse"
    }
  }
}
```

### 5. Verify MCP Integration
After setup, you should see the MCP tool available in Cursor:
<img size=500 alt="Screenshot" src="https://github.com/user-attachments/assets/b1abecda-2c64-4b36-ae6e-54328fa3ccf6" />

### 6. Set Working Directory Context
Before creating notebooks, prompt Cursor in the chat box:
```
Please determine my current WSL/Linux directory path (starting with /mnt/c/) and remember this as the base location for creating/modifying notebooks via MCP tools.
```

### 7. Start Creating Notebooks! 🚀
You're now ready to create and modify Jupyter notebooks using Cursor's AI assistance.


## Troubleshooting

### Reset MCP Server
To restart the MCP server, first free up the port by killing existing processes:
```bash
# Kill all cursor-notebook-mcp processes
pkill -f cursor-notebook-mcp
