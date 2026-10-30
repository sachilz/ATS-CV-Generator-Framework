# AI-Powered ATS CV Generator System 🚀

An automated, intelligent, and ATS-optimized CV generation framework designed to work seamlessly with **Claude (Artifacts / Canvas)**, **LaTeX**, and **Overleaf**.

This repository provides a modular, prompt-engineered system that tailors a **strictly one-page, ATS-compliant CV** for any given Job Description (JD) using the candidate's personal markdown profile as the **single source of truth** — eliminating AI hallucinations, formatting headaches, and multi-page overflow.

---

## 📌 Key Highlights

- **🛡️ Zero Hallucinations**: Claude is strictly constrained to facts from your candidate profile file. It will never invent fake metrics, inflated numbers, or non-existent credentials.
- **📄 Strictly One-Page A4 Rule**: Built-in LaTeX typography knobs and spacing constraints guarantee that the CV stays on exactly one page, filling neatly to the bottom margin.
- **🎯 Dynamic JD Alignment & ATS Title Matching**:
  - Directly matches the **exact Job Title** in the header subtitle and professional summary for 100% ATS score.
  - Weaves in key JD qualifying keywords (e.g., "motivated", "collaborative", "responsive web applications") into the professional summary.
  - Automatically identifies and picks the **4 best-matching projects** for the target role.
  - Prioritizes technical skills matching the JD requirements while retaining project tools.
  - Selects the **2–3 strongest certifications** directly relevant to the vacancy.
- **⚡ Claude Canvas / Artifact Integration**: The complete LaTeX code is delivered directly in Claude’s side Artifact panel (`CV_[CandidateName].tex`) for instant one-click copying — keeping the chat clean.
- **🔍 ATS Keyword Review**: Highlights keywords successfully matched in the CV and flags missing keywords from the JD so you can review and manually adjust if needed.
- **🧩 Reusable for Any Candidate**: Fully parameterized; works with any profile file without hardcoded dependencies.

---

## 📂 Repository Structure

```text
Sachintha-CV-Profile/
├── README.md                      # Root documentation (this file)
│
├── Personal_Info/                 # Candidate data directory
│   └── info.md                    # Single source of truth containing candidate's facts,
│                                  # skills, projects, certifications, and experience
│
├── CV_Guidelines/                 # Layout and design specification
│   └── cv_guide.md                # Typography rules, spacing knobs, Overleaf guide,
│                                  # and base LaTeX template
│
└── Instructions/                  # AI agent orchestration
    └── instruction.md             # Master system instructions directing Claude
                                   # on how to parse, validate, and build the CV
```

---

## 🛠️ How It Works (Step-by-Step)

```mermaid
flowchart TD
    A["Candidate Profile\n(Personal_Info/info.md)"] --> D["Claude 3.5 / 3.7\nwith instruction.md & cv_guide.md"]
    B["CV Guidelines\n(CV_Guidelines/cv_guide.md)"] --> D
    C["Instructions\n(Instructions/instruction.md)"] --> D
    
    D --> E{"Info Validation Check"}
    E -- Missing Critical Details --> F["Ask User to Provide Missing Info\nor 'Proceed with what I have'"]
    F --> G["User Provides JD"]
    E -- Info Complete --> G
    
    G --> H["Intelligent Matching &\nLaTeX Generation"]
    H --> I["Claude Artifact / Canvas Panel\n(CV_CandidateName.tex)"]
    H --> J["Chat Output:\nATS Keyword Review (Matched vs Missing)"]
    
    I --> K["Overleaf / LaTeX Engine"]
    K --> L["One-Page ATS-Optimized PDF 📄"]
```

---

## 🚀 Quick Start Guide

### Step 1: Update Your Candidate Profile
Navigate to [`Personal_Info/info.md`](Personal_Info/info.md) (or create your own profile markdown file) and ensure your facts are updated:
- Contact information and social profile links
- Concise professional summary (3–4 lines)
- Grouped technical skills and tools
- Projects with 1 factual bullet point and technology tags
- Degree, relevant coursework, and high school qualifications
- Course certificates (under *Certifications and Training*)
- Experience and community leadership roles

### Step 2: Start a New Chat with Claude
Open Claude and attach the following **3 files** in your initial prompt:
1. `Instructions/instruction.md`
2. `CV_Guidelines/cv_guide.md`
3. Your Profile file (e.g., `Personal_Info/info.md`)

> **Initial Prompt to Claude:**
> *"Read the attached instructions, guidelines, and candidate profile. Please confirm once you are ready for the Job Description."*

### Step 3: Upload the Job Description (JD)
Once Claude acknowledges:
1. Paste the target **Job Description (JD)** text or upload a screenshot/document of the job posting.
2. If any critical info is missing from your profile, Claude will notify you. You can either supply the missing info or reply:
   > *"Proceed with what I have."*

### Step 4: Get Your Tailored CV
Claude will output:
- **Canvas / Artifact Panel:** Full, production-ready LaTeX source code (`CV_[CandidateName].tex`).
- **Chat:** ATS Keyword Review detailing matched keywords and any gaps.

### Step 5: Compile in Overleaf
1. Log in to [Overleaf](https://www.overleaf.com).
2. Click **New Project** → **Blank Project**.
3. Replace the default template with the LaTeX code from Claude's canvas.
4. Click **Recompile** and download your ATS-ready PDF!

---

## 📐 Layout & Typography Rules (Built-in)

| Element | Specification | Purpose |
|---|---|---|
| **Font** | Latin Modern (`lmodern`, 10pt body) | Timeless, clean, academic readability |
| **Page Length** | Strictly 1 A4 Page | Eliminates weak spillover pages |
| **Margins** | Symmetric (Left = Right = 0.45in, Top = Bottom = 0.45in) | Perfectly equal borders on all 4 sides |
| **Colors** | `linkblue` (links) & `techblue` (tool tags) | Subtle professional contrast without breaking ATS |
| **Projects** | Exactly 4 projects, 1 bullet each | High-impact focus for 10–20 second scans |
| **Tech Tags** | Strictly 1 line (6–8 tags max, extends towards GitHub text margin) | Never wraps to a 2nd line; prevents 2-page overflow |
| **Project Gap** | `\vspace{5pt}` after each project | Visual breathing room between experience blocks |
| **Header** | Name, exact JD job title, contact & uniform domain links (`linkedin.com/in/...`, `github.com/...`, `medium.com/@...`, `youtube.com/@...`) | Professional consistency & guaranteed ATS recognition |
| **Headings** | ATS-compliant names (`Professional Experience`) | Ensures ATS parsers recognize work history |

---

## ⚙️ Overflow Troubleshooting Knobs

If a CV ever renders across two pages on Overleaf, apply adjustments in this exact priority order:

1. **Trim Technology Tags**: Ensure each Technologies line fits on strictly 1 line (drop tags if it wraps to line 2).
2. **Adjust Section Spacing**: Tuned default is `\titlespacing*{\section}{0pt}{5.5pt}{2pt}` (adjust between 5pt and 6.5pt).
3. **Adjust Project Gap**: Default project gap is `\vspace{3.5pt}` (adjust to 3pt if needed).
4. **Adjust Bullet Spacing**: Default itemize is `itemsep=0pt,topsep=0.5pt`.
5. **Shorten Summary**: Trim one sentence from the professional summary.
6. **Trim Certifications**: Keep the 2 strongest certifications.

---

## 👤 Author & Maintainer

- **Sachintha Dilshan Madhushankha**
  - **Portfolio**: [sachilz.me](https://sachilz.me)
  - **LinkedIn**: [linkedin.com/in/sachilz](https://www.linkedin.com/in/sachilz)
  - **GitHub**: [@sachilz](https://github.com/sachilz)
  - **YouTube**: [@NextOpz](https://www.youtube.com/@NextOpz)

---

## 📄 License

This project is open-source and free to adapt for personal and educational career development.

