
# 🤖 LLM-Driven Code_Aster Automation  
### A Showcase of My Work on AI-Assisted Structural Analysis  
*Amir Yarmohamadi — 2025*

---

## 🚀 Overview

This repository showcases **my contributions** to a joint project with  
**Saeideh Mohammadikish**, where we developed an **LLM-based automation pipeline for Code_Aster** using Python, LangChain, Gmsh, and Code_Aster.

The project connects **AI reasoning** with **finite element analysis**, enabling automatic generation of:

- geometry  
- mesh (.geo → .med)  
- Code_Aster `.comm` files  
- `.export` files  
- FE execution  
- post-processing and visualization  

All triggered through **natural-language input**.

The original project repository is hosted by Saeideh:  
👉 *(link to Saeideh’s repo)*

---

## 🧩 My Main Contributions

### 🔹 1. Architecture Design
Designed the multi-stage pipeline that transforms a natural-language request into a complete Code_Aster analysis:

1. Parameter extraction  
2. Geometry generation (Gmsh)  
3. Meshing  
4. `.comm` file creation  
5. `.export` file generation  
6. Solver execution  
7. Plotting and reporting  

---

### 🔹 2. Geometry Generator (Gmsh)
I developed the **Gmsh geometry generator** component (`geo_generator.py`):

- automatic beam geometry creation  
- element partitioning  
- parameter sanitation  
- mm/m conversion logic  
- workspace management  

---

### 🔹 3. Mesh Generator
Implemented meshing logic:

- structured 1D/2D mesh  
- element sizing  
- integration with the pipeline workflow  
- error handling & logging  

---

### 🔹 4. Code_Aster `.comm` Generator
This was one of the most technical parts of the project.

I implemented:

- complete FE definition  
- material assignment  
- section properties (rectangular section)  
- load and boundary conditions  
- time-history output commands  
- node/element selection logic  

---

### 🔹 5. Export File Generator
Automatic creation of `.export` files based on workspace structure.

Key features:

- auto-path linking for `.comm`/`.med`  
- standardized file names  
- run directory management  

---

### 🔹 6. AI Integration (LangChain + OpenAI)
I integrated the LLM layer:

- extraction of parameters from a natural sentence  
- tool routing (geometry → mesh → comm → export → run → visualize)  
- structured JSON outputs  
- hybrid agent mode  
- error-aware parsing  

---

### 🔹 7. Workspace Manager
I implemented the standardized workspace:

workspace/
├── model.geo
├── model.med
├── model.comm
├── model.export
├── results/

yaml
Copy code

This made the entire pipeline reproducible and clean.

---

## 🧪 Example Workflow

### User input:
simulate a 5m concrete beam, rectangular section 0.35m x 0.25m,
load 1300 N at the free end

mathematica
Copy code

### The LLM automatically:
1. extracts parameters  
2. creates geometry  
3. generates mesh  
4. writes `.comm`  
5. writes `.export`  
6. runs Code_Aster  
7. returns plots + result summary  

---

## 🧱 System Architecture (High-Level)

```mermaid
flowchart LR

A[User Request] --> B[LLM (OpenAI)]
B --> C{Tool Selection}

C -->|Geometry| G[Geometry Generator<br/>Gmsh]
C -->|Mesh| M[Mesh Generator]
C -->|.comm| D[Code_Aster COMM Generator]
C -->|.export| E[Export Generator]
C -->|Run| F[Code_Aster Solver]
F --> H[Results & Visualization]

G --> M --> D --> E --> F
📌 Features
Natural-language-driven FE analysis

Parameter extraction via LLM

Full automation: geometry → mesh → FE solver

Error-resistant pipeline

Modular Python architecture

Works with OpenAI API + LangChain

📸 Screenshots
(Add your images here, e.g. pipeline runs, plots, terminal screenshots)

Copy code
images/
 ├── pipeline_run.png
 ├── result_plot.png
 └── workspace_structure.png
🤝 Collaboration
This work was developed jointly with:

Saeideh Mohammadikish
(host of the main repository)

The full project is available at:
👉 (put GitHub link here)

📄 Report & Presentation (Optional)
You can include links to:

project report PDF

presentation slides

diagrams

any deliverable from the university

Example:

bash
Copy code
📄 Report (PDF): link  
🎤 Presentation Slides: link  
👨‍💻 Author
Amir Yarmohamadi
Structural Engineer → AI & Computational Mechanics
Politecnico di Torino

⭐ If useful, please give a star
Seeing support helps us continue improving the project.
