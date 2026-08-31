# Workday Integration Hub — Complete User Guide

Welcome to the **Workday Integration Hub**, your AI-powered assistant for building Workday integrations faster than ever. This guide walks you through everything from first-time setup to generating production-ready code — all from within Claude Desktop.

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

The Workday Integration Hub is a **visual dashboard that lives inside Claude Desktop**. When you open it, a beautiful slide-out panel appears on the right side of your chat. You fill out forms, upload design documents, and click **Generate** — Claude reads everything you provide, applies Workday-specific knowledge and production templates, and writes complete, deployable integration code directly in the chat window.

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
| **Python 3.10 or higher** | Download from [python.org](https://python.org). During installation, **check the box "Add Python to PATH"**. Verify by opening Command Prompt and typing `python --version`. |
| **Claude Desktop** | The official Claude Desktop application, installed and logged in with an active account. |
| **Node.js 18+** *(Optional)* | Only needed if you plan to modify the visual dashboard source code. Not required for normal use. |

---

## 4. First-Time Setup (Step by Step)

### Step 1: Extract the ZIP
Unzip the distribution folder to any convenient location on your computer. For example:
```
C:\Users\YourName\workday_hub
```

### Step 2: Install Python Dependencies
Open **Command Prompt** (cmd) and navigate to the **project root folder** (the folder containing `requirements.txt`):
```cmd
cd C:\Users\YourName\workday_hub
pip install -r requirements.txt
```

> ⚠️ **Common mistake**: Make sure you run this command from the **project root folder** — NOT from inside the `ui/` or `server/` subfolder. If you see "No such file or directory", you're in the wrong folder.

This installs the following packages automatically:
- `fastmcp` — The communication bridge between Claude Desktop and the Hub server.
- `pandas` & `openpyxl` — For reading Excel mapping files and the Web Services database.
- `python-docx` — For reading Word design documents (`.docx`).
- `pypdf` — For extracting text from PDF specification files.
- `tabulate` — For formatting tabular data.
- `lxml` — For advanced XML processing.

### Step 3: Register with Claude Desktop
In the **same Command Prompt window** (still in the project root), run:
```cmd
python server\server.py
```

You will see output like:
```
============================================================
   WORKDAY INTEGRATION ASSISTANT — AUTO REGISTRATION
============================================================
[*] Server Command: python
[*] Configuration target: C:\Users\...\AppData\Roaming\Claude\claude_desktop_config.json

[+] SUCCESS: Registered successfully with Claude Desktop!
[*] Please RESTART Claude Desktop completely to apply changes.

[+] Created quick-start prompt file: ...\INITIAL_PROMPT.txt
============================================================

Press Enter to exit...
```

Press **Enter** to close.

> 💡 **Alternative**: You can also run `setup_server.bat` by double-clicking it — it does Steps 2 and 3 automatically.

### Step 4: Restart Claude Desktop
This step is **critical**:
1. **Right-click the Claude icon** in the Windows system tray (bottom-right corner, near the clock) and click **Quit**.
2. Relaunch Claude Desktop.
3. Go to **Settings → Developer → MCP** and confirm that **"Workday Transformation Assistant"** shows a **green dot** next to it.

✅ **Setup is complete.** You're ready to use the Hub.

---

## 5. How to Open the Dashboard in Claude

Open any chat in Claude Desktop and type one of these commands:

> **"Launch the Workday dashboard"**
>
> **"Open workday home"**

Claude will process the request and display a small button labeled **"open widget"** on the right side of its chat response.

**You MUST click the "open widget" button.** This is what opens the visual dashboard panel on the right side of Claude Desktop.

```
+------------------------------------------+-------------------------------------------+
|  Claude Desktop Chat                     |  Workday Integration Hub (Widget Panel)   |
|                                          |                                           |
|  You: Launch the Workday dashboard       |  ┌───────────────────────────────────────┐ |
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

> 💡 **Shortcut**: You can also open individual modules directly by telling Claude:
> - *"Open the XSLT generator"*
> - *"Open Studio integration"*
> - *"Open the BIRT report designer"*
> - *"Open the Web Service builder"*

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

1. Click the **XSLT Generation** card on the Hub dashboard.
2. *(Optional but recommended)* Upload your design document — if you do, all other fields become optional.
3. Select your **Category** (e.g., `Core Connector DT`).
4. Select your **Output Format** (e.g., `CSV (comma-delimited)`).
5. Select your **XSLT Version** (default: `XSLT 2.0 (recommended)`).
6. Paste your **Source XML** (or upload an XML file). Example:
   ```xml
   <Root>
     <Employee>
       <ID>90847</ID>
       <Name>Jane Doe</Name>
     </Employee>
   </Root>
   ```
7. *(Optional)* Fill in Expected Output, Field Mappings, and Additional Instructions.
8. Click **"Generate Transformation"**.
9. A notification appears: **"✅ Context injected! Claude is compiling the XSLT in the chat panel."**
10. **Look at the left side of Claude Desktop** (the chat area). Claude is now writing the complete XSLT stylesheet.
11. Copy the generated XSLT from Claude's chat response and use it in your Workday integration.

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

1. Click the **Studio Integration** card on the Hub dashboard (or tell Claude *"Open Studio integration"*).
2. **Drag and drop your design document** onto the upload area (or click to browse).
   - Example quick test: Upload a simple `.txt` file containing:
     > *"SFTP inbound integration fetching worker profiles, splitting records, and sending updates to Workday using the Import_Service_Deliveries web service operation."*
3. *(Optional)* Type **Additional Instructions** for extra rules. Example:
   ```
   Position 1: SFTP, Position 2: XML Splitter, Position 3: Web Service Call.
   ```
4. Click **"Generate Studio Integration →"**.
5. A notification appears: **"✅ Context injected! Claude is compiling the Studio Spring Beans XML files in the chat panel."**
6. **Look at the chat area** in Claude Desktop. Claude will:
   - Ask you any gap questions (e.g., *"What is the SFTP hostname?"*, *"Is this inbound or outbound?"*) in a **single numbered list**.
   - Once you answer, Claude generates the complete `.clara` assembly XML and the `.assembly-diagram.xml` layout coordinates.
7. Copy the generated XML code from Claude's response.

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

1. Click the **BIRT Report Generation** card on the Hub dashboard.
2. **Upload your visual PDF layout** — this is a sample or screenshot of what the report should look like.
3. **Provide the XML data**:
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
4. **Provide the XSD schema**:
   - Upload an XSD file, **OR** paste it directly. Example:
     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
       <xsd:element name="Report_Data"/>
     </xsd:schema>
     ```
5. Click **"Generate BIRT Report"**.
6. A notification appears: **"✅ Context injected! Claude is compiling the BIRT .rptdesign code in the chat."**
7. **Look at the chat area.** Claude writes the complete `.rptdesign` XML layout that you can directly deploy to Workday.

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

1. Click the **Workday Web Service** card on the Hub dashboard.
2. Select the **Operation** from the dropdown (e.g., `Change_Legal_Name`).
3. Select the **WSDL Version** (e.g., `v43.0`).
4. Type your **Field Mapping** requirements. Example:
   ```
   Worker Reference -> Employee_ID from source file
   Legal Name -> First_Name + " " + Last_Name
   Country -> "US"
   Effective Date -> Current date
   ```
5. *(Optional)* Upload a design document with detailed specifications.
6. Click **"Generate Web Service Request"**.
7. A notification appears: **"✅ SOAP request template prepared!"**
8. **Look at the chat area.** Claude generates the complete SOAP request envelope XML with all field mappings applied and correct Workday namespace conventions.

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
   to the background server                  
        │                                    
        ▼                                    
5. Server reads your documents,              
   applies Workday-specific rules,           
   loads production templates,               
   and packages enriched context             
        │                                    
        ▼                                    
6. Enriched context is delivered             6. Claude receives the enriched
   to Claude via the bridge ──────────────►     context automatically
                                             
                                             7. Claude generates production-
                                                ready code in the chat
                                             
                                             8. You copy the code from chat
                                                and deploy it to Workday
```

**Key point**: You don't need to type any prompts manually. The visual form + the server's knowledge engine handle everything. Claude receives a rich, structured specification — not just your raw text — so the generated code is production-quality from the start.

---

## 12. Where Are My Generated Files Saved?

When Claude generates code, it appears in the **chat window** for you to copy.

Additionally, Claude can **automatically save files to disk**. Generated files are saved to:
```
<project_folder>/Generated documents/<integration_name>/
```

For example:
```
workday_hub/Generated documents/INT502_Willis_Towers_Watson/
├── INT502.clara
└── INT502_assembly-diagram.xml
```

You can ask Claude in chat: *"Save this to disk"* and it will use the built-in file saver to write the code directly to your `Generated documents/` folder.

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

### For End Users (Non-Developers)
Run the release packager to create a clean ZIP that only contains what users need:
```cmd
python package_release.py --build-ui
```
Output: `workday_hub_release_YYYYMMDD.zip`

Recipients only need to:
1. Unzip the archive.
2. Run `setup_server.bat` (or manually: `pip install -r requirements.txt` then `python server\server.py`).
3. Restart Claude Desktop.

### For Developers (Source Code)
Run the developer packager to share full source code (minus `node_modules` and `.venv`):
```cmd
python package_developer.py
```
Output: `workday_hub_dev_YYYYMMDD.zip`

Recipients will need to:
1. Unzip the archive.
2. Run `pip install -r requirements.txt` in the project root.
3. Run `cd ui && npm install && npm run build` to compile the React dashboard.
4. Run `python server\server.py` to register.

---

## 15. Troubleshooting & FAQ

### "pip install" says "No such file or directory" for requirements.txt
**Cause**: You're in the wrong directory.  
**Fix**: Navigate to the **project root folder** (the one containing `requirements.txt`, `server/`, and `ui/`):
```cmd
cd C:\Users\YourName\workday_hub
pip install -r requirements.txt
```

### Claude Desktop shows a red dot next to "Workday Transformation Assistant"
**Cause**: Server registration failed or Python can't find dependencies.  
**Fix**:
1. Open Command Prompt in the project root.
2. Run `python server\server.py` and check for error messages.
3. If you see import errors, re-run `pip install -r requirements.txt`.
4. If paths are wrong in the config, open `%APPDATA%\Claude\claude_desktop_config.json` and fix the absolute paths.
5. Restart Claude Desktop completely (quit from system tray first).

### I clicked "Generate" but nothing happened in the chat
**Cause**: The context transfer may not have completed, or Claude's listener wasn't active.  
**Fix**: In Claude Desktop's chat area, type one of these:
- *"Listen for UI session"*
- *"Generate"*
- *"Run the listen_for_ui_session tool"*

Claude will pick up your submission and generate the code.

### The widget panel opens but shows a blank page
**Cause**: The React dashboard hasn't been compiled yet (`ui/dist/` folder is missing).  
**Fix**:
```cmd
cd ui
npm install
npm run build
cd ..
```
Then restart Claude Desktop.

### Port 8000 is already in use
**Cause**: Another application is using port 8000.  
**Fix**: Close the other application, or change the port number in `server\server.py` (search for `start_ui_http_server(8000)` and change `8000` to another port like `8080`).

### How do I update to a newer version?
1. Download the new ZIP.
2. Extract it to a fresh folder (or overwrite the old one).
3. Re-run `pip install -r requirements.txt`.
4. Re-run `python server\server.py` to re-register.
5. Restart Claude Desktop.

### Can I use this in a web browser instead of Claude Desktop?
Yes! When the server is running, you can also open `http://localhost:8000` directly in Chrome or any browser. The visual dashboard works the same way. However, to get Claude's AI generation, you'll need to tell Claude to *"listen for UI session"* or *"connect to the listener"* in the Claude Desktop chat while you submit from the browser.

### After installing Executable file, MCP Files are not shoeing up in Claude Desktop Settings?
This is ideally a path issue - Please take the path generated during the execution of .exe file ("C:\Users\abc\AppData\Roaming\Claude") and refer to the json file "claude_desktop_config.json" and copy its First node of Json ( mcpServers ) into the file path from Settings > Developer > Connector > Edit Config ( It will be similar to  " C:\Users\abc\AppData\Local\Packages\Claude_xyz\LocalCache\Roaming\Claude" )
---

*Workday Integration Hub — Accenture · Workday Practice*
