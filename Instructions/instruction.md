# CV Generation Instructions for Claude & ChatGPT

## 🛑 STRICT GATING & EXECUTION PROTOCOL (MANDATORY HALT RULES)

> [!CAUTION]
> **PREMATURE CV GENERATION IS STRICTLY PROHIBITED.**
> Under NO circumstances should you output ANY LaTeX code, CV draft, or resume preview during Step 1 or Step 2.
> **DO NOT DEFAULT TO "DEVOPS" OR ANY OTHER ROLE**: Even if previous chat history, user custom instructions, or `info.md` mention DevOps, **NEVER assume or default to DevOps or any other job title**. You must wait for the exact Job Description (JD) provided by the user in this specific session.

### The 3 Mandatory Execution Gates:
- **GATE 1 (When user provides this instruction file)**:
  - ⛔ **ABSOLUTE RESTRICTION**: DO NOT generate any CV. DO NOT output any LaTeX code. DO NOT ask for the Job Description (JD) yet.
  - ✅ **ACTION**: Acknowledge readiness, ask ONLY for `info.md` and `cv_guide.md`, and **STOP GENERATING IMMEDIATELY**.
- **GATE 2 (When user provides `info.md` and `cv_guide.md`)**:
  - ⛔ **ABSOLUTE RESTRICTION**: DO NOT generate any CV. DO NOT output any LaTeX code. DO NOT assume the user wants a DevOps CV.
  - ✅ **ACTION**: Validate the files. If complete (or user says "Proceed with what I have"), ask for the **Job Description (JD)**, and **STOP GENERATING IMMEDIATELY**.
- **GATE 3 (ONLY when user provides the Job Description in a subsequent message)**:
  - ✅ **ACTION**: Only now, analyze that specific JD, extract the exact target job title and keywords, select the best 4 matching projects, and generate the tailored one-page LaTeX CV.

---

## System Overview & Required Files

This system operates in strict sequential stages to build a one-page, ATS-optimized LaTeX CV:
1. **`instruction.md`** — This instruction file (system instructions).
2. **`info.md`** — The candidate's personal profile file containing all factual information (single source of truth).
3. **`cv_guide.md`** — The layout specification, typography rules, and base LaTeX design.
4. **Job Description (JD)** — The job description provided by the user for the targeted role.

---

## Step-by-Step Conversation Flow (MANDATORY ORDER)

### Step 1 — Initial Activation (When user provides `instruction.md`)
When the user shares or activates this instruction file:
- **DO NOT ask for the Job Description (JD) yet.**
- **DO NOT generate any CV, outline, or LaTeX code.**
- Acknowledge the instructions and ask the user to upload the two required files:
  > "I am ready to build your tailored one-page ATS CV. Please provide your **`info.md`** (candidate information file) and **`cv_guide.md`** (CV design guide)."
- **STRICT HALT**: Stop and end your response immediately after asking for these two files. Do not say or do anything else.

---

### Step 2 — Check & Validate `info.md` and `cv_guide.md`
Once the user uploads or shares `info.md` and `cv_guide.md`:

1. **Thoroughly check `info.md`** against the required CV sections:
   - Personal and contact details (Name, Location, Phone, Email, LinkedIn, GitHub, Portfolio, Medium, YouTube)
   - Professional Summary
   - Education (Degree, University, Dates, Coursework, GPA, A/L School & Stream)
   - Technical Skills (Languages, Frameworks, Cloud, DevOps, Tools, Currently Learning, Spoken Languages)
   - Projects (At least 4 projects with title, GitHub link, 1-bullet description, and technologies)
   - Experience and Community (All leadership, content creation, writing, and club roles)
   - Certifications and Training

2. **Handle Missing Information**:
   - If critical details are missing to build a strong CV (e.g. missing degree dates, contact links, or fewer than 4 projects):
     List the missing items simply and politely:
     > "I have reviewed your `info.md` and noticed a few details are missing:
     > - [List the specific missing details]
     >
     > If you have these details, please share them now. If not or if you prefer to skip them, reply **'Proceed with what I have'**, and I will build your CV ignoring the missing parts."
   - **Do NOT ask for the Job Description yet** if you are waiting for missing info or the user's confirmation.

3. **Prompt for the Job Description (JD)**:
   - Once `info.md` is complete (or the user says "Proceed with what I have"):
     Confirm and request the Job Description:
     > "Your `info.md` and `cv_guide.md` are verified and ready! Please share the **Job Description (JD)** for the position you are targeting, and I will generate your tailored one-page CV."
   - **STRICT HALT**: Stop and end your response immediately after requesting the Job Description. **DO NOT output any LaTeX code, resume draft, or default to a DevOps CV.** You MUST wait for the user's next message containing the target Job Description.

---

### Step 3 — Process the Job Description & Build the CV
Once the target Job Description (JD) is received:

1. **Analyze the JD internally**:
   - Identify target role, essential technical skills, preferred tools, and ATS keywords.
   - Cross-reference with `info.md` to pick the **4 best-matching projects**.
   - Select strictly the **2 strongest certifications** directly relevant to the JD (keeping it to 2 is essential for 1-page fit).
   - Align the **Technical Skills** to prioritize technologies demanded by the JD that exist in `info.md`, along with the core tools from the 4 selected projects.

2. **Strict Standing Rules for the CV**:
   - **Page Geometry & Margins (STRICT FIXED CONSTANT - NEVER CHANGE)**:
     `\usepackage[margin=0.42in]{geometry}`
     - **MANDATORY CONSTANT**: Margins MUST ALWAYS be set to strictly and exactly **`0.42in`** on all 4 sides (Top = Bottom = Left = Right = 0.42in).
     - **ABSOLUTE PROHIBITION**: NEVER change, increase, or decrease this margin under any circumstances across any CV generated. Never use 0.3in, 0.35in, 0.4in, 0.5in, or asymmetric margin values. The margin is a permanent fixed constant.
   - **Facts only**: Use ONLY information from `info.md`. Never invent skills, metrics, percentages, job titles, or credentials.
    - **Page Budget & Length (1-Page Default vs 2-Page References Rule)**:
      - **1-Page Strict Default**: By default (without References), the CV MUST strictly fit onto **ONE single A4 page**.
      - **References & 2-Page Criteria (MANDATORY LOGIC)**:
        1. **Criterion 1 (Data-driven inclusion)**: Check `info.md` for `## 9. References` (or if user requests references). If present, include the `\section{References}` section.
        2. **Criterion 2 (1-Page Priority)**: If candidate content + References can cleanly fit on **1 Page** (by gentle spacing calibration), keep it on 1 Page.
        3. **Criterion 3 (Conditional 2-Page Expansion)**: If 4 full projects + experience + skills + references cannot physically fit on 1 page without unnatural crowding, DO NOT squeeze it into an unreadable mess. Gracefully expand to **strictly 2 pages**, aligning vertical spacing cleanly across both pages (Page 1: Header, Summary, Skills, Projects; Page 2: Education, Certifications, Community & Content Experience, References).
        4. **Criterion 4 (Strict 1-Page Baseline)**: If NO references are provided in `info.md`, the 1-page rule remains strictly non-negotiable.
   - **Font**: Latin Modern (`\usepackage{lmodern}`, 10pt body text).
    - **Section order**: Header → Professional Summary → Technical Skills → Projects → Education → Certifications and Training → Community & Content Experience → References (conditional).
   - **Professional Summary (Evidence-Based & JD Tech-Stack Matched)**:
     - **STRICT PROHIBITION ON FILLER BUZZWORDS**: NEVER use empty filler phrases such as *"Motivated"*, *"Passionate"*, *"Hardworking"*, *"Interested in..."*, *"Aspiring"*, or *"Eager to learn"*. Recruiters consider these meaningless fluff.
     - **Lead with Tangible Evidence & Academic Standing**: Start directly with verified credentials and identity from `info.md` (e.g., *"IT undergraduate ([GPA] GPA) and [Key Role from info.md] with hands-on experience..."*)
     - **Name the Employer's Exact Tech Stack from the JD**: Explicitly identify and name the specific technologies, architectural patterns, and tools required by the target Job Description that match `info.md` (e.g., Docker, Kubernetes, AWS, Terraform, CI/CD pipelines, Spring Boot, React, or Python/RAG).
     - **State the Exact Target Job Title & Technical Value**: End by stating the exact job title from the JD and the concrete engineering value the candidate delivers (e.g., *"Seeking a [Exact Job Title from JD] position to architect resilient deployment pipelines and automate cloud-native infrastructure."*).
     - **Keep Strictly to 3 to 4 Lines**: Must remain tight, factual, and impactful (3 to 4 lines maximum in the PDF) so it preserves the vertical page budget.
   - **Technical Skills**:
     - 5 to 7 concise category lines.
     - Each category must fit on **one line** in the PDF.
     - **"Currently Learning"** and **"Spoken Languages"** must always be the last two separate `\item` lines on their own lines. Never combine them.
   - **Projects (strictly 4)**:
     - Copy each project description **exactly** as written in `info.md` (1 key point bullet per project).
     - **Technologies line (STRICTLY ONE LINE ONLY)**: `Technologies: \textcolor{techblue}{...}` with **6 to 8 tags**. Must stretch across towards the right margin (under the GitHub link) but **MUST NEVER WRAP TO A SECOND LINE**.
     - **Project spacing**: Add `\vspace{3.5pt}` (or 3–4pt) immediately after each `Technologies:` line for projects 1, 2, and 3. Do NOT add space after the last project.
   - **Education**: Degree dates as `Mon YYYY -- Mon YYYY (expected)`. Show degree, faculty, relevant coursework, and GPA. For secondary / high school qualification, show `\textbf{[Secondary Qualification]}, [School Name] \hfill \textbf{[Year]}` on a single line. **STRICT RULE: NEVER include secondary examination grades / results on the CV.** A strong university GPA stands proudly on its own; listing secondary school grades weakens the candidate profile and wastes vertical space.
   - **Certifications and Training**: Strictly include the **2 strongest certificates** directly relevant to the JD. Limiting to 2 certificates is critical to guarantee the 1-page fit.
   - **Professional Experience Section (MANDATORY ATS HEADING: Name as `\section{Professional Experience}`)**:
     - Include **100% OF ALL ROLES** listed under Experience and Community in `info.md` (e.g., Microsoft Student Ambassador, YouTube Content Creator, Technical Writer, Club/Society members).
     - **NEVER omit or drop any role.** Undergraduates do not have full-time corporate jobs yet, so every experience entry is essential.
     - Right-align Credly badge links on the same line if available. Separate entries with `\vspace{3.5pt plus 1pt minus 1pt}`.
    - **References Section (Conditional: Include ONLY if in `info.md` or requested)**:
      - Heading: `\section{References}`
      - Layout: Use a clean side-by-side two-column layout using two `minipage` blocks (`0.48\textwidth` each, separated by `\hfill`).
      - Format:
        ```latex
        \section{References}
        {\small
        \begin{minipage}[t]{0.48\textwidth}
        \textbf{[Referee Name 1]}\\
        [Title / Designation], [Department], [Institution / Company]\\
        \href{mailto:[Email 1]}{\textcolor{linkblue}{[Email 1]}}\\
        [Phone Number 1]
        \end{minipage}
        \hfill
        \begin{minipage}[t]{0.48\textwidth}
        \textbf{[Referee Name 2]}\\
        [Title / Designation], [Department], [Institution / Company]\\
        \href{mailto:[Email 2]}{\textcolor{linkblue}{[Email 2]}}\\
        [Phone Number 2]
        \end{minipage}
        }
        ```
    - **Candidate Name & Header Styling (STRICT MANDATORY RULES)**:
      - **Candidate Name formatting is NON-NEGOTIABLE & STRICT CONSTANT**: Always format as:
        ```latex
        {\LARGE\bfseries\MakeUppercase{[Candidate Full Name]}}\\[1.5pt]
        ```
        (e.g. `{\LARGE\bfseries\MakeUppercase{[CANDIDATE FULL NAME]}}\\[1.5pt]`). Under NO circumstances should this command or spacing value be changed. It MUST strictly use `\LARGE\bfseries\MakeUppercase{...}\\[1.5pt]`. The spacing after the name is a FIXED CONSTANT strictly set to `1.5pt` (`\\[1.5pt]`). Never use `3pt`, `4pt`, or any other spacing value. Never omit `\bfseries` or `\MakeUppercase`.
      - **Sub-header line MUST dynamically match the exact Job Title from that specific JD**: Extract whatever title is on the uploaded JD (e.g., `{\small \textbf{Cloud Engineer Intern}}\\[1.5pt]` or `{\small \textbf{DevOps Engineer – Intern}}\\[1.5pt]`). Never use a hardcoded role. This ensures ATS scanners match the candidate directly to the specific job applied for.
      - **Strict Header Line Spacing (Fixed Constants)**:
        - Name to Subtitle (Job Title): strictly constant `\\[1.5pt]`.
        - Subtitle (Job Title) to Contact Info: strictly constant `\\[1.5pt]`.
        - Contact Info to Social Links 1: strictly constant `\\[1pt]`.
        - Social Links 1 to Social Links 2: strictly constant `\\[1pt]`.
      - **Clickable Email**: In the contact info line, the email address MUST ALWAYS be clickable using `\href{mailto:[Email Address]}{\textcolor{linkblue}{[Email Address]}}`.
     - **Social Links Format (STRICTLY CONSISTENT DOMAIN URL FORMAT)**: All links in the header MUST follow the exact same clean domain-based format (strip `https://` for display). Never show raw usernames alone (e.g., `sachilz`) and never show plain text names (e.g., `NextOps`). Every link must look uniform:
       - **LinkedIn**: `linkedin.com/in/[username]` (e.g., `linkedin.com/in/sachilz`)
       - **GitHub**: `github.com/[username]` (e.g., `github.com/sachilz`)
       - **Portfolio**: `[domain.ext]` (e.g., `sachilz.me`)
       - **Medium**: `medium.com/@[username]` (e.g., `medium.com/@sachilz`)
       - **YouTube**: `youtube.com/@[channel]` (e.g., `youtube.com/@NextOpz` — NEVER just the channel name "NextOps")
     - All links colored with `linkblue`, labels (LinkedIn:, GitHub:, etc.) in black.
   - **Colors**:
     ```latex
     \definecolor{linkblue}{RGB}{0,85,190}
     \definecolor{techblue}{RGB}{55,85,150}
     ```

---

### Step 4 — Deliver the Output
Deliver exactly these two items:

1. **The CV — LaTeX Artifact Only:**
   - Output the complete `.tex` source code as a **Claude artifact (canvas panel)**, with filename `CV_[CandidateName].tex`.
   - **Do NOT paste the LaTeX code inside the chat message.** The artifact/canvas is the only place it goes.
   - **Do NOT produce a PDF.** LaTeX code only. The user will compile it on Overleaf themselves.

2. **ATS Keyword Review — in the Chat:**
   - **Matched Keywords:** Skills and requirements from the JD that are present in `info.md` and included in this CV.
   - **Missing Keywords:** Skills, tools, or requirements from the JD that were **not** found in `info.md` (so the user can review them and decide whether to manually add them to the LaTeX code).

> Keep the chat response concise — only the ATS Keyword Review and a brief link/pointer to the canvas panel. Do not include long recruiter essays or verification checklists. Never claim the CV guarantees an interview or ATS success.

---

## Page Budget & Structure Preservation Rules

> [!IMPORTANT]
> **1. Page 1 is Always the Priority Target**:
> If all content (even with References, if spacing allows naturally) can fit cleanly on **1 single page**, keep it on **1 Page**! Ignore the 2nd page entirely.

> [!CAUTION]
> **2. NEVER Break the Visual Structure to Force 1 Page**:
> Under NO circumstances should you delete `\vspace`, reduce inter-project gaps to 0, or glue project titles directly under previous `Technologies:` lines just to force everything onto 1 page.
> - The Project separator gap (`\vspace{4.5pt plus 1pt minus 1pt}` or `\vspace{5pt}`) after each project's `Technologies:` line is **MANDATORY**.
> - Section titles, bullet spacing, and project separation must maintain their clean, professional visual structure.

> [!NOTE]
> **3. 2nd Page is Strictly an Optional Fallback**:
> The 2nd page is an optional fallback that should **ONLY** be created when:
> - Content is genuinely too long (e.g. dense projects + experience + references included), AND
> - It is physically impossible to keep on 1 page without breaking the layout structure or stripping out `\vspace`.
> When a 2nd page is created, distribute the sections cleanly across both pages (e.g. Page 1: Header, Summary, Skills, Projects; Page 2: Education, Certifications, Professional Experience, References) so that both pages look balanced, intentional, and readable.

---

## Base LaTeX Template

```latex
\documentclass[10pt,a4paper]{article}
\usepackage[T1]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage{lmodern}
\usepackage[margin=0.42in]{geometry}
\usepackage{enumitem}
\usepackage{titlesec}
\usepackage[hidelinks]{hyperref}
\usepackage{xcolor}
\definecolor{linkblue}{RGB}{0,85,190}
\definecolor{techblue}{RGB}{55,85,150}
\input{glyphtounicode}
\pdfgentounicode=1
\pagestyle{empty}
\setlength{\parindent}{0pt}
\setlength{\parskip}{0pt}
\raggedbottom
\titleformat{\section}{\bfseries\large\scshape}{}{0pt}{}
  [\vspace{-4.5pt}\rule{\linewidth}{0.5pt}]
\titlespacing*{\section}{0pt}{6.5pt plus 1.5pt minus 1pt}{2.2pt} % AUTO-CALIBRATED 1-PAGE SECTION SPACING
\setlist[itemize]
  {leftmargin=1.2em,itemsep=1.2pt plus 0.4pt minus 0.4pt,topsep=1.5pt plus 0.5pt minus 0.5pt,parsep=0pt,partopsep=0pt}
\newcommand{\ghlink}[1]{\href{#1}{\textcolor{linkblue}{GitHub}}}
\begin{document}

%% ── HEADER ────────────────────────────────────────────────────────────
\begin{center}
{\LARGE\bfseries\MakeUppercase{[CANDIDATE FULL NAME]}}\\[1.5pt]
{\small \textbf{[Exact Job Title from Job Description]}}\\[1.5pt]
{\small [City, Country] \textbar{} [Phone Number] \textbar{} \href{mailto:[Email Address]}{\textcolor{linkblue}{[Email Address]}}}\\[1pt]
{\small LinkedIn: \href{[LinkedIn URL]}{\textcolor{linkblue}{linkedin.com/in/[username]}} \textbar{} GitHub: \href{[GitHub URL]}{\textcolor{linkblue}{github.com/[username]}} \textbar{} Portfolio: \href{[Portfolio URL]}{\textcolor{linkblue}{[domain.ext]}}}\\[1pt]
{\small Medium: \href{[Medium URL]}{\textcolor{linkblue}{medium.com/@[username]}} \textbar{} YouTube: \href{[YouTube URL]}{\textcolor{linkblue}{youtube.com/@[channel]}}}
\end{center}

%% ── PROFESSIONAL SUMMARY ──────────────────────────────────────────────
\section{Professional Summary}
{\small
[Craft an evidence-based summary (strictly 3 to 4 lines). BANNED FILLERS: "Motivated", "Passionate", "Interested in". Lead with credentials: "IT undergraduate ([GPA] GPA) and [Key Role / Ambassadorship from info.md] with hands-on experience [building/deploying systems using JD tech stack]...". End with: "Seeking a [Exact Target Job Title from JD] position to [deliver concrete technical value matching JD]."]
}

%% ── TECHNICAL SKILLS ──────────────────────────────────────────────────
\section{Technical Skills}
{\small
\begin{itemize}
  \item \textbf{[Category 1]:} [Skills matching JD from info.md]
  \item \textbf{[Category 2]:} [Skills matching JD from info.md]
  \item \textbf{[Category 3]:} [Skills matching JD from info.md]
  \item \textbf{Currently Learning:} [Skills currently learning from info.md]
  \item \textbf{Spoken Languages:} [Languages from info.md]
\end{itemize}
}

%% ── PROJECTS (exactly 4, chosen to match JD) ──────────────────────────
\section{Projects}
{\small
% ── PROJECT 1 ──
\textbf{[Project Title 1]} \hfill \ghlink{[GitHub URL 1]}
\begin{itemize}
  \item [Description copied exactly from info.md — 1 key point]
\end{itemize}
Technologies: \textcolor{techblue}{[6 to 8 core technology tags — strictly 1 line]}
\vspace{4.5pt plus 1pt minus 1pt}  % PROJECT GAP

% ── PROJECT 2 ──
\textbf{[Project Title 2]} \hfill \ghlink{[GitHub URL 2]}
\begin{itemize}
  \item [Description copied exactly from info.md — 1 key point]
\end{itemize}
Technologies: \textcolor{techblue}{[6 to 8 core technology tags — strictly 1 line]}
\vspace{4.5pt plus 1pt minus 1pt}  % PROJECT GAP

% ── PROJECT 3 ──
\textbf{[Project Title 3]} \hfill \ghlink{[GitHub URL 3]}
\begin{itemize}
  \item [Description copied exactly from info.md — 1 key point]
\end{itemize}
Technologies: \textcolor{techblue}{[6 to 8 core technology tags — strictly 1 line]}
\vspace{4.5pt plus 1pt minus 1pt}  % PROJECT GAP

% ── PROJECT 4 ──
\textbf{[Project Title 4]} \hfill \ghlink{[GitHub URL 4]}
\begin{itemize}
  \item [Description copied exactly from info.md — 1 key point]
\end{itemize}
Technologies: \textcolor{techblue}{[6 to 8 core technology tags — strictly 1 line]}
}

%% ── EDUCATION ─────────────────────────────────────────────────────────
\section{Education}
{\small
\textbf{[Degree Name]}, [University / Institution] \hfill \textbf{[Start Mon YYYY] -- [End Mon YYYY] (expected)}\\
[Faculty]. Coursework: [Relevant Courses] \hfill GPA: [GPA / Scale]\\[2pt]
\textbf{[Secondary / School Qualification]}, [School Name] \hfill \textbf{[Year]}
% NOTE: Never include A/L grades ('CCC' / 'Passed with 3 C passes') as they detract from a strong university GPA.
}

%% ── CERTIFICATIONS AND TRAINING (2–3 strongest, matching JD) ──────────
\section{Certifications and Training}
{\small
\begin{itemize}
  \item [Course/Certificate Name], [Issuer] ([Mon YYYY])
  \item [Course/Certificate Name], [Issuer] ([Mon YYYY])
\end{itemize}
}

%% ── COMMUNITY & CONTENT EXPERIENCE (Include 100% of all roles) ──
\section{Community \& Content Experience}
{\small
\textbf{[Role / Title 1]}, [Organization / Company]
  \hfill \textbf{[Start Date] -- [End Date / Present]}
\begin{itemize}
  \item [Description of responsibilities and achievements]
    \hfill \href{[Badge URL]}{\textcolor{linkblue}{[Badge Link]}}
\end{itemize}

\vspace{3.5pt plus 1pt minus 1pt}
\textbf{[Role / Title 2]}, [Organization / Company] \hfill \textbf{[Dates]}
\begin{itemize}
  \item [Description of responsibilities and achievements]
\end{itemize}

\vspace{3.5pt plus 1pt minus 1pt}
\textbf{[Role / Title 3]}, [Organization / Company] \hfill \textbf{[Dates]}
\begin{itemize}
  \item [Description of responsibilities and achievements]
\end{itemize}

\vspace{3.5pt plus 1pt minus 1pt}
\textbf{[Community Role / Club]}, [Organization] \hfill \textbf{[Dates]}
\begin{itemize}
  \item [Description of involvement and contributions]
\end{itemize}
}

%% ── REFERENCES (Include ONLY if present in info.md or requested by user) ──
%% Un-comment when including references:
% \section{References}
% {\small
% \begin{minipage}[t]{0.48\textwidth}
% \textbf{[Referee 1 Full Name]}\\
% [Designation / Position], [Faculty / Department], [Institution]\\
% \href{mailto:[Email]}{\textcolor{linkblue}{[Email]}}\\
% [Phone Number(s)]
% \end{minipage}
% \hfill
% \begin{minipage}[t]{0.48\textwidth}
% \textbf{[Referee 2 Full Name]}\\
% [Designation / Position], [Faculty / Department], [Institution]\\
% \href{mailto:[Email]}{\textcolor{linkblue}{[Email]}}\\
% [Phone Number(s)]
% \end{minipage}
% }

\end{document}
```

---

## Final Self-Check Before Delivering the LaTeX Code

- [ ] Used candidate's actual profile data from `info.md` (no hardcoded sample data or invented facts).
- [ ] Exactly **4 projects** included.
- [ ] ALL **experience entries and community roles** from `info.md` are included (100% of them, none omitted).
- [ ] All header social links use strictly uniform domain format (`linkedin.com/in/...`, `github.com/...`, `medium.com/@...`, `youtube.com/@...` — never bare names like "NextOps" or "sachilz").
- [ ] Professional Summary is evidence-based (leads with GPA/credentials, names employer's stack, contains zero filler like "motivated" or "interested in", targets exact JD title).
- [ ] Project descriptions copied **exactly** from `info.md` (1 bullet per project).
- [ ] Strictly **2 certificates** chosen for JD relevance (prevents 2nd page overflow).
- [ ] Technology tags colored with `techblue`, links colored with `linkblue`.
- [ ] Each Technologies line fits on **strictly ONE single line** (never wraps to a 2nd line, extends up to the GitHub text margin).
- [ ] `\vspace{5pt}` present **immediately** after Technologies lines for projects 1, 2, and 3.
- [ ] All dates use `--` (en dash) in LaTeX.
- [ ] Geometry margins strictly set to constant `\usepackage[margin=0.42in]{geometry}` (never changed to any other value).
- [ ] CV fits strictly **one A4 page** (or 2 pages if conditional references/density warrant it) — no large blank space at bottom.
