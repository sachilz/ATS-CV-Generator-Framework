# How to Build a Clean, Professional One-Page CV with AI

A step-by-step guide for students and interns, based on a DevOps internship CV built with an AI assistant, LaTeX and Overleaf.

## 1. What the finished CV looks like

The goal is a CV that is clean, easy to scan in 10 to 20 seconds, and readable by applicant tracking systems (ATS). These are the design rules:

- Strictly one A4 page, single column (unless conditional references require 2 pages).
- Margins: STRICT FIXED CONSTANT `\usepackage[margin=0.42in]{geometry}` (Top = Bottom = Left = Right = 0.42in). Never change this margin value under any circumstances across different CVs.
- Latin Modern font (the classic LaTeX look), 10 pt body text with 9 pt content blocks.
- No tables, photos, icons, skill bars, graphics or colored backgrounds.
- Section order: Header, Professional Summary, Technical Skills, Projects, Education, Certifications and Training, Community & Content Experience, References (conditional).
- Section headings in bold small capitals with a thin line underneath.
- The header must always show every social link from your profile file: LinkedIn, GitHub, Portfolio, Medium and YouTube. Strictly uniform URL formatting: all links must display their clean domain/URL path (e.g. `linkedin.com/in/sachilz`, `github.com/sachilz`, `sachilz.me`, `medium.com/@sachilz`, `youtube.com/@NextOpz`) — never bare usernames or plain channel text like "NextOps" or "sachilz". Each link is blue and the label in front stays black.
- Each project has a bold title, a blue "GitHub" link on the right (no underline), the project description copied exactly from your profile file (1 key point each), and a "Technologies:" line (no italics) whose technology tags are colored with techblue.
- Dates aligned to the right edge of the page.
- Only relevant content for the target job. Leave out weak or unrelated items.

## 2. Step 1: Write your profile file (your source of truth)

Create one text or Markdown file with every fact about you. The AI must only use what is written there, which stops it from inventing anything. Use these headings:

1. Personal and contact details: name, email, phone, city and country, LinkedIn, GitHub, portfolio, Medium, YouTube. Also write your professional summary here (3 to 4 lines); the CV copies it exactly as written.
2. Education: degree, university, dates, GPA, relevant coursework. Also your A/L school, year, stream and result.
3. Technical skills, grouped by category (languages, front-end, back-end, databases, CI/CD, containers, cloud, security tools).
4. Projects: title, GitHub link, technologies, and 1 factual key point (the description) for each one.
5. Experience and community: role, organization, dates, what you really do. Include every club and society you belong to, with your role and a short description.
6. Certifications and training: name, issuer, date. Label course certificates honestly as "Certifications and Training".
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
8. Technology tags: no italics. Color only the tags with \\textcolor{techblue}{...}. The color techblue is defined at the very top of the file.
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
2. Assess my fit: strongest matches, gaps, risks.
3. Ask me concise questions only if essential information is missing.
4. Build a one-page, single-column, ATS-friendly CV that follows my
   standing rules and the design template.
5. Run a quality check: every claim supported, keywords natural, no
   spelling or date errors, no placeholders.

Deliver: (a) The CV via LaTeX artifact/canvas only, and (b) an ATS Keyword Review in the chat listing Matched Keywords included and Missing Keywords from the JD (so the user can review and manually adjust if needed).
Never claim the CV guarantees an interview or ATS success.

Strict rules:
- The CV must fit on exactly ONE page. Never produce a second page.
- The header must always include ALL my social links from the profile
  file: LinkedIn, GitHub, Portfolio, Medium and YouTube. Never skip any.
- Keep a clear gap above every section title: at least 8pt of space
  before each heading. Never squeeze the headings against the text above.
- Use the LaTeX template from this guide exactly as given: do not change
  the preamble or the section formatting, only the content.
- Read the job requirements first, then check them against my profile
  file, and only then build the CV.
- Give me the LaTeX code as a file or canvas that I can open and
  download, never pasted inside the chat message.
```

## 5. Step 4: Give the target

Tell the AI what you are applying for:

- A job posting: paste the text or upload a screenshot of it.
- A career fair: say "create a DevOps focused CV for a career fair, use my best 4 projects".
- A general role: say "create a Software Engineer internship CV".

The AI then reorders your skills, copies your summary from the profile file, picks the best projects, and keeps only the relevant certificates. Every role needs its own version of the CV.

**Recommended order of messages.** Send things in this order so the AI never skips a rule:

1. In your first message, upload this guide and your profile file (for example `info.md`). Say: "Read both. Follow this guide for layout and rules, and use my profile file as the only source of facts."
2. Wait for the AI to confirm. Do not send the job description yet.
3. Send the job description last. The AI must read the job requirements, check them against your profile file, and only then build the CV, picking the skills, projects and certificates that match what the job asks for.
4. Check the result before you send it: exactly one page, and all five social links in the header (LinkedIn, GitHub, Portfolio, Medium, YouTube).

**CV content rules.** Every CV must follow these:

- **Exactly 4 projects.** Always show exactly 4 projects, with each description copied exactly as written in your profile file (1 key point each). When you add new projects to the profile file later, the AI must read the job requirements and pick the 4 best matching projects.
- **Skills align with both the JD and the projects.** Keep the Technical Skills section simple and easy to read, with 5 to 7 short category lines. Prioritize and include every skill mentioned in the Job Description (JD) that exists in your profile file, along with the core tools and languages used in the 4 chosen projects. Leave out minor, unrelated tools so the section stays clean. Update the skills whenever the target role or the 4 projects change.
- **Strictly 2 certificates only.** Show strictly the 2 strongest certificates directly relevant to the target role. Limiting to 2 certificates is essential to prevent the CV from overflowing to a 2nd page.
- **Experience Heading: `\section{Community \& Content Experience}` & Include ALL roles.** Name this section `\section{Community \& Content Experience}` (escaped as `\&` in LaTeX). Because undergraduates do not have corporate industry jobs yet, labeling student ambassador roles and YouTube channels as "Professional Experience" can look dishonest to recruiters. "Community & Content Experience" is 100% transparent and respected. You MUST include **EVERY SINGLE ROLE** listed in the candidate profile's Experience and Community section (Student Ambassador, YouTube, Medium, Clubs). NEVER omit, filter, or drop any role. Right-align Credly badges. Use `\vspace{3.5pt plus 1pt minus 1pt}` between entries.
- **Education.** Show your university degree (dates, GPA, coursework) and your G.C.E. Advanced Level (school name and year only). **STRICT RULE: Do NOT include A/L results or grades ('CCC' / 'Passed with 3 C passes') on the CV.** The candidate's strong 3.52 university GPA stands on its own, and listing 'CCC' hurts the candidate profile and wastes vertical space.
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

**Professional summary (ATS Job-Matched).** Tailor the professional summary to naturally incorporate the exact target Job Title from the JD (e.g. "Motivated IT undergraduate... seeking a Full Stack Software Engineer – Intern position...") and key qualifying terms from the JD (such as "motivated", "collaborative", "responsive web applications") while staying 100% truthful to the candidate's profile facts. Keep to strictly 3 to 4 lines.

**Colors.** Define both colors at the very top of the CV file, right after the packages. Use linkblue for every link and techblue only for the technology tags:

```latex
\definecolor{linkblue}{RGB}{0,85,190}
\definecolor{techblue}{RGB}{55,85,150}
```

## 6. Step 5: Ask for the right output

Use one of these requests:

- "Create the CV as a PDF only." You get the finished file to send.
- "Create the CV as a PDF and also the Overleaf LaTeX code separately." You get a PDF plus a `.tex` file you can edit later.

Always ask for the LaTeX code as a file or canvas that you can open and download, never pasted inside the chat message. If your AI cannot create files, ask for the LaTeX code in a canvas and compile it yourself:

1. Go to overleaf.com and create a free account.
2. Choose New Project, then Blank Project.
3. Paste the LaTeX code over the default file.
4. Press Recompile and download the PDF.

The LaTeX template at the end of this guide produces the same clean look.

## 7. Step 6: Page Budget & Structure Preservation Rules

1. **Page 1 is Always the Priority Target**:
   If all content (even with References, if spacing allows naturally) can fit cleanly on **1 single page**, keep it on **1 Page**! Ignore the 2nd page entirely.

2. **NEVER Break the Visual Structure to Force 1 Page**:
   Under NO circumstances should you delete `\vspace`, reduce inter-project gaps to 0, or glue project titles directly under previous `Technologies:` lines just to force everything onto 1 page.
   - The Project separator gap (`\vspace{4.5pt plus 1pt minus 1pt}`) after each project's `Technologies:` line is **STRICTLY MANDATORY**.
   - Section titles, bullet spacing, and project separation must maintain their clean, professional visual structure.

3. **2nd Page is Strictly an Optional Fallback**:
   The 2nd page is an optional fallback that should **ONLY** be created when:
   - Content is genuinely too long (e.g. dense projects + experience + references included), AND
   - It is physically impossible to keep on 1 page without breaking the layout structure or stripping out `\vspace`.
   When a 2nd page is created, distribute the sections cleanly across both pages (Page 1: Header, Summary, Skills, Projects; Page 2: Education, Certifications, Community & Content Experience, References) so that both pages look balanced, intentional, and readable.

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

- "Create a DevOps focused CV for a career fair. Use my best 4 projects. PDF only."
- "Here is a job description. Analyze it, tell me my gaps, then create a tailored one-page CV as a PDF and the Overleaf code separately."
- "Update my profile file with these new details and rebuild the CV."
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
Tailor your professional summary to include the exact target Job Title from the JD and key descriptive ATS keywords (e.g., "motivated", "collaborative") based on your profile facts (3 to 4 lines).
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
Technologies: \textcolor{techblue}{Tool, Tool, Tool, Tool}

\vspace{4.5pt plus 1pt minus 1pt}  % PROJECT GAP KNOB
\textbf{Project Name Two} \hfill \ghlink{https://github.com/you/project-two}
\begin{itemize}
\item Action verb + what you built + tools + specific result.
% 1 key point per project, so no second item
\end{itemize}
Technologies: \textcolor{techblue}{Tool, Tool, Tool, Tool}
}

\section{Education}
{\small
\textbf{BSc (Hons) in Your Degree}, Your University \hfill \textbf{Mon YYYY -- Mon YYYY (expected)}\\
Faculty. Coursework: Course, Course, Course \hfill GPA: X.XX/4.0\\[2pt]
\textbf{G.C.E. Advanced Level}, Your School \hfill \textbf{YYYY}
% NOTE: Never include A/L grades ('CCC' / 'Passed with 3 C passes') as they detract from a strong university GPA.
}

\section{Certifications and Training}
{\small
\begin{itemize}
\item Course name, Issuer (Mon YYYY)
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
% \textbf{Referee Name One}\\
% Senior Lecturer, Faculty of IT, Horizon Campus\\
% \href{mailto:email@horizoncampus.edu.lk}{\textcolor{linkblue}{email@horizoncampus.edu.lk}}\\
% +94 77 000 0000
% \end{minipage}
% \hfill
% \begin{minipage}[t]{0.48\textwidth}
% \textbf{Referee Name Two}\\
% Emeritus Professor, University of Ruhuna\\
% \href{mailto:email@gmail.com}{\textcolor{linkblue}{email@gmail.com}}\\
% +94 77 000 0000
% \end{minipage}
% }
\end{document}
```

Tips for using the template:

- Add more `\textbf{Project...}` blocks until you have exactly 4 projects, each with 1 key point copied from your profile file.
- Under Experience, include **EVERY** role, content creation, writing, or club from the profile file. Never drop any role.
- Delete the Credly line if you have no badge to link. Keep every social link you own in the header (LinkedIn, GitHub, Portfolio, Medium, YouTube) and remove only the ones you do not have.
- Use `--` for an en dash in date ranges and `\&` for an ampersand in LaTeX.
- Never put tables, images or columns in the CV, because they can break ATS parsing.
