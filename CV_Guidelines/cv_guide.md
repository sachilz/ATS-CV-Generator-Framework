# How to Build a Clean, Professional One-Page CV with AI

A step-by-step guide for students and interns, based on a DevOps internship CV built with an AI assistant, LaTeX and Overleaf.

## 1. What the finished CV looks like

The goal is a CV that is clean, easy to scan in 10 to 20 seconds, and readable by applicant tracking systems (ATS). These are the design rules:

- Strictly one A4 page, single column (unless conditional references require 2 pages).
- Margins: STRICT FIXED CONSTANT `\usepackage[margin=0.42in]{geometry}` (Top = Bottom = Left = Right = 0.42in). Never change this margin value under any circumstances across different CVs.
- Latin Modern font (the classic LaTeX look), 10 pt body text with 9 pt content blocks.
- No tables, photos, icons, skill bars, graphics or colored backgrounds.
- Section order: Header, Professional Summary, Technical Skills, Projects, Education, Courses and Certifications, Community & Content Experience. (All 7 sections fit on exactly 1 page. References are excluded by default).
- Section headings in bold small capitals with a thin line underneath.
- The header must always show every social link from your profile file: LinkedIn, GitHub, Portfolio, Medium and YouTube. Strictly uniform URL formatting: all links must display their clean domain/URL path (e.g. `linkedin.com/in/username`, `github.com/username`, `portfolio.com`, `medium.com/@username`, `youtube.com/@channel`) — never bare usernames or plain channel text like "NextOps" or "sachilz". Each link is blue and the label in front stays black.
- Each project has a bold title, a blue "GitHub" link on the right (no underline), the project description copied exactly from your profile file (1 key point each), and a "Technologies:" line (no italics) whose technology tags are colored with techblue.
- Dates aligned to the right edge of the page using `\hfill \textbf{...}` (never in parentheses).
- Structural integrity: NEVER compress skills or certificates onto single lines with pipes `|`. NEVER remove `\begin{itemize}` bullets. The CV must fill the entire single page vertically with zero massive blank space at the bottom.
- Only relevant content for the target job. Leave out weak or unrelated items.

## 2. Step 1: Write your profile file (your source of truth)

Create one text or Markdown file with every fact about you. The AI must only use what is written there, which stops it from inventing anything. Use these headings:

1. Personal and contact details: name, email, phone, city and country, LinkedIn, GitHub, portfolio, Medium, YouTube. Also write your baseline professional summary here (3 to 4 lines); for each specific job, the AI dynamically adapts this summary to match the target Job Description (tech stack and requested criteria) while strictly preserving your verified facts and credentials.
2. Education: degree, university, dates, GPA, relevant coursework. Also your A/L school, year, stream and result.
3. Technical skills, grouped by category (languages, front-end, back-end, databases, CI/CD, containers, cloud, security tools).
4. Projects: title, GitHub link, technologies, and 1 factual key point (the description) for each one.
5. Experience and community: role, organization, dates, what you really do. Include every club and society you belong to, with your role and a short description.
6. Courses and certifications: course name, issuer, date. Label as "Courses and Certifications". Combine multiple related beginner courses from the same date/provider into cohesive lines.
7. Your standing rules (see Step 3).

Honesty rules for this file:

- Never write numbers you cannot prove (users, speed-ups, percentages).
- Mark anything in progress as "Currently Learning" and never as a completed skill or certificate.
- Describe academic or solo projects as what they are.
- Keep it updated. Upload the latest version whenever it changes.

## 3. Step 2: Set your standing rules

Put these rules at the bottom of your profile file so the AI applies them to every CV:

1. Font & Candidate Name: Latin Modern (`\usepackage{lmodern}`). Candidate name MUST STRICTLY ALWAYS be formatted as `{\LARGE\bfseries\MakeUppercase{YOUR FULL NAME}}\\[1.5pt]` (e.g. `{\LARGE\bfseries\MakeUppercase{Sachintha Dilshan Madhushankha}}\\[1.5pt]`). The `1.5pt` line spacing is a strict fixed constant. Never omit `\bfseries` or `\MakeUppercase`, and never use `3pt` or `4pt`.
2. Certificates: strictly include the 2 strongest ones that relate to the job description. Limiting to 2 certificates is critical to guarantee the 1-page fit.
3. Include strictly 4 projects in every CV. Choose the 4 that best match the job requirements. If the profile file has only 4, include all 4.
4. Use only facts from the profile file. Never invent details.
5. Show the degree dates as "Mon YYYY - Mon YYYY (expected)" with no year or semester of study.
6. Length: strictly one page. Never produce a second page.
7. Project descriptions: copy each project's description exactly as written in the profile file (1 key point per project). Do not rewrite it or add bullets.
8. Technology tags: no italics. Color only the tags with \textcolor{techblue}{...}. The color techblue is defined at the very top of the file.
9. Header: always show all social links from the profile file (LinkedIn, GitHub, Portfolio, Medium, YouTube), none missing. Strictly uniform domain format: `linkedin.com/in/...`, `github.com/...`, `medium.com/@...`, `youtube.com/@...` (never bare names like "NextOps" or "sachilz"). Links are blue; GitHub and Credly links have no underline.
10. Full-page layout: no large blank space at the bottom of the page. LaTeX code: always deliver it as a file or canvas, never pasted inside the chat message.
11. Margins (Strict Fixed Constant): Always use `\usepackage[margin=0.42in]{geometry}`. The margins MUST ALWAYS be strictly 0.42in on all 4 sides. Under NO circumstances should the margin value be altered or customized across different CVs.

## 4. Step 3: Start the chat with a master prompt

Paste your profile file and then this prompt. It makes the AI behave like a senior recruiter and ATS expert:

```
Act as a Senior Technical Recruiter, Hiring Manager, ATS Specialist and
Professional CV Writer with 15+ years of experience recruiting for IT
internships and graduate roles.

Use my attached profile file as the single source of truth. Never invent
skills, metrics, users, responsibilities or credentials. Select only the
information relevant to the target job.

When I give a job description (or a target such as "DevOps internship for
a career fair"), do this in order:
1. Analyze the role: title, essential and preferred skills, ATS keywords.
2. Check my profile for completeness.
3. Ask me for my preferred output format:
   - Option 1: LaTeX Code only (for Overleaf)
   - Option 2: PDF only (compiled ready-to-use PDF)
   - Option 3: Both (LaTeX code + compiled PDF)
4. Build a one-page, single-column, ATS-friendly CV according to my chosen format.
5. Keep the chat response clean and direct (no ATS review essays or filler).
Never claim the CV guarantees an interview or ATS success.

Strict rules:
- The CV must fit on exactly ONE page. All sections (Header, Summary, Skills, 4 Projects, Education, 2 Certificates, Experience) MUST be on that single page. Never produce a second page. Fill the page cleanly with no large empty space at the bottom.
- Subtitle: Directly under my name, include the exact target Job Title from the JD as {\small \textbf{[Exact Job Title]}}\\[1.5pt].
- Professional Summary: Adapt the 3-4 line summary to match the target JD's tech stack and requested criteria (e.g. problem-solving, analytical skills, eagerness to learn), never just copy the default summary. MUST BE WRITTEN AS A SINGLE CONTINUOUS PARAGRAPH with NO manual line breaks (\\ or \newline). Let LaTeX automatically justify the text evenly to the margins (same-length lines).
- LaTeX syntax & structure: Use the Base LaTeX Template strictly without improvising or stripping bullets. NEVER merge categories or certificates with pipes (|) (e.g. NEVER combine Languages | Frontend or Cert 1 | Cert 2). Each category/certificate MUST be its own separate \item. Never put "| GitHub" next to titles (use \hfill \ghlink{...}). Dates MUST use \hfill \textbf{...} (never in parentheses). Never change \section{Projects} to "Selected Projects". Always use \begin{itemize}\item...\end{itemize} for all lists. This ensures the page fills vertically with no giant bottom whitespace.
- Omit References completely by default unless I explicitly request them in my prompt.
- Section headings MUST have the horizontal line underneath ([\vspace{-4.5pt}\rule{\linewidth}{0.5pt}]) and bold small-caps (\scshape). Never remove the horizontal line.
- The header must always include ALL my social links from the profile file: LinkedIn, GitHub, Portfolio, Medium and YouTube. Never skip any. Uniform domain format.
- Use the LaTeX template from this guide exactly as given: do not change the preamble or the geometry margin (strictly 0.42in).
- Read the job requirements first, then check them against my profile file, and only then build the CV.
- Give me the LaTeX code as a file or canvas that I can open and download, never pasted inside the chat message.
```

## 5. Step 4: Give the target & choose output format

Tell the AI what you are applying for:

- A job posting: paste the text or upload a screenshot of it.
- A career fair: say "create a DevOps focused CV for a career fair, use my best 4 projects".
- A general role: say "create a Software Engineer internship CV".

The AI will then ask for your preferred output format (LaTeX Code only, PDF only, or Both) and build the CV matching the vacancy.

**Recommended order of messages.** Send things in this order so the AI never skips a rule:

1. In your first message, upload this guide and your profile file (for example `info.md`). Say: "Read both. Follow this guide for layout and rules, and use my profile file as the only source of facts."
2. Wait for the AI to confirm. Do not send the job description yet.
3. Send the job description. The AI will ask for your preferred output format:
   - Option 1: LaTeX Code only (for Overleaf)
   - Option 2: PDF only (compiled ready-to-use PDF)
   - Option 3: Both (LaTeX code + compiled PDF)
4. Confirm your choice (1, 2, or 3), and the AI builds and delivers your tailored CV directly without chat clutter or review essays.
5. The AI will prompt you to choose whether to verify (check) your CV: reply **1** (Yes) to get the built-in 4-section Recruiter & ATS Audit Report, or **2** (No) to finish.

**CV content rules.** Every CV must follow these:

- **Strictly 4 projects (Ranked in Descending Order of JD Relevance & Strength).** Always show exactly 4 projects, ordered strictly from highest relevance to lowest: Project 1 (Strongest direct match to the target JD role and core tech stack), Project 2 (Second strongest direct match), Project 3 (Core domain match), and Project 4 (Strongest complementary engineering project from the remainder). Copy each project description exactly as written in your profile file (1 key point each).
- **Skills align with both the JD and the projects.** Keep the Technical Skills section simple and easy to read, with 5 to 7 short category lines. Prioritize and include every skill mentioned in the Job Description (JD) that exists in your profile file, along with the core tools and languages used in the 4 chosen projects. Leave out minor, unrelated tools so the section stays clean. Update the skills whenever the target role or the 4 projects change.
- **Courses and Certifications (Combine related courses & align with JD + Projects).** Name this section `\section{Courses and Certifications}`. Select courses matching BOTH the target Job Description (JD) and the tech stack of your 4 selected projects. If multiple related beginner courses share the same issuer and completion date (e.g. KodeKloud Feb 2026 courses or SLIIT Stages I & II), group and combine them into single cohesive bullet lines: e.g. `\item AWS, Terraform, Docker, Kubernetes, Jenkins Pipelines with Hands-On Labs \hfill \textbf{Feb 2026 -- KodeKloud}`. Right-align the date and provider in bold using `\hfill \textbf{Mon YYYY -- Provider}`. Keep to 2 to 4 clean lines total. Never merge certificates on one line with pipes `|`.
- **Experience Heading: `\section{Community \& Content Experience}` & Include ALL roles.** Name this section `\section{Community \& Content Experience}` (escaped as `\&` in LaTeX). Because undergraduates do not have corporate industry jobs yet, labeling student ambassador roles and YouTube channels as "Professional Experience" can look dishonest to recruiters. "Community & Content Experience" is 100% transparent and respected. You MUST include **EVERY SINGLE ROLE** listed in the candidate profile's Experience and Community section (Student Ambassador, YouTube, Medium, Clubs). NEVER omit, filter, or drop any role. Right-align Credly badges. Use `\vspace{3.5pt plus 1pt minus 1pt}` between entries.
- **Education.** Show your university degree (dates, GPA, coursework) and your secondary / high school (qualification name, school name, and year only). **STRICT RULE: Do NOT include secondary school results or grades on the CV.** The candidate's university GPA stands on its own, and listing secondary grades weakens the candidate profile and wastes vertical space.
- **One page.** All of this must still fit on exactly one page.

**Project spacing.** After each project's "Technologies:" line, add `\vspace{4.5pt plus 1pt minus 1pt}` before the next project title, so the projects are clearly separated.

**Project spacing is mandatory.** Put the `\vspace{4.5pt plus 1pt minus 1pt}` line between every two projects, directly after the "Technologies:" line of the first project and before the next project title, exactly like this. Never skip it, and never remove it when fitting the page:

```latex
Technologies: \textcolor{techblue}{Tool, Tool, Tool}

\vspace{4.5pt plus 1pt minus 1pt}
\textbf{Next Project Title} \hfill \ghlink{https://github.com/you/next-project}
```

**Skills layout.** Every skills category goes on its own bullet line, one below the other. "Currently Learning" and "Spoken Languages" are two separate lines and must never be joined on one line. Keep each category line short enough to fit on one or two lines.

**Auto-calibrated section spacing.** Use `\titlespacing*{\section}{0pt}{6.5pt plus 1.5pt minus 1pt}{2.2pt}` with `\usepackage[margin=0.42in]{geometry}`. This tuned calibration guarantees that 4 projects (with full 1-bullet descriptions), technical skills, education, certifications, and all 4 experience roles fit strictly on ONE single A4 page with 100% equal margins on all 4 sides, without any page overflow.

**Professional summary (Evidence-based & 100% JD-Matched — Strictly Single Continuous Paragraph).** Lead with concrete evidence from your profile file (GPA, student ambassadorship, hands-on projects) combined with the employer's exact tech stack and requirements. **Mandatory Single Paragraph Rule:** The summary MUST be written as a single, unbroken continuous paragraph of prose (strictly 3 to 4 lines). **NEVER insert manual line breaks (`\\` or `\newline`)** or write keypoint-like separate sentences. Let LaTeX's paragraph engine naturally justify every line to the full text width (`same-length lines`). **Mandatory JD Keyword Ingestion:** When the Job Description lists specific criteria in "What We're Looking For" or "Requirements" (such as *problem-solving and analytical skills*, *eagerness to learn, adapt, and take initiative*, *web fundamentals*), weave those exact keywords and phrases directly into the summary alongside your verified tech stack. This guarantees 100% ATS keyword matching against both technical and behavioral filters. **General Roles / Career Fair Fallback:** If the target role lacks detailed JD keywords, ground the summary directly in the core architectural accomplishments of your 4 selected projects and community leadership from your profile file. Keep to strictly 3 to 4 lines.

**Colors.** Define both colors at the very top of the CV file, right after the packages. Use linkblue for every link and techblue only for the technology tags:

```latex
\definecolor{linkblue}{RGB}{0,85,190}
\definecolor{techblue}{RGB}{55,85,150}
```

## 6. Step 5: Choose your output format

Before generating the CV, choose one of these 3 format options:

- **Option 1: LaTeX Code only** — You get the `.tex` file in an artifact panel for Overleaf compilation.
- **Option 2: PDF only** — You get the finished, download-ready PDF document.
- **Option 3: Both** — You get both the LaTeX source code and the compiled PDF.

If you compile the LaTeX code on Overleaf yourself:
1. Go to overleaf.com and create a free account.
2. Choose New Project, then Blank Project.
3. Paste the LaTeX code over the default file.
4. Press Recompile and download the PDF.

## 7. Step 6: Page Budget & Structure Preservation Rules

1. **Page 1 is Always the Absolute Standard (100% 1-Page Default)**:
   - Every standard CV MUST fit on **EXACTLY 1 A4 PAGE**.
   - Page 1 MUST include ALL sections: Header, Professional Summary, Technical Skills, 4 Projects, Education, 2 Certifications, and Community & Content Experience.
   - **NEVER generate a 2nd page by default.**
   - **NEVER push Education, Certifications, or Experience to a 2nd page.**
   - References are **OMITTED BY DEFAULT** and must NEVER be included unless the user explicitly requests them in chat or the JD mandates them.

2. **NEVER Break the Visual Structure to Force 1 Page**:
   Under NO circumstances should you delete `\vspace`, reduce inter-project gaps to 0, or glue project titles directly under previous `Technologies:` lines just to force everything onto 1 page.
   - The Project separator gap (`\vspace{4.5pt plus 1pt minus 1pt}`) after each project's `Technologies:` line is **STRICTLY MANDATORY**.
   - Section titles, bullet spacing, and project separation must maintain their clean, professional visual structure.

3. **2nd Page is Strictly an Optional Fallback (Only when References are explicitly requested)**:
   The 2nd page is an optional fallback that should **ONLY** be created when:
   - The user explicitly requested References (or JD mandates them), AND
   - The candidate content + References physically cannot fit on 1 page without breaking the layout structure or stripping out `\vspace`.
   - **If references are NOT requested, a 2nd page is strictly forbidden.**

4. **Section Headings & Preamble Rules**:
   - Every section heading MUST have a 0.5pt horizontal line underneath:
     `\titleformat{\section}{\bfseries\large\scshape}{}{0pt}{}[\vspace{-4.5pt}\rule{\linewidth}{0.5pt}]`
   - NEVER omit `[\vspace{-4.5pt}\rule{\linewidth}{0.5pt}]`! Section headings must always be bold small-caps (`\scshape`) with the underline.

4. **References Layout:** Format in two side-by-side columns using `minipage[t]{0.48\textwidth}` with `\hfill` and clickable email links.

## 8. Step 7: Write strong project bullets

Each project has 1 key point in your profile file, and the CV copies it exactly as written. Write that key point in your profile file with this pattern: action verb, what you built, tools used, specific outcome.

- Good: "Provisioned custom AWS networking (VPC, subnet, internet gateway) with Terraform and automated server setup with Ansible roles over SSH."
- Good: "Built a multi-stage Jenkins pipeline with security gates for secrets, code quality, Dockerfile linting and image vulnerabilities."
- Weak: "Worked on a cloud project using many tools."
- Never: invented numbers such as "improved speed by 80%" unless you can prove them.

For each project add one "Technologies:" line in plain black text with tags colored in techblue. Strictly ONE line only: stretch the tags across the page towards the right margin (aligning under the GitHub link), but NEVER allow it to wrap onto a second line. Typically 6 to 8 core tags fit this width. For DevOps, those are infrastructure, CI/CD and container deployment projects. For software engineering, they are full-stack and API projects.

## 9. Step 8: Final checks before you send

- Count the pages (it must be exactly 1) and check that the header shows all five social links: LinkedIn, GitHub, Portfolio, Medium and YouTube. Check that there is a clear gap above every section title, that every project is separated by the 5pt gap, and that Currently Learning and Spoken Languages are on separate lines. Then open every link (GitHub, portfolio, LinkedIn, certificates) and make sure it works and is public.
- Check your email, phone number and all dates.
- Make sure your LinkedIn matches the CV (roles and dates). Recruiters often cross-check.
- Confirm every certificate and project claim is something you can explain in an interview.
- Pin your best 3 repositories on GitHub and give each a clear README.
- Read the PDF out loud once to catch typos.
- Name the file clearly, for example `YourName_CV_Company_Role.pdf`, and send it as a PDF.
- For a career fair, print several copies on A4.

## 10. Quick prompts you can reuse

- "Create a DevOps focused CV for a career fair. Use my best 4 projects. Option 2: PDF only."
- "Here is a job description. Analyze it and build my CV. Option 3: Both LaTeX and PDF."
- "Update my profile file with these new details and rebuild the CV. Option 1: LaTeX code only."
- "The CV runs onto 2 pages. Fit it to one page without removing my best project."
- "The page has blank space at the bottom. Spread the content so it fills the page."

## 11. The LaTeX template

Paste this into a blank Overleaf project, replace the placeholder text, and press Recompile. It uses only standard packages and builds on one page.

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
\titleformat{\section}{\bfseries\large\scshape}{}{0pt}{}[\vspace{-4.5pt}\rule{\linewidth}{0.5pt}]
\titlespacing*{\section}{0pt}{6.5pt plus 1.5pt minus 1pt}{2.2pt}   % AUTO-CALIBRATED 1-PAGE SECTION SPACING
\setlist[itemize]{leftmargin=1.2em,itemsep=1.2pt plus 0.4pt minus 0.4pt,topsep=1.5pt plus 0.5pt minus 0.5pt,parsep=0pt,partopsep=0pt}
\newcommand{\ghlink}[1]{\href{#1}{\textcolor{linkblue}{GitHub}}}

\begin{document}
% Balanced vertical distribution

\begin{center}
{\LARGE\bfseries\MakeUppercase{YOUR FULL NAME}}\\[1.5pt]
{\small \textbf{[Exact Job Title from Job Description]}}\\[1.5pt]
{\small City, Country \textbar{} +00 00 000 0000 \textbar{} \href{mailto:you@email.com}{\textcolor{linkblue}{you@email.com}}}\\[1pt]
% NOTE: All header links MUST display in the exact same domain URL format (e.g. medium.com/@..., youtube.com/@...) — never bare names!
{\small LinkedIn: \href{https://linkedin.com/in/you}{\textcolor{linkblue}{linkedin.com/in/you}} \textbar{} GitHub: \href{https://github.com/you}{\textcolor{linkblue}{github.com/you}} \textbar{} Portfolio: \href{https://yoursite.com}{\textcolor{linkblue}{yoursite.com}}}\\[1pt]
{\small Medium: \href{https://medium.com/@you}{\textcolor{linkblue}{medium.com/@you}} \textbar{} YouTube: \href{https://youtube.com/@you}{\textcolor{linkblue}{youtube.com/@you}}}
\end{center}

\section{Professional Summary}
{\small
% STRICT MANDATE: Write as ONE continuous paragraph (strictly 3 to 4 lines). NEVER use \\ or \newline linebreaks! Must flow naturally so LaTeX automatically justifies each line to full width (same-length lines).
Craft an evidence-based summary as a single unbroken paragraph (strictly 3 to 4 lines). Never use filler like "Motivated" or "Interested in...". Lead with verified credentials (degree, GPA, leadership/community roles from profile), name the employer's tech stack from the JD, and state the exact target role along with the technical value delivered.
}

\section{Technical Skills}
{\small
\begin{itemize}
\item \textbf{Category 1:} Skill, Skill, Skill
\item \textbf{Category 2:} Skill, Skill, Skill
\item \textbf{Currently Learning:} Skill, Skill
\item \textbf{Spoken Languages:} Language (Level), Language (Level)
\end{itemize}
}

\section{Projects}
{\small
\textbf{Project Name One} \hfill \ghlink{https://github.com/you/project-one}
\begin{itemize}
\item Action verb + what you built + tools + specific result.
% 1 key point per project, so no second item
\end{itemize}
Technologies: \textcolor{techblue}{Tool, Tool, Tool, Tool}\par

\vspace{4.5pt plus 1pt minus 1pt}  % PROJECT GAP KNOB
\noindent\textbf{Project Name Two} \hfill \ghlink{https://github.com/you/project-two}
\begin{itemize}
\item Action verb + what you built + tools + specific result.
% 1 key point per project, so no second item
\end{itemize}
Technologies: \textcolor{techblue}{Tool, Tool, Tool, Tool}\par
}

\section{Education}
{\small
\textbf{BSc (Hons) in Your Degree}, Your University \hfill \textbf{Mon YYYY -- Mon YYYY (expected)}\\
Faculty. Coursework: Course, Course, Course \hfill GPA: X.XX/4.0\\[2pt]
\textbf{G.C.E. Advanced Level}, Your School \hfill \textbf{Feb 2022}
% NOTE: Never include A/L grades ('CCC' / 'Passed with 3 C passes') as they detract from a strong university GPA.
}

\section{Courses and Certifications}
{\small
\begin{itemize}
\item Microsoft Get started developing agents in Microsoft Foundry Skill \hfill \textbf{Sep 2026 -- Microsoft}
\item AI/ML Engineer, Stage I,II \hfill \textbf{Feb 2025 -- SLIIT}
\item AWS, Terraform, Docker, Kubernetes, Jenkins Pipelines with Hands-On Labs \hfill \textbf{Feb 2026 -- KodeKloud}
\end{itemize}
}

\section{Community \& Content Experience}
{\small
% RULE: Include EVERY role and community activity from the profile file.
% Never omit or drop any experience entry.
\textbf{Role / Title 1}, Organization \hfill \textbf{Mon YYYY -- Present}
\begin{itemize}
\item One line on what you do. \hfill \href{https://credly.com/badges/your-badge}{\textcolor{linkblue}{Credly Link}}
\end{itemize}
\vspace{3pt}
\textbf{Role / Title 2}, Organization \hfill \textbf{Mon YYYY -- Present}
\begin{itemize}
\item One line on what you do.
\end{itemize}
\vspace{3pt}
\textbf{Role / Title 3}, Organization \hfill \textbf{Mon YYYY -- Present}
\begin{itemize}
\item One line on what you do.
\end{itemize}
\vspace{3pt}
\textbf{Club / Community Name, Your Role} \hfill \textbf{Mon YYYY -- Present}
\begin{itemize}
\item Role description copied from your profile file.
\end{itemize}
}

% Optional References Section (Two-column minipage layout)
% \section{References}
% {\small
% \begin{minipage}[t]{0.48\textwidth}
% \textbf{[Referee Name 1]}\\
% [Title / Designation], [Department / Company]\\
% \href{mailto:[email1]}{\textcolor{linkblue}{[email1]}}\\
% [Phone Number 1]
% \end{minipage}
% \hfill
% \begin{minipage}[t]{0.48\textwidth}
% \textbf{[Referee Name 2]}\\
% [Title / Designation], [Department / Company]\\
% \href{mailto:[email2]}{\textcolor{linkblue}{[email2]}}\\
% [Phone Number 2]
% \end{minipage}
% }
\end{document}
