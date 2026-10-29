# How to Build a Clean, Professional One-Page CV with AI

A step-by-step guide for students and interns, based on a DevOps internship CV built with an AI assistant, LaTeX and Overleaf.

## 1. What the finished CV looks like

The goal is a CV that is clean, easy to scan in 10 to 20 seconds, and readable by applicant tracking systems (ATS). These are the design rules:

- Strictly one A4 page, single column. The CV must never run onto a second page, and the content must fill the page right down to the bottom margin.
- Latin Modern font (the classic LaTeX look), 10 pt body text with 9 pt content blocks.
- No tables, photos, icons, skill bars, graphics or colored backgrounds.
- Section order: Header, Professional Summary, Technical Skills, Projects, Education, Certifications and Training, Experience.
- Section headings in bold small capitals with a thin line underneath.
- The header must always show every social link from your profile file: LinkedIn, GitHub, Portfolio, Medium and YouTube. Never leave one out. Each link is blue and the label in front of it stays black.
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

1. Font: Latin Modern (`\usepackage{lmodern}`).
2. Certificates: include only the 2 or 3 strongest ones that relate to the job description. Never more than 3.
3. Include strictly 4 projects in every CV. Choose the 4 that best match the job requirements. If the profile file has only 4, include all 4.
4. Use only facts from the profile file. Never invent details.
5. Show the degree dates as "Mon YYYY - Mon YYYY (expected)" with no year or semester of study.
6. Length: strictly one page. Never produce a second page.
7. Project descriptions: copy each project's description exactly as written in the profile file (1 key point per project). Do not rewrite it or add bullets.
8. Technology tags: no italics. Color only the tags with \\textcolor{techblue}{...}. The color techblue is defined at the very top of the file.
9. Header: always show all social links from the profile file (LinkedIn, GitHub, Portfolio, Medium, YouTube), none missing. Links are blue; GitHub and Credly links have no underline.
10. Full-page layout: no large blank space at the bottom of the page.

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

Deliver, separately: (a) recruiter assessment, (b) the CV, (c) ATS
keyword review, (d) a checklist of details I must verify myself.
Never claim the CV guarantees an interview or ATS success.

Strict rules:
- The CV must fit on exactly ONE page. Never produce a second page.
- The header must always include ALL my social links from the profile
  file: LinkedIn, GitHub, Portfolio, Medium and YouTube. Never skip any.
- Read the job requirements first, then check them against my profile
  file, and only then build the CV.
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
- **Skills follow the projects.** Keep the Technical Skills section simple and easy to read, with a few short category lines (about 5 to 7). Include the languages and the most important tools used in the 4 projects on the CV, and always include every skill the job description asks for that your projects demonstrate. Leave out minor tools and small details so the section does not become crowded. Update the skills whenever the 4 projects change.
- **2 or 3 certificates only.** Show only the 2 or 3 strongest certificates that relate to the job description. Never more than 3.
- **Experience line.** Under Experience, put the Credly link on the same line as the description, aligned to the right edge of the page. Also add every club and society from the profile file to the Experience section, with the role, dates and description exactly as written there.
- **Education.** Show your university degree and also your G.C.E. Advanced Level details from the profile file: the school on the main line, then the A/L stream and result on the line below, in professional wording, for example: Technology Stream. Passed with 3 C passes.
- **One page.** All of this must still fit on exactly one page.

**Project spacing.** After each project's "Technologies:" line, add `\vspace{5pt}` before the next project title, so the projects are clearly separated.

**Professional summary.** Copy the summary exactly from your profile file. Do not rewrite it for each job.

**Colors.** Define both colors at the very top of the CV file, right after the packages. Use linkblue for every link and techblue only for the technology tags:

```latex
\definecolor{linkblue}{RGB}{0,85,190}
\definecolor{techblue}{RGB}{55,85,150}
```

## 6. Step 5: Ask for the right output

Use one of these requests:

- "Create the CV as a PDF only." You get the finished file to send.
- "Create the CV as a PDF and also the Overleaf LaTeX code separately." You get a PDF plus a `.tex` file you can edit later.

If your AI cannot create files, ask for the LaTeX code and compile it yourself:

1. Go to overleaf.com and create a free account.
2. Choose New Project, then Blank Project.
3. Paste the LaTeX code over the default file.
4. Press Recompile and download the PDF.

The LaTeX template at the end of this guide produces the same clean look.

## 7. Step 6: Make it fill exactly one page

The CV must be strictly one page: never a second page, and no big empty space at the bottom. It should end close to the bottom margin. These are the controls:

- **Section spacing:** the number in `\titlespacing*{\section}{0pt}{8pt}{3pt}`. Raise 8pt to spread sections out, lower it to tighten.
- **Project gap:** the `\vspace{5pt}` between projects.
- **Bullet spacing:** `itemsep` inside `\setlist[itemize]`.

If the CV runs onto a second page, trim in this order:

1. Reduce spacing slightly.
2. Shorten the summary by a sentence.
3. Merge two skill lines, but never remove a skill used in the 4 projects.
4. Remove the least relevant certificate line.
5. Never drop a project: the CV must keep exactly 4 projects. Reduce spacing or shorten the summary instead.

If there is blank space at the bottom, raise the section spacing one point at a time until the page is full.

## 8. Step 7: Write strong project bullets

Each project has 1 key point in your profile file, and the CV copies it exactly as written. Write that key point in your profile file with this pattern: action verb, what you built, tools used, specific outcome.

- Good: "Provisioned custom AWS networking (VPC, subnet, internet gateway) with Terraform and automated server setup with Ansible roles over SSH."
- Good: "Built a multi-stage Jenkins pipeline with security gates for secrets, code quality, Dockerfile linting and image vulnerabilities."
- Weak: "Worked on a cloud project using many tools."
- Never: invented numbers such as "improved speed by 80%" unless you can prove them.

For each project add one "Technologies:" line in plain black text listing the tools used. Choose the 4 projects that best match the job requirements. For DevOps, those are infrastructure, CI/CD and container deployment projects. For software engineering, they are full-stack and API projects.

## 9. Step 8: Final checks before you send

- Count the pages (it must be exactly 1) and check that the header shows all five social links: LinkedIn, GitHub, Portfolio, Medium and YouTube. Then open every link (GitHub, portfolio, LinkedIn, certificates) and make sure it works and is public.
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
\usepackage[margin=0.5in,top=0.4in,bottom=0.4in]{geometry}
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
\titleformat{\section}{\bfseries\normalsize\scshape}{}{0pt}{}[\vspace{-5pt}\rule{\linewidth}{0.5pt}]
\titlespacing*{\section}{0pt}{8pt}{3pt}   % SECTION SPACING KNOB
\setlist[itemize]{leftmargin=1.2em,itemsep=0.5pt,topsep=1pt,parsep=0pt,partopsep=0pt}
\newcommand{\ghlink}[1]{\href{#1}{\textcolor{linkblue}{GitHub}}}

\begin{document}
\begin{center}
{\LARGE \textbf{YOUR FULL NAME}}\\[3pt]
{\small Aspiring [Role] \textbar{} Seeking [Role] Internship}\\[2pt]
{\small City, Country \textbar{} +00 00 000 0000 \textbar{} you@email.com}\\[2pt]
{\small LinkedIn: \href{https://linkedin.com/in/you}{\textcolor{linkblue}{linkedin.com/in/you}} \textbar{}
GitHub: \href{https://github.com/you}{\textcolor{linkblue}{github.com/you}} \textbar{}
Portfolio: \href{https://yoursite.com}{\textcolor{linkblue}{yoursite.com}}}\\[2pt]
{\small Medium: \href{https://medium.com/@you}{\textcolor{linkblue}{medium.com/@you}} \textbar{}
YouTube: \href{https://youtube.com/@you}{\textcolor{linkblue}{youtube.com/@you}}}
\end{center}

\section{Professional Summary}
{\small
Copy your professional summary exactly from your profile file.
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

\vspace{5pt}  % PROJECT GAP KNOB
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
Faculty. Coursework: Course, Course, Course \hfill GPA: X.XX/4.0\\[3pt]
\textbf{G.C.E. Advanced Level}, Your School \hfill \textbf{YYYY}\\
Your Stream. Passed with X passes.
}

\section{Certifications and Training}
{\small
\begin{itemize}
\item Course name, Issuer (Mon YYYY)
\end{itemize}
}

\section{Experience}
{\small
\textbf{Role}, Organization \hfill \textbf{Mon YYYY -- Present}
\begin{itemize}
\item One line on what you do. \hfill \href{https://credly.com/badges/your-badge}{\textcolor{linkblue}{Credly Link}}
% Credly link stays on the same line as the text, right-aligned
\end{itemize}
\vspace{3pt}
\textbf{Club Name, Your Role} \hfill \textbf{Mon YYYY -- Present}
\begin{itemize}
\item Club description copied from your profile file.
\end{itemize}
}
\end{document}
```

Tips for using the template:

- Add more `\textbf{Project...}` blocks until you have exactly 4 projects, each with 1 key point copied from your profile file.
- Delete the Credly line if you have no badge to link. Keep every social link you own in the header (LinkedIn, GitHub, Portfolio, Medium, YouTube) and remove only the ones you do not have.
- Use `--` for an en dash in date ranges and `\&` for an ampersand in LaTeX.
- Never put tables, images or columns in the CV, because they can break ATS parsing.
