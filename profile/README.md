<p align="center">
  <img src="https://raw.githubusercontent.com/RAEN-DT/.github/main/Assets/RaenHeader.png" width="820" alt="RAEN Digital Tools — The Bridge between AI and BIM"/>
</p>

<p align="center">
  <a href="https://www.raendt.com/">RAEN Digital Tools</a> &middot;
  <a href="mailto:info@raendt.com">info@raendt.com</a> &middot;
  Madrid, Spain
</p>

### 📥 Request your 30-day **Trial** here:
Contact: **[info@raendt.com](mailto:info@raendt.com)** to request access.

---

## 🏢 Who we are

**RAEN Digital Tools** is a software company specialised in automation and artificial intelligence
for BIM environments. We come from digital engineering, not from generic software — the tooling
here was built while coordinating real projects, and it shows in what it chooses to solve.

We work three ways: as a **product** you install, as an **engine** partners extend, and as an
**implementation project** we run alongside your team.

| | |
| :--- | :--- |
| 🧭 **Specialised team** | Digital engineering and software development working together, continuously. |
| 🛠️ **Our own technology** | Tooling standardised over years of real BIM coordination, not adapted from elsewhere. |
| 📈 **Scalable by design** | Solutions built to grow with your organisation, at any project size. |
| 🤝 **Continuous support** | We stay from design through deployment and into the evolution of the solution. |

---

## ⚙️ What we do

Most of the hours a BIM team loses go into work that is precise, repetitive and impossible to
delegate: chasing clashes, checking a model against the standard, pulling quantities, rebuilding
the same report every month. We turn that work into something your team asks for in plain language
and gets back in minutes — and we stay to make sure it holds up on the next project.

| | |
| :--- | :--- |
| 🔁 **BIM automation** | Repetitive coordination, auditing and reporting work, automated inside the Autodesk tools your team already uses. |
| 🤖 **AI integration** | Connect your AI assistant to live models so it can query, analyse and modify them — not just talk about them. |
| 🧩 **Custom development** | Workflows encoding your own engineering criteria: tolerance rules, BEP standards, budget structures. |
| 🎓 **Deployment & training** | Company-wide rollout, with the people side handled as seriously as the technical one. |

---

## 🚀 PyNET Platform

<p align="center">
  <img src="https://raw.githubusercontent.com/RAEN-DT/PyNet/main/Assets/PyNetLogo.png" width="360" alt="PyNET Platform"/>
</p>

Our platform lets an AI assistant operate **Autodesk Navisworks, Revit and Civil 3D** directly.
You describe a task in your own words; the assistant writes the Python, it runs **inside the live
model**, and when the Autodesk API rejects something the error comes back and the script gets
rewritten.

> It executes, reads the result, and acts on it — inside the process, on your machine.
> Nothing is handed to you to paste.

<p align="center">
  <img src="https://raw.githubusercontent.com/RAEN-DT/.github/main/Assets/PyNETWorkflow.png" width="900" alt="PyNET workflow: from natural language through the AI client and the PyNET Bridge into Revit, Navisworks Manage and Civil 3D"/>
</p>

Every arrow above stays on your machine — the bridge, the plugin and the viewer all communicate
locally. The only thing that ever leaves is the conversation you have with the AI provider you
chose.

<p align="center">
  <a href="https://github.com/RAEN-DT/PyNet/releases"><img src="https://img.shields.io/github/v/release/RAEN-DT/PyNet?label=release&color=f78166" alt="Release"/></a>
  <a href="https://pypi.org/project/pynet-mcp-bridge/"><img src="https://img.shields.io/pypi/v/pynet-mcp-bridge?label=pypi&color=2b7489" alt="PyPI"/></a>
  <img src="https://img.shields.io/badge/python-3.10%2B-blue" alt="Python"/>
  <img src="https://img.shields.io/badge/platform-Windows-lightgrey" alt="Windows"/>
  <img src="https://img.shields.io/badge/hosts-Navisworks%20%C2%B7%20Revit%20%C2%B7%20Civil%203D-orange" alt="Hosts"/>
  <img src="https://img.shields.io/badge/MCP-compatible-8A2BE2" alt="MCP"/>
</p>

---

## 🔗 The repositories

PyNET is not one monolithic plugin. It is a handful of pieces that each do one job well — the
engine that runs inside Autodesk, the server that talks to your AI, and the knowledge base that
teaches it the API. Each lives in its own repository, so you can install only what you need and
see exactly what runs on your machine.

<p align="center">
  <img src="https://raw.githubusercontent.com/RAEN-DT/PyNet/main/Assets/PyNetPlatformStructure.png" width="880" alt="PyNET Platform structure"/>
</p>

| | Repository | What it is |
| :--- | :--- | :--- |
| ⚙️ | **[PyNet](https://github.com/RAEN-DT/PyNet)** | The plugin. Hosts the embedded Python.NET engine inside Navisworks, Revit and Civil 3D, plus the ribbon/UI layer the AI can extend at runtime. |
| 🛡️ | **[PyNetBridge](https://github.com/RAEN-DT/PyNetBridge)** | The MCP server. Exposes the platform to any MCP-compatible AI client and statically validates every script *before* it reaches Autodesk. On PyPI as `pynet-mcp-bridge`. |
| 📚 | **[PyNetLibrary](https://github.com/RAEN-DT/PyNetLibrary)** | The AI's knowledge base — **125+ production-tested reference scripts**, **189 stub modules** mirroring the Autodesk .NET APIs, and the workflow skills behind the use cases above. |

---

## 🎯 What PyNET can do

These are not demos built for a slide. They are the workflows our clients run on live projects,
each one encoding the judgement an experienced coordinator applies — which interferences to
approve, which parameters a model must carry, which design alternative wins. The assistant runs
the whole process, not a single command.

<p align="center">
  <img src="https://raw.githubusercontent.com/RAEN-DT/.github/main/Assets/UseCases.png" width="900" alt="PyNET use cases: clash coordination, quality checks and generative design"/>
</p>

### 🎬 See it running

| Video | What you will see |
| :--- | :--- |
| **[Autonomous BIM coordination](https://www.youtube.com/watch?v=Vw7ig8TItng)** | An AI client driving **Revit and Navisworks at the same time**: audits both models, triages the clash matrix by tolerance, generates the sleeves in Revit — and when the Revit API throws a type exception, reads the stack trace, rewrites the script and finishes. |
| **[AI coordination in Navisworks](https://www.youtube.com/watch?v=Sfq9iXJFacU)** | The coordination loop end to end inside a federated model. |
| **[Setup with Codex](https://youtu.be/HdmbCO_pTN0)** | Wiring the bridge to an AI client and querying a live model. |
| **[Configuring the plugin](https://www.youtube.com/watch?v=3eR5GAOkEug)** | First run in Navisworks: licence, Python path and script folder. |

---

## 🧊 PyNET Viewer for VS Code

<p align="center">
  <img src="https://raw.githubusercontent.com/RAEN-DT/PyNetVSCode/main/Assets/PynetViewer.png" width="360" alt="PyNET Viewer"/>
</p>

The **[PyNET Viewer extension](https://marketplace.visualstudio.com/items?itemName=RAENDT.pynet-viewer)**
puts a 3D BIM viewer inside the editor and sets up the MCP bridge for every AI client it finds —
one install covers both. To install it, open the **Extensions** panel in VS Code and search for
*PyNET Viewer*.

Export a `.pnt` package — a single self-contained file with the federated models and the clash
data — and open it in VS Code. Spatial tree, properties, sections, measurements, clash results.

### 🤝 The assistant and the viewer, talking to each other

The viewer is not a passive window. It is wired to the same MCP bridge as your Autodesk hosts, so
the assistant can **drive the scene while it explains it** — isolate a discipline, highlight both
sides of a clash, read an element's properties, refit the camera. You ask in the chat panel; the
answer appears in the text *and* in the model beside it.

<p align="center">
  <img src="https://raw.githubusercontent.com/RAEN-DT/PyNetVSCode/main/Assets/Pynet_view_AI.png" width="900" alt="Claude breaking down clash counts in the VS Code chat panel while the PyNET Viewer highlights the clashing pair in red and green"/>
</p>

Above: the assistant breaks down 3,706 clashes across five federated models, and the element pair
it is describing is already highlighted in the viewer — red against green — without anyone touching
the 3D view.

**No licence required to open and explore a package.**

---

## 🔑 Licensing

PyNET Platform is distributed via the Freemius platform to ensure secure licensing and controlled
access.

| License | Description |
| :--- | :--- |
| **Trial** | 30-day trial access to a basic license. |
| **Basic** | Access to a basic license for the extension to integrate the Autodesk products available individually. |
| **Pro** | Access to a Pro license for the extension to integrate the Autodesk products available at the same time. |
| **Enterprise** | Integrate PyNET in your company with an implementation project service. |

**Start with a 30-day Trial.** Write to **[info@raendt.com](mailto:info@raendt.com)** and we set you
up with full access. If it fits, you choose a plan; if not, you do nothing.

---

## 🔒 Security by design

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

<sub>PyNET Platform is intended for professional use in BIM automation. Users are responsible for
reviewing and validating AI-generated scripts before applying them in production.</sub>

<p align="center">
  <br/>
  <img src="https://raw.githubusercontent.com/RAEN-DT/PyNet/main/Assets/RAENDigitalTools.png" alt="RAEN Digital Tools" width="180"><br/>
  <sub>© 2026 RAEN Digital Tools · Todos los derechos reservados.<br/>
  Obra inscrita en el Registro de la Propiedad Intelectual de la Comunidad de Madrid.</sub>
</p>
