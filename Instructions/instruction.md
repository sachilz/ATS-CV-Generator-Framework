# CV Generation Instructions for Claude & ChatGPT

## 🛑 STRICT GATING & EXECUTION PROTOCOL (MANDATORY HALT RULES)

> [!CAUTION]
> **PREMATURE CV GENERATION IS STRICTLY PROHIBITED.**
> Under NO circumstances should you output ANY LaTeX code, CV draft, or resume preview during Step 1 or Step 2.
> **DO NOT DEFAULT TO "DEVOPS" OR ANY OTHER ROLE**: Even if previous chat history, user custom instructions, or `info.md` mention DevOps, **NEVER assume or default to DevOps or any other job title**. You must wait for the exact Job Description (JD) provided by the user in this specific session.

### The 4 Mandatory Execution Gates:
- **GATE 1 (When user provides this instruction file)**:
  - ⛔ **ABSOLUTE RESTRICTION**: DO NOT generate any CV. DO NOT output any LaTeX code or PDF. DO NOT ask for the Job Description (JD) yet.
  - ✅ **ACTION**: Acknowledge readiness, ask ONLY for `info.md` and `cv_guide.md`, and **STOP GENERATING IMMEDIATELY**.
- **GATE 2 (When user provides `info.md` and `cv_guide.md`)**:
  - ⛔ **ABSOLUTE RESTRICTION**: DO NOT generate any CV. DO NOT output any LaTeX code or PDF. DO NOT assume the user wants a DevOps CV.
  - ✅ **ACTION**: Validate the files. If complete (or user says "Proceed with what I have"), ask for the **Job Description (JD)** and prompt for output format, and **STOP GENERATING IMMEDIATELY**.
- **GATE 3 (When user provides the Job Description)**:
  - ⛔ **ABSOLUTE RESTRICTION**: DO NOT generate the CV yet until output format is confirmed.
  - ✅ **ACTION**: If the user did not specify their output format in their message, confirm receipt of the JD and ask the user to choose their preferred format:
    > "I have received and analyzed your Job Description for **[Target Role]**! Before I generate your CV, please choose your preferred output format:
    > 1. **LaTeX Code only** (for Overleaf compilation)
    > 2. **PDF only** (compiled, download-ready PDF document)
    > 3. **Both** (LaTeX code + compiled PDF)
    >
    > Please reply with **1**, **2**, or **3** to proceed."
  - **STRICT HALT**: Stop and wait for the user to select their preferred option (unless the user already specified their choice alongside their JD).
- **GATE 4 (When user chooses Option 1, 2, or 3)**:
  - ✅ **ACTION**: Generate and deliver the CV strictly according to the selected format!
  - 🛑 **STRICT PRE-COMPILATION AUDIT FOR CLAUDE & CHATGPT**:
    1. **Strictly 1 Page Fit**: All 7 sections (Header, Summary, Skills, 4 Projects, Education, 2 Certifications, Community Experience) MUST fit on Page 1. Never add `\newpage`!
    2. **Omit References by Default**: DO NOT include `\section{References}` unless the user explicitly requested it in their prompt!
    3. **Exact Preamble & Mandatory Section Underline**: You MUST copy the exact LaTeX preamble verbatim:
       `\usepackage[margin=0.42in]{geometry}`
       `\titleformat{\section}{\bfseries\large\scshape}{}{0pt}{}[\vspace{-4.5pt}\rule{\linewidth}{0.5pt}]`
       Every section heading MUST have the horizontal rule (`\rule{\linewidth}{0.5pt}`) underneath and bold small-caps (`\scshape`).
    4. **No Chat Clutter**: Deliver the CV directly without automatic ATS keyword essays in chat.

---

## System Overview & Required Files

This system operates in strict sequential stages to build a one-page, ATS-optimized LaTeX CV:
1. **`instruction.md`** — This instruction file (system instructions).
2. **`info.md`** — The candidate's personal profile file containing all factual information (single source of truth).
3. **`cv_guide.md`** — The layout specification, typography rules, and base LaTeX design.
4. **`verification_instruction.md`** — (Optional Stage 2) Hyper-critical recruiter audit and ATS scoring instructions.
5. **Job Description (JD)** — The job description provided by the user for the targeted role.

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

3. **Prompt for the Job Description (JD) & Output Format**:
   - Once `info.md` is complete (or the user says "Proceed with what I have"):
     Confirm and request the Job Description:
     > "Your `info.md` and `cv_guide.md` are verified and ready! Please share the **Job Description (JD)** for the position you are targeting, and tell me your preferred output format:
     > 1. **LaTeX Code only** (for Overleaf compilation)
     > 2. **PDF only** (compiled ready-to-use PDF)
     > 3. **Both** (LaTeX code + compiled PDF)"
   - **STRICT HALT**: Stop and end your response immediately after requesting the Job Description. **DO NOT output any LaTeX code, resume draft, or default to a DevOps CV.** You MUST wait for the user's next message containing the target Job Description.

---

### Step 3 — Process the Job Description & Build the CV
Once the target Job Description (JD) and output format are confirmed:

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
    - **Page Budget & Length (STRICT 1-PAGE RULE vs CONDITIONAL 2-PAGE RULE)**:
      - 🛑 **STRICT DEFAULT: EXACTLY ONE (1) A4 PAGE**:
        - Every CV generated MUST fit completely on **EXACTLY ONE (1) A4 PAGE**.
        - Page 1 MUST contain ALL 7 sections in order:
          1. Header
          2. Professional Summary (strictly 3 to 4 lines)
          3. Technical Skills (5 to 7 category lines, 1 line each)
          4. Projects (strictly 4 projects, 1 bullet point each, 1-line technologies with techblue)
          5. Education (University degree + High school line)
          6. Certifications and Training (strictly 2 most relevant certificates)
          7. Community & Content Experience (all roles)
        - ⛔ **ABSOLUTE PROHIBITION**: NEVER generate a 2nd page by default. NEVER push Education, Certifications, or Community & Content Experience to a 2nd page! The entire CV must be complete on Page 1.
      - 🚫 **REFERENCES RULE (DEFAULT: COMPLETELY OMITTED)**:
        - Even though `info.md` contains a `## 9. References` section or referee contact details, **DO NOT INCLUDE REFERENCES ON THE CV BY DEFAULT**.
        - The `\section{References}` section MUST BE COMPLETELY OMITTED unless:
          1. The user explicitly requests in their chat prompt: *"Include references"* or *"Add references"*, OR
          2. The target Job Description explicitly states: *"References required"*.
        - If neither condition is met, **NEVER include References**.
      - ⚠️ **THE 2-PAGE RULE (STRICT FALLBACK ONLY)**:
        - A 2nd page is **STRICTLY AN EXCEPTIONAL FALLBACK**.
        - A 2nd page is **ONLY PERMITTED IF**:
          1. The user explicitly requested References (or JD mandates them), AND
          2. The candidate's content + References cannot physically fit on 1 page without removing mandatory `\vspace` or distorting section spacing.
        - **If references are NOT requested by the user, a 2nd page is 100% FORBIDDEN.**
    - **Section Headings & Horizontal Rule (MANDATORY LATEX SYNTAX)**:
      - Every section heading MUST be formatted using:
        ```latex
        \titleformat{\section}{\bfseries\large\scshape}{}{0pt}{}
          [\vspace{-4.5pt}\rule{\linewidth}{0.5pt}]
        \titlespacing*{\section}{0pt}{6.5pt plus 1.5pt minus 1pt}{2.2pt}
        ```
      - ⛔ **MANDATORY HORIZONTAL LINE**: The `[\vspace{-4.5pt}\rule{\linewidth}{0.5pt}]` draws a clean 0.5pt horizontal line under every section title. **NEVER OMIT THIS LINE!** If a section heading has no horizontal line underneath, it is a direct guideline violation.
      - ⛔ **MANDATORY SMALL CAPS**: Section titles MUST be in bold small-caps (`\scshape`).
   - **Font**: Latin Modern (`\usepackage{lmodern}`, 10pt body text).
    - **Section order (ALL 7 SECTIONS FIT ON PAGE 1)**: Header → Professional Summary → Technical Skills → Projects → Education → Certifications and Training → Community & Content Experience. (References section is completely excluded by default; include ONLY if explicitly requested by user in chat).
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
   - **Community & Content Experience Section (Name as `\section{Community \& Content Experience}`)**:
     - Include **100% OF ALL ROLES** listed under Experience and Community in `info.md` (e.g., Microsoft Student Ambassador, YouTube Content Creator, Technical Writer, Club/Society members).
     - **NEVER omit or drop any role.** Undergraduates do not have full-time corporate jobs yet, so every experience entry is essential.
     - Right-align Credly badge links on the same line if available. Separate entries with `\vspace{3.5pt plus 1pt minus 1pt}`.
    - **References Section (STRICTLY EXCLUDED BY DEFAULT — Include ONLY if explicitly requested by user in chat)**:
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

### Step 4 — Deliver the Output (Based on User's Choice)
Deliver strictly according to the format selected by the user (Option 1, 2, or 3):

1. **Option 1 (LaTeX Code only)**:
   - Output the complete `.tex` source code as an **artifact (canvas panel)**, with filename `CV_[CandidateName].tex`.
   - **Do NOT paste raw LaTeX code inside the chat message.** The artifact/canvas panel is the only place it goes.

2. **Option 2 (PDF only)**:
   - Deliver the compiled, download-ready PDF document `CV_[CandidateName].pdf`.

3. **Option 3 (Both — LaTeX Code + PDF)**:
   - Deliver the complete `.tex` source code in the artifact/canvas panel AND provide the compiled `CV_[CandidateName].pdf`.

> [!CAUTION]
> **ABSOLUTE BAN ON AUTOMATIC ATS ESSAYS IN STEP 4**:
> - **DO NOT include an ATS Keyword Review in the chat during Step 4.**
> - **DO NOT list "Matched Keywords" or "Missing Keywords" automatically.**
> - Keep the chat response clean, brief, and direct — confirm that the CV has been generated for the target job title according to the chosen format, and prompt the user if they wish to run the separate Verification Audit:
>   > "Your tailored one-page CV for **[Target Role]** has been generated according to your selected format!
>   > 
>   > Would you like me to run a **Hyper-Critical Recruiter & ATS Verification Audit** on this CV against your target Job Description?
>   > If yes, please provide **`Verification_Instructions/verification_instruction.md`** (or reply **'Review my CV'**), and I will generate your detailed 4-section Audit Report (ATS Score 1–100, Strengths & Weaknesses, Bullet Optimization, and Red Flags Check)."

---

### Step 5 — Optional Hyper-Critical Recruiter & ATS Verification Audit
If the user provides `Verification_Instructions/verification_instruction.md` or replies "Review my CV":
- Follow `Verification_Instructions/verification_instruction.md` strictly.
- Act as a Senior Technical Recruiter & Hiring Manager reviewing 200+ engineering resumes weekly.
- Deliver the hyper-critical 4-section Audit Report in chat:
  1. **ATS Score & Compatibility (1–100 Rating with Matched vs. Missing Keywords)**
  2. **Strengths & Weaknesses (Top 3 of each from a Hiring Manager perspective)**
  3. **Bullet Point Optimization (3 concrete Before vs. After rewrites)**
  4. **Red Flags & Recruiter Screening Check (Final Verdict: Pass / Warning / Reject)**

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
> **3. 2nd Page is Strictly an Optional Fallback (TRIGGERED ONLY BY EXPLICIT USER REQUEST FOR REFERENCES)**:
> - The standard CV (Header, Summary, Skills, 4 Projects, Education, 2 Certifications, Community Experience) MUST fit on **EXACTLY 1 PAGE**.
> - A 2nd page should **ONLY** be created if the user explicitly requested References (or JD required them) AND the combined content physically cannot fit on 1 page without deleting mandatory `\vspace` or breaking layout.
> - **DO NOT artificially split content across 2 pages if references are not requested.** Leaving Education and Experience on Page 2 while Page 1 ends at Projects is a CRITICAL GUIDELINE FAILURE.

---

## Base LaTeX Template

> [!CAUTION]
> ### 🛑 STRICT PREAMBLE ENFORCEMENT — ZERO MODIFICATIONS PERMITTED
> When outputting LaTeX code, you MUST copy the exact preamble below character-for-character.
> - `\usepackage[margin=0.42in]{geometry}` — STRICT 0.42in margin on all 4 sides. NEVER change to 0.5in, 0.75in, or 1in!
> - `\titleformat{\section}{\bfseries\large\scshape}{}{0pt}{}[\vspace{-4.5pt}\rule{\linewidth}{0.5pt}]` — MANDATORY horizontal line (`\rule{\linewidth}{0.5pt}`) and bold small-caps (`\scshape`) under EVERY section heading. NEVER omit this line!
> - `\titlespacing*{\section}{0pt}{6.5pt plus 1.5pt minus 1pt}{2.2pt}` — MANDATORY tuned vertical elastic spacing.
> - `\setlist[itemize]{leftmargin=1.2em,itemsep=1.2pt plus 0.4pt minus 0.4pt,topsep=1.5pt plus 0.5pt minus 0.5pt,parsep=0pt,partopsep=0pt}` — MANDATORY compact list spacing.

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

%% ── PROJECTS (strictly 4, chosen to match JD) ──────────────────────────
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

%% ── REFERENCES (STRICTLY OMITTED BY DEFAULT — Include ONLY if explicitly requested by user in chat) ──
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

## Final Self-Check Before Delivering the CV

- [ ] Used candidate's actual profile data from `info.md` (no hardcoded sample data or invented facts).
- [ ] Output format strictly matches user's choice (LaTeX Code only / PDF only / Both).
- [ ] ZERO automatic ATS Keyword Review or recruiter commentary in chat during Step 4.
- [ ] Prompted user if they wish to run the separate Verification Audit (`verification_instruction.md`).
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
- [ ] Section heading rule `[\vspace{-4.5pt}\rule{\linewidth}{0.5pt}]` and `\scshape` present on EVERY section heading.
- [ ] References section EXCLUDED by default (included ONLY if user explicitly typed "include references").
- [ ] CV fits strictly on **ONE (1) A4 page** with ALL 7 sections on that single page. ZERO overflow to a second page.
