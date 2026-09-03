# Workday Transformation Assistant — Usage Guide

Install the MCP server in Claude Code and run the Studio, XSLT, and Web Service generators.

---

## Part 1 — One-time Setup

### Step 1: Download and save the `.exe`

Create a folder named **"Claude MCP"** and place the `WorkdayMCP.exe` file inside it.

### Step 2: Double-click the `.exe` file

### Step 3: Wait for auto-registration to complete

A console window opens and registers the server with Claude Desktop. You should see a **SUCCESS** message confirming it is registered.

### Step 4: Press Enter

Press **Enter** in the console window to close it once registration is complete.

### Step 5: Quit and restart Claude

Fully quit Claude Desktop and reopen it so the new server is loaded.

### Step 6: Verify the server in Settings → Developer

In Claude Code, open **Settings → Developer**. The Workday Transformation Assistant should be listed under **Local MCP servers** with a **running** status.

### Step 7: Select your working folder in Claude Code

In Claude Code, use **Select Folder** and choose the **"Claude MCP"** folder where you saved the `.exe`.

---

## Part 2 — Using the Assistant

Once the server is running and your folder is selected, start a task from Claude Code. Each generator follows the same pattern:

1. Open the tool
2. Fill in the inputs
3. Click **Generate**
4. Press **Enter** on the single-line prompt that appears in chat

---

### A. Studio Integration

#### Step 8: Open Studio and run the listener

Send a message in Claude Code:

```
Open Studio and run listener
```

Allow every permission pop-up that appears (including the **"Listen for studio ui"** permission).

#### Step 9: Provide the design document and generate

Upload the design document, add any additional instructions, then click **Generate Studio Integration**.

#### Step 10: Press Enter on the single-line prompt

After clicking Generate, the chat shows a single pre-filled line. Press **Enter** to run it — Claude generates the Studio integration codebase and saves the files.

> **Result:** Generated assembly, diagram, and XSLT files saved to the project.

---

### B. XSLT Generation

Send the following message in Claude Code to launch the XSLT Generator:

```
open xslt
```

Fill in all the parameters:

| Parameter | Description |
|---|---|
| Category | Integration category |
| Output Format | Desired output format |
| XSLT Version | Target XSLT version |

Then provide the **source XML** and, optionally, an **expected output sample**.

Click **Generate Transformation**, then press **Enter** on the single-line prompt in chat.

> Copy the completed XSLT directly from Claude's reply.

---

### C. Web Service (SOAP Request Builder)

Open the **Workday Web Service SOAP Request Builder** from Claude Code, then fill in the operation details:

- **WWS operation web service name**
- **WSDL version**
- **Field mappings** or a **sample payload specification**

Click **Generate Web Service Request**, then press **Enter** on the single-line prompt in chat.

> **Result:** Claude returns the fully configured SOAP request payload with all field mappings applied.

