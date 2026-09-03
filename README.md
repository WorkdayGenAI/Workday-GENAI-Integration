# Workday Integration Hub — Complete User Guide

Welcome to the **Workday Integration Hub**, your AI-powered assistant for building Workday integrations faster than ever. This guide walks you through everything from first-time setup to generating production-ready code — all from within Claude Code.

---

## 📑 Table of Contents

1. [What Is the Workday Integration Hub?](#1-what-is-the-workday-integration-hub)
2. [What Can It Do?](#2-what-can-it-do)
3. [What You Need Before Starting](#3-what-you-need-before-starting)
4. [First-Time Setup (Step by Step)](#4-first-time-setup-step-by-step)
5. [How to Open the Dashboard in Claude](#5-how-to-open-the-dashboard-in-claude)
6. [The Hub Dashboard — Your Starting Point](#6-the-hub-dashboard--your-starting-point)
7. [Module 1: XSLT Stylesheet Generator](#7-module-1-xslt-stylesheet-generator)
8. [Module 2: Workday Studio Integration Generator](#8-module-2-workday-studio-integration-generator)
9. [Module 3: BIRT Report Design Generator](#9-module-3-birt-report-design-generator)
10. [Module 4: Web Services SOAP Request Builder](#10-module-4-web-services-soap-request-builder)
11. [How It Works Behind the Scenes](#11-how-it-works-behind-the-scenes)
12. [Where Are My Generated Files Saved?](#12-where-are-my-generated-files-saved)
13. [The Knowledge Base — What Claude Knows](#13-the-knowledge-base--what-claude-knows)
14. [Sharing the Tool With Your Team](#14-sharing-the-tool-with-your-team)
15. [Troubleshooting & FAQ](#15-troubleshooting--faq)

---

## 1. What Is the Workday Integration Hub?

The Workday Integration Hub is a **visual dashboard that lives inside Claude Code**. When you open it, a widget panel appears on the right side of your chat. You fill out forms, upload design documents, and click **Generate** — Claude reads everything you provide, applies Workday-specific knowledge and production templates, and writes complete, deployable integration code directly in the chat window.

**No manual prompting required.** You don't need to know how to write prompts. The visual forms handle all of that for you.

---

## 2. What Can It Do?

The Hub gives you four dedicated AI-powered generators:

| Generator | What It Creates | When to Use It |
| :--- | :--- | :--- |
| **XSLT Generator** | Production-ready XSLT stylesheets (1.0, 2.0, 3.0) | You need a Workday Document Transformation, EIB transform, Core Connector output, or PECI transformation |
| **Studio Integration Generator** | Complete `.clar` Spring Beans assembly XML + visual `.assembly-diagram.xml` layout coordinates | You are building a Workday Studio integration project and have a design specification document |
| **BIRT Report Generator** | Deployable Eclipse BIRT `.rptdesign` report layout XML | You need to create or replicate a Workday BIRT report from a visual layout sample |
| **Web Services SOAP Builder** | Ready-to-use SOAP request XML envelope payloads | You need the correct SOAP request format for a specific Workday Web Service API operation |

---

## 3. What You Need Before Starting

| Requirement | Details |
| :--- | :--- |
| **Claude Code** | The official Claude Code application (desktop or IDE extension), installed and logged in with an active account. |
| **WorkdayMCP.exe** | The Workday MCP server executable. Place it in a dedicated folder (e.g., `C:\Users\YourName\Claude MCP`). No additional Python or Node.js installation is required. |

---

## 4. First-Time Setup (Step by Step)

### Step 1: Create a folder and place the .exe
Create a folder named **"Claude MCP"** in a convenient location on your computer. For example:
```
C:\Users\YourName\Claude MCP
```
Place the `WorkdayMCP.exe` file inside this folder.

### Step 2: Double-click the .exe file
Double-click `WorkdayMCP.exe` to launch the auto-registration process. A console window will open.

### Step 3: Wait for auto-registration to complete
The console window registers the MCP server with Claude automatically. Wait until you see a **SUCCESS** message confirming it has been registered.

```
============================================================
   WORKDAY INTEGRATION ASSISTANT — AUTO REGISTRATION
============================================================
[+] SUCCESS: Registered successfully with Claude!
[*] Please RESTART Claude completely to apply changes.
============================================================
```

### Step 4: Press Enter
Once the SUCCESS message appears, press **Enter** in the console window to close it.

### Step 5: Quit and restart Claude
This step is **critical**:
1. **Fully quit Claude** — close it completely from the taskbar or system tray.
2. **Relaunch Claude Code** so the new server is loaded.

### Step 6: Verify the server in Settings → Developer
Open **Settings → Developer** in Claude Code. The **Workday Transformation Assistant** should be listed under **Local MCP servers** with a **running** status.

```
Settings → Developer
└── Local MCP servers
    └── Workday Transformation Assistant  ●  running   ✅
```

### Step 7: Select your working folder in Claude Code
Back in Claude Code, use **Select Folder** and choose the **"Claude MCP"** folder where you saved the `.exe`. This is the working directory where generated files will be saved.

✅ **Setup is complete.** You're ready to use the Hub.

> 💡 **FYI — What's bundled inside the .exe**: The executable packages all required dependencies so you don't need to install anything manually. These include:
> - `fastmcp` — The communication bridge between Claude and the Hub server.
> - `pandas` & `openpyxl` — For reading Excel mapping files and the Web Services database.
> - `python-docx` — For reading Word design documents (`.docx`).
> - `pypdf` — For extracting text from PDF specification files.
> - `tabulate` — For formatting tabular data.
> - `lxml` — For advanced XML processing.

---

## 5. How to Open the Dashboard in Claude

Once the server is running and your folder is selected, start a task from Claude Code. Each generator has a dedicated launch command:

| Module | Command to type in Claude Code |
| :--- | :--- |
| **Hub Home (all modules)** | `Open workday home` |
| **Studio Integration** | `Open Studio and run listener` |
| **XSLT Generator** | `open xslt` |
| **BIRT Report Generator** | `Open the BIRT report designer` |
| **Web Service SOAP Builder** | `Open the Web Service builder` |

Claude will process the request and display a widget on the right side of its chat response.

> ⚠️ **Important**: When you open Studio or any module for the first time in a session, Claude Code will show **permission pop-ups**. You must **Allow every permission pop-up that appears** for the tools to function correctly.

```
+------------------------------------------+-------------------------------------------+
|  Claude Code Chat                        |  Workday Integration Hub (Widget Panel)   |
|                                          |                                           |
|  You: Open workday home                  |  ┌───────────────────────────────────────┐ |
|                                          |  │  ACCENTURE · WORKDAY PRACTICE         │ |
|  Claude: ✓ Tool executed                 |  │                                       │ |
|  ┌──────────────────────────┐            |  │  Build integrations faster than ever  │ |
|  │  [ open widget ]         │ ◄── CLICK  |  │                                       │ |
|  └──────────────────────────┘            |  │  ┌─────────────┐ ┌─────────────────┐ │ |
|                                          |  │  │ XSLT        │ │ Studio          │ │ |
|                                          |  │  │ Generation   │ │ Integration     │ │ |
|                                          |  │  └─────────────┘ └─────────────────┘ │ |
|                                          |  │  ┌─────────────┐ ┌─────────────────┐ │ |
|                                          |  │  │ BIRT Report  │ │ Web Service     │ │ |
|                                          |  │  │ Generation   │ │ SOAP Builder    │ │ |
|                                          |  │  └─────────────┘ └─────────────────┘ │ |
|                                          |  └───────────────────────────────────────┘ |
+------------------------------------------+-------------------------------------------+
```

---

## 6. The Hub Dashboard — Your Starting Point

The main Hub dashboard shows four clickable cards:

1. **XSLT Generation** — Tags: `Core Connector`, `PECI`, `EIB`, `Studio`
2. **Studio Integration** — Tags: `Connector Steps`, `Document Maps`, `Fault Handling`
3. **BIRT Report Generation** — Tags: `Reports`, `Data Sources`, `Layouts`
4. **Workday Web Service** — Tags: `SOAP`, `WSDL`, `Web Services`

Click any card to open its dedicated generator workspace.

---

## 7. Module 1: XSLT Stylesheet Generator

### Purpose
Generates complete, production-ready XSLT transformation stylesheets for Workday integrations. Claude automatically applies the correct Workday XML namespace declarations, output format rules, and version-specific element constraints.

### Form Fields

| Field | Required? | Description |
| :--- | :--- | :--- |
| **Design / Transformation Document** | Optional | Upload your Workday Integration Design Document (PDF, DOCX, XLSX, CSV, TXT, MD, or XML). If you upload a design doc, **all other fields below become optional** — Claude extracts everything it needs from the document. |
| **Category** | Required | Select the integration type. Options: `Core Connector DT`, `PECI`, `EIB`, `Report DT`, `Studio`. |
| **Output Format** | Required | What the XSLT should produce. Options: `CSV (comma-delimited)`, `Fixed-width`, `XML`, `DOCX`, `XLSX`, `PDF`, `Other` (type custom). |
| **XSLT Version** | Required | The transformation engine version. Options: `XSLT 1.0`, `XSLT 2.0 (recommended)`, `XSLT 3.0`. |
| **Source XML** | Optional (if design doc uploaded) | Either upload an `.xml` file **OR** paste sample Workday XML directly into the text box. This is the XML that the XSLT will transform. |
| **Expected Output Sample** | Optional | Paste what the final transformed output should look like (e.g., CSV rows, XML structure). Helps Claude match your exact expectations. |
| **Field Level Mappings** | Optional | Map source XML elements to output fields. Example: `Employee_ID -> EmpID`, `First_Name -> FirstName`. You can also paste raw `xsl:template` blocks here. |
| **Additional Instructions** | Optional | Any extra business rules. Examples: *"Skip terminated workers"*, *"Date format must be MM/DD/YYYY"*, *"Add a header row with column names"*. |

### Step-by-Step Walkthrough

1. In Claude Code, type **`open xslt`** to launch the XSLT Generator widget.
2. Allow any permission pop-ups that appear.
3. *(Optional but recommended)* Upload your design document — if you do, all other fields become optional.
4. Select your **Category** (e.g., `Core Connector DT`).
5. Select your **Output Format** (e.g., `CSV (comma-delimited)`).
6. Select your **XSLT Version** (default: `XSLT 2.0 (recommended)`).
7. Paste your **Source XML** (or upload an XML file). Example:
   ```xml
   <Root>
     <Employee>
       <ID>90847</ID>
       <Name>Jane Doe</Name>
     </Employee>
   </Root>
   ```
8. *(Optional)* Fill in Expected Output, Field Mappings, and Additional Instructions.
9. Click **"Generate Transformation"**.
10. The chat shows a **single pre-filled prompt line**. **Press Enter** to run it.
11. Claude generates the complete XSLT stylesheet in the chat. Copy the completed XSLT directly from Claude's reply.

### What Claude Knows Automatically
- Correct Workday namespace declarations (`wd:`, `is:`, `xtt:`, `etv:`) for each category.
- XSLT version-specific rules (e.g., XSLT 1.0 does not support `xsl:for-each-group`).
- Output format rules (e.g., CSV requires `xsl:output method="text"`, pipe delimiters for fixed-width).
- Production-quality patterns from its built-in knowledge base.

---

## 8. Module 2: Workday Studio Integration Generator

### Purpose
Scaffolds a complete Workday Studio integration project from a design specification document. Claude generates two files:
- **Assembly XML (`.clara`)**: The Spring Beans XML file defining all integration components, connector steps, endpoints, and data flows.
- **Assembly Diagram XML (`.assembly-diagram.xml`)**: The graphical layout coordinates that position each component cleanly on Workday Studio's visual canvas.

### Form Fields

| Field | Required? | Description |
| :--- | :--- | :--- |
| **Design Document** | Required (or provide instructions) | Upload your complete integration design specification. Supported formats: PDF, DOCX, XLSX, XLS, CSV, TXT, MD, XML, XSL. Claude reads the **entire document** to understand the integration requirements. |
| **Additional Instructions** | Optional | Custom rules, naming conventions, specific steps, component positions, or anything to add beyond the design document. Example: *"Pos 1: SFTP Inbound, Pos 2: XML Splitter, Pos 3: Web Service Call"*. |

### Step-by-Step Walkthrough

1. In Claude Code, type **`Open Studio and run listener`**.
2. **Allow every permission pop-up** that appears — these are required for the Studio listener to function.
3. The Studio widget opens with a listener running in the background.
4. **Drag and drop your design document** onto the upload area (or click to browse).
   - Example quick test: Upload a simple `.txt` file containing:
     > *"SFTP inbound integration fetching worker profiles, splitting records, and sending updates to Workday using the Import_Service_Deliveries web service operation."*
5. *(Optional)* Type **Additional Instructions** for extra rules. Example:
   ```
   Position 1: SFTP, Position 2: XML Splitter, Position 3: Web Service Call.
   ```
6. Click **"Generate Studio Integration →"**.
7. The chat shows a **single pre-filled prompt line**. **Press Enter** to run it.
8. Claude generates the complete Studio integration codebase and **saves the files** directly to the project folder — the `.clara` assembly XML and the `.assembly-diagram.xml` layout coordinates.

### What Claude Knows Automatically
- The complete `CLAUDE.md` Studio Generation Protocol (multi-step build process with checklist verification).
- Direction-specific rules for **Inbound**, **Outbound**, and **Bi-directional** integrations.
- Production assembly blueprints from real Workday Studio projects (e.g., `INT2001b_ADP_Vista`, `INT502_Willis_Towers_Watson`, `INT506e_Fidelity_ESPP`, `INT111 GGI`).
- Component library: SFTP connectors, XML Splitters, Aggregators, Web Service Calls (MWS), Local In/Out endpoints, Java Hashmaps, fault handling blocks.
- Graphical canvas coordinate placement formulas for the `.assembly-diagram.xml`.
- Checklists for each direction (Inbound Checklist, Outbound Checklist, Bi-directional Checklist).

---

## 9. Module 3: BIRT Report Design Generator

### Purpose
Generates a complete, deployable Eclipse BIRT `.rptdesign` report layout XML. You provide a visual sample of what the report should look like (as a PDF), the data it needs (sample XML), and the schema (XSD), and Claude writes the full `.rptdesign` file.

### Form Fields

| Field | Required? | Description |
| :--- | :--- | :--- |
| **Sample Layout (PDF)** | Required | Upload a PDF showing the visual design of the target report (tables, columns, headers, logos, page layout). Claude reads this to understand the visual structure. |
| **Source Data XML** | Required | Either **Upload** an XML file or switch to **"Paste Raw XML"** mode to paste your Workday Custom Report XML data feed directly. This is the data the report will display. |
| **Source XSD Schema** | Required | Either **Upload** an XSD file or switch to **"Paste Raw XML"** mode to paste the XSD schema defining field types and structure. |

### Step-by-Step Walkthrough

1. In Claude Code, type **`Open the BIRT report designer`** to launch the BIRT widget.
2. Allow any permission pop-ups that appear.
3. **Upload your visual PDF layout** — this is a sample or screenshot of what the report should look like.
4. **Provide the XML data**:
   - Click **"Upload File"** to drop an XML file, **OR**
   - Click **"Paste Raw XML"** and paste your sample XML directly. Example:
     ```xml
     <Report_Data>
       <Report_Entry>
         <Employee_ID>10098</Employee_ID>
         <Legal_Name>John Smith</Legal_Name>
       </Report_Entry>
     </Report_Data>
     ```
5. **Provide the XSD schema**:
   - Upload an XSD file, **OR** paste it directly. Example:
     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
       <xsd:element name="Report_Data"/>
     </xsd:schema>
     ```
6. Click **"Generate BIRT Report"**.
7. The chat shows a **single pre-filled prompt line**. **Press Enter** to run it.
8. Claude writes the complete `.rptdesign` XML layout that you can directly deploy to Workday.

### What Claude Knows Automatically
- The complete `BIRTClaude.md` protocol — detailed BIRT report design patterns, element ID sequencing rules, styling guidelines, data source binding conventions, and table/grid layout structures.

---

## 10. Module 4: Web Services SOAP Request Builder

### Purpose
Builds ready-to-use Workday Web Service SOAP request XML envelopes. The Hub includes a built-in database of **100+ standard Workday API operations** with their base SOAP request templates. You select the operation, specify your field mappings, and Claude generates the fully populated SOAP payload.

### Available Operations (Partial List)
The dropdown includes operations such as:
- `Change_Legal_Name`, `Change_Preferred_Name`, `Change_Work_Contact_Information`
- `Change_Emergency_Contacts`, `Add_Dependent`, `Change_Government_IDs`
- `Terminate_Employee`, `Create_Position`, `Edit_Position`, `Close_Position`
- `Request_Compensation_Change`, `Request_Leave_of_Absence`
- `Import_Request_One-Time_Payment`, `Edit_Worker_Additional_Data`
- `Contract_Contingent`, `Rehire_Contingent_Worker`
- `Bulk_Import_Register_Asset`, `Cancel_Requisition`
- …and many more (100+ operations total)

### Form Fields

| Field | Required? | Description |
| :--- | :--- | :--- |
| **Web Service Operation** | Required | Select the Workday API operation from the dropdown (e.g., `Change_Legal_Name`, `Terminate_Employee`). |
| **WSDL Version** | Required | Select the Workday Web Services API version. Options: `v43.0`, `v42.0`, `v41.0`, `v40.0`. |
| **Field Mapping / Requirements** | Required (or upload design doc) | Describe how fields should be populated in the SOAP payload. Example: *"Worker Reference = Employee ID from source file, Legal Name = First + Last name"*. |
| **Design Document** | Optional | Upload a requirements document (PDF, DOCX, XLSX, TXT) with detailed field mapping specifications. |

### Step-by-Step Walkthrough

1. In Claude Code, type **`Open the Web Service builder`** to launch the SOAP Builder widget.
2. Allow any permission pop-ups that appear.
3. Select the **Operation** from the dropdown (e.g., `Change_Legal_Name`).
4. Select the **WSDL Version** (e.g., `v43.0`).
5. Type your **Field Mapping** requirements. Example:
   ```
   Worker Reference -> Employee_ID from source file
   Legal Name -> First_Name + " " + Last_Name
   Country -> "US"
   Effective Date -> Current date
   ```
6. *(Optional)* Upload a design document with detailed specifications.
7. Click **"Generate Web Service Request"**.
8. The chat shows a **single pre-filled prompt line**. **Press Enter** to run it.
9. Claude returns the fully configured SOAP request envelope XML with all field mappings applied and correct Workday namespace conventions.

### What Claude Knows Automatically
- The base SOAP XML template for each operation (loaded from the built-in `WSS_entries.xlsx` database).
- Standard Workday namespace conventions for SOAP envelopes.
- Field structure and nesting patterns for each operation type.

---

## 11. How It Works Behind the Scenes

Here is what happens each time you click **Generate** in any module:

```
YOU (in the Widget Panel)                    CLAUDE (in the Chat Area)
─────────────────────────                    ──────────────────────────
1. Fill out the form                         
2. Upload files (if any)                     
3. Click "Generate"                          
        │                                    
        ▼                                    
4. Widget sends your inputs                  
   to the MCP server                         
        │                                    
        ▼                                    
5. Server reads your documents,              
   applies Workday-specific rules,           
   loads production templates,               
   and packages enriched context             
        │                                    
        ▼                                    
6. A single pre-filled prompt line           6. Claude receives the enriched
   appears in chat ──────────────────────►      context automatically
                                             
7. You press Enter on that line              7. Claude generates production-
                                                ready code in the chat
                                             
                                             8. Files are saved to the project
                                                folder (Studio) or you copy
                                                from chat (XSLT / SOAP)
```

**Key point**: You don't need to type any prompts manually. The visual form + the MCP server's knowledge engine handle everything. Claude receives a rich, structured specification — not just your raw text — so the generated code is production-quality from the start.

---

## 12. Where Are My Generated Files Saved?

When Claude generates code, it appears in the **chat window** for you to copy.

For **Studio Integrations**, Claude also **automatically saves files to disk** in the selected working folder. Generated files are saved to:
```
<Claude MCP folder>/Generated documents/<integration_name>/
```

For example:
```
Claude MCP/Generated documents/INT502_Willis_Towers_Watson/
├── INT502.clara
└── INT502_assembly-diagram.xml
```

You can also ask Claude in chat: *"Save this to disk"* and it will use the built-in file saver to write the code directly to your `Generated documents/` folder.

---

## 13. The Knowledge Base — What Claude Knows

The Hub ships with a curated knowledge base that Claude consults during every generation. This is stored in the `claude_folder/` directory:

### Integration Protocols
- **`CLAUDE.md`** — The master Workday Studio generation protocol. Defines the multi-step build process: design review → checklist verification → process flow → code generation.
- **`BIRTClaude.md`** — The BIRT report design protocol with styling guidelines, element ID rules, and layout structure patterns.

### Production Reference Assemblies
Real-world Workday Studio assembly blueprints that Claude uses as structural templates:

| Direction | Reference Projects |
| :--- | :--- |
| **Inbound** | `INT2001b_ADP_Vista`, `INT502_Willis_Towers_Watson`, `INT506e_Fidelity_ESPP` |
| **Outbound** | `INT2001a_ADP_Vista`, `INT2001ab_ADP_Vista` |
| **Bi-directional** | `INT111 GGI`, `INT2001b_ADP_Vista` |

### Instruction Documents
Detailed Workday integration instructions located in `claude_folder/Instructions/`:
- `Instructions.txt` — General Studio integration build instructions
- `Inbound integration.txt` — Inbound-specific component patterns
- `Outbound integration.txt` — Outbound-specific component patterns
- `Bi-directional integration.txt` — Bi-directional flow patterns
- `Inbound checklist.txt` / `Outbound checklist.txt` / `Bi-directional checklist.txt` — Verification checklists
- `Concepts in each KB.txt` — Workday Studio component glossary
- `Webservices.txt` — Web Service operation details
- `API Calls to external endpoints.txt` — External API integration patterns
- `Hashmaps and XSLT3.txt` — Java Hashmap and XSLT 3.0 patterns

### Web Service Database
- **`web_service_shells/WSS_entries.xlsx`** — Contains 100+ standard Workday Web Service API operations with their base SOAP XML request templates.

---

## 14. Sharing the Tool With Your Team

Sharing the Hub with teammates is straightforward — no build steps or packaging scripts are needed.

### For All Users (End Users and Developers)
Simply share the `WorkdayMCP.exe` file. Recipients follow the same one-time setup:
1. Create a **"Claude MCP"** folder and place `WorkdayMCP.exe` inside it.
2. Double-click `WorkdayMCP.exe` and wait for the SUCCESS message.
3. Press Enter to close the console.
4. Fully quit and restart Claude.
5. Verify the server shows **running** in **Settings → Developer → Local MCP servers**.
6. In Claude Code, use **Select Folder** to choose the "Claude MCP" folder.

No Python installation, no `pip install`, and no `npm build` steps are required for end users.

---

## 15. Troubleshooting & FAQ

### The Workday Transformation Assistant does not appear in Settings → Developer
**Cause**: The .exe has not been run yet, or Claude was not fully restarted after registration.  
**Fix**:
1. Double-click `WorkdayMCP.exe` again and confirm you see the SUCCESS message.
2. Press Enter to close the console.
3. Fully quit Claude (from the taskbar or system tray) and reopen it.
4. Check **Settings → Developer → Local MCP servers** again.

### The server shows a status other than "running" in Settings → Developer
**Cause**: The MCP server process stopped or failed to start.  
**Fix**:
1. Double-click `WorkdayMCP.exe` again to re-register.
2. Quit and restart Claude completely.
3. Verify the status changes to **running**.

### I clicked "Generate" but the chat showed no pre-filled prompt line
**Cause**: The context transfer may not have completed, or the listener was not active.  
**Fix**: In Claude Code's chat area, type one of these:
- *"Listen for UI session"*
- *"Generate"*
- *"Run the listen_for_ui_session tool"*

Claude will pick up your submission and generate the code.

### Permission pop-ups keep appearing and blocking the workflow
**Cause**: Claude Code requires explicit permission for MCP tool calls.  
**Fix**: Click **Allow** on every permission pop-up. If you want to avoid repeated prompts, you can grant persistent permissions in Claude Code's settings for the Workday Transformation Assistant tools.

### The widget panel opens but shows a blank page
**Cause**: The server may not be fully running yet.  
**Fix**:
1. Re-run `WorkdayMCP.exe` and confirm the SUCCESS message.
2. Restart Claude Code fully.
3. Re-open the widget by typing the launch command again.

### How do I update to a newer version?
1. Download the new `WorkdayMCP.exe`.
2. Replace the old `.exe` in your "Claude MCP" folder with the new one.
3. Double-click the new `.exe` and wait for the SUCCESS message.
4. Press Enter, then fully quit and restart Claude.

### After running the .exe, MCP files are not showing up in Claude Settings?
This is typically a path issue. Take the path generated during the execution of the `.exe` file (e.g., `C:\Users\abc\AppData\Roaming\Claude`) and refer to the `claude_desktop_config.json` file. Copy the first node of the JSON (`mcpServers`) into the config file found at **Settings → Developer → Connector → Edit Config** (which will be at a path similar to `C:\Users\abc\AppData\Local\Packages\Claude_xyz\LocalCache\Roaming\Claude`).

### Can I use this in a web browser instead of Claude Code?
The generators are designed to work within Claude Code using the MCP server integration. The widget panels are embedded in Claude Code's interface and depend on the MCP tools for context injection and file saving.

---

*Workday Integration Hub — Accenture · Workday Practice*
