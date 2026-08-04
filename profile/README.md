<p align="center">
  <img src="https://raw.githubusercontent.com/RAEN-DT/PyNet/main/Assets/PyNetLogo.png" width="360" alt="PyNET Platform"/>
</p>

<p align="center">
  <b>We make AI actually operate BIM software.</b><br/>
  Not a chatbot bolted onto Autodesk — an execution engine that writes, validates,<br/>
  runs and fixes its own Python inside Navisworks, Revit and Civil 3D.
</p>

<p align="center">
  <a href="https://github.com/RAEN-DT/PyNet/releases"><img src="https://img.shields.io/github/v/release/RAEN-DT/PyNet?label=release&color=f78166" alt="Release"/></a>
  <img src="https://img.shields.io/pypi/v/pynet-mcp-bridge?label=pynet-mcp-bridge&color=2b7489" alt="PyPI"/>
  <img src="https://img.shields.io/badge/python-3.10%20–%203.13-blue" alt="Python"/>
  <img src="https://img.shields.io/badge/platform-Windows-lightgrey" alt="Windows"/>
  <img src="https://img.shields.io/badge/hosts-Navisworks%20·%20Revit%20·%20Civil%203D-orange" alt="Hosts"/>
  <img src="https://img.shields.io/badge/MCP-compatible-8A2BE2" alt="MCP"/>
</p>

---

## The problem we solve

BIM automation has always meant one of two things: a plugin someone else wrote that does *almost*
what you need, or a script you write yourself, from scratch, every time the project changes.

PyNET removes that choice. You describe the task in your own words; the AI writes the Python,
it runs **inside the live model**, and if the Autodesk API rejects it, the error comes back and
the script gets rewritten. No export, no round-trip, no waiting on a developer.

> **This is not code generation.** The AI does not hand you a snippet to paste. It executes,
> reads the result, and acts on it — inside the process, on your machine.

---

## How it fits together

```mermaid
flowchart LR
    U["You<br/><i>natural language</i>"] --> AI["Your AI client<br/>Claude · Copilot · Codex · Cline</>"]
    AI <-->|MCP| B["PyNET Bridge<br/>static validator</>"]
    B <-->|Local Communication| P["PyNET Plugin<br/>Python.NET engine</>"]
    P <--> H["Navisworks · Revit · Civil 3D<br/>live model</>"]
    L["PyNET Library<br/>scripts + API stubs</>"] -.->|context| AI
    P -.->|.pnt package| V["VS Code Viewer"]
    AI <-->|drives the scene| V

style B fill:#D6EAF8,color:#34495E
style P fill:#FADADD,color:#5D4E4E
style H fill:#D5F5E3,color:#2E5E4E
style V fill:#E8DAEF,color:#4B3F72
```

Every arrow above stays on your machine. The bridge talks to the plugin over a Windows named pipe;
the viewer binds to `127.0.0.1`. The only thing that ever leaves is the conversation you have with
the AI provider you chose.

---

## The repositories

| | Repository | What it is |
| :--- | :--- | :--- |
| ⚙️ | **[PyNet](https://github.com/RAEN-DT/PyNet)** | The plugin. Hosts the embedded Python.NET engine inside Navisworks, Revit and Civil 3D, plus the ribbon/UI layer the AI can extend at runtime. |
| 🛡️ | **[PyNetBridge](https://github.com/RAEN-DT/PyNetBridge)** | The MCP server. Exposes the platform to any MCP-compatible AI client and statically validates every script *before* it reaches Autodesk. On PyPI as `pynet-mcp-bridge`. |
| 📚 | **[PyNetLibrary](https://github.com/RAEN-DT/PyNetLibrary)** | The AI's knowledge base — **125+ production-tested reference scripts**, **189 stub modules** mirroring the Autodesk .NET APIs, and the workflow skills below. |
| 🧊 | **[PyNetVSCode](https://github.com/RAEN-DT/PyNetVSCode)** | VS Code extension: embedded 3D BIM viewer + one-click setup of the bridge across every AI client you have installed. |

---

## Workflow Skills — engineering criteria, not just code

The library ships **domain workflows**, not only API examples. Each one encodes the judgement an
experienced coordinator would apply, so the AI runs the whole process instead of a single command.

| Skill | Host | What it does |
| :--- | :--- | :--- |
| **ClashDetection** | Navisworks | Builds the clash matrix from dynamic SearchSets, runs the tests, and auto-triages results against tolerance rules. |
| **ClashCoordination** | Navisworks → Revit | Reads reviewed clashes and generates the corresponding sleeves and floor openings in Revit — across two hosts, in one conversation. |
| **ClashToleranceComparison** | Navisworks | Re-runs the full matrix under different tolerances and produces a side-by-side Excel comparison. |
| **QCModelAudit** | Revit | Audits a model against BEP standards and issues a scored HTML + Excel report. |
| **QuantityTakeoff** | Revit | 5D extraction: matches model quantities to a reference budget and builds the measurement breakdown. |
| **WindSiting** | Civil 3D + GIS | Wind-farm siting for any zone in Spain — terrain, wind resource, exclusions and a suitability heat map as native Civil 3D objects. |
| **PowerlineFireRisk** | Civil 3D + GIS | Wildfire exposure of a transmission line from Sentinel-2 imagery, ranked by segment, draped on the terrain. |

---

## What it looks like in practice

In [this recorded session](https://www.youtube.com/watch?v=Vw7ig8TItng), an AI client connects to
**Revit and Navisworks at the same time** and runs a coordination cycle end to end:

1. **Audits** both models and flags the elements missing their classification parameter.
2. **Runs the clash matrix** and applies the tolerance rules to decide what to auto-approve.
3. **Generates the sleeves** in Revit — real geometry, rotated to match each pipe's angle.
4. **Hits a live Revit API type exception**, reads the stack trace, rewrites the script, and finishes.

Step 4 is the point. Everything before it, other tools do.

**More:** [AI coordination in Navisworks](https://www.youtube.com/watch?v=Sfq9iXJFacU) ·
[Setup with Codex](https://youtu.be/HdmbCO_pTN0) ·
[Configuring the plugin](https://www.youtube.com/watch?v=3eR5GAOkEug)

---

## Start here

> **Requirements:** Windows · Python **3.10 – 3.13** (3.14 is not supported yet by the `pythonnet`
> runtime) · the Autodesk host you want to drive.

**The one-step route** — the [VS Code extension](https://github.com/RAEN-DT/PyNetVSCode) installs
the bridge, configures every AI client it finds, and gives you the BIM viewer:

```
Extensions → search "PyNet Platform" → Install
```

**Bridge only:**

```powershell
pip install pynet-mcp-bridge
```

Detected and configured automatically: **Claude Desktop**, **Claude Code**, **GitHub Copilot**,
**Codex**, **Cline** and **Roo Code**. Full instructions live in
[PyNetBridge](https://github.com/RAEN-DT/PyNetBridge).

> **Bring your own AI.** PyNET is the integration layer, not a model vendor. No AI subscription is
> included — you connect the client and provider you already use.

---

## The viewer is free

<p align="center">
  <img src="https://raw.githubusercontent.com/RAEN-DT/PyNet/main/Assets/PyNetPlatformStructure.png" width="880" alt="PyNET Platform structure"/>
</p>

Export a `.pnt` package — a single self-contained file with the federated models and the clash
data — and open it in VS Code. Spatial tree, properties, sections, measurements, clash results.

The interesting part: your AI drives the same scene while it talks. It isolates the discipline it
is discussing, highlights both sides of a clash in red and green, and points at the element it just
measured. **No licence required to open and explore a package.**

---

## Licensing

| Tier | For |
| :--- | :--- |
| **Viewer** | Free, forever. Open and explore any `.pnt` package. |
| **Beta Trial** | 30 days of full platform access — request at [info@raendt.com](mailto:info@raendt.com). |
| **Basic** | One Autodesk host. |
| **Pro** | All hosts, simultaneously. |
| **Enterprise** | Company-wide deployment with an implementation project. |

---

## Security by design

The sandbox is **closed on purpose**, and we do not widen it for convenience.

* **Static validation** — every AI-generated script is parsed and checked against an import and
  call whitelist. Rejected scripts never leave the MCP server.
* **No network from the sandbox** — `os`, `subprocess`, `socket`, `urllib` and friends are blocked
  at the root. Code that legitimately needs them runs through its own launcher, outside the bridge.
* **Local execution only** — scripts run in-process, on your machine, on your models.
* **No telemetry** — no collection, no analytics, nothing sent to us or to any third party.
* **Human-executed, human-responsibility** — scripts you save to a ribbon button are yours to run;
  only the AI path is sandboxed.

Full policy: **https://privacy.raendt.com/**

---

## Support

| | |
| :--- | :--- |
| 🐛 **Bugs** | Open an issue in the relevant repository. |
| ❓ **Questions** | [PyNET FAQs](https://github.com/RAEN-DT/PyNet/wiki/PyNET-FAQs) |
| ✉️ **Contact** | [info@raendt.com](mailto:info@raendt.com) |
| 🖥️ **Platform** | Windows only — the Autodesk hosts and the named-pipe IPC are Windows-bound. |

---

<sub>PyNET Platform is intended for professional use in BIM automation. Users are responsible for
reviewing and validating AI-generated scripts before applying them in production.</sub>

<p align="center">
  <br/>
  <img src="https://raw.githubusercontent.com/RAEN-DT/PyNet/main/Assets/RAENDigitalTools.png" alt="RAEN Digital Tools" width="180"><br/>
  <sub>© 2026 RAEN Digital Tools · Todos los derechos reservados.<br/>
  Obra inscrita en el Registro de la Propiedad Intelectual de la Comunidad de Madrid.</sub>
</p>
