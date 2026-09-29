# HelpingHands — SEM 3 Project Documentation Plan (3-Person Split)

This plan divides the full project report into **3 independent parts** so all three of you can write with AI assistance **at the same time**, with no one blocked waiting on another person's section. It follows the exact structure of your reference report ("Online Car Rental System") and the college's formatting rules.

---

## 0. Ground Rules (apply to everyone, read first)

### Formatting (from `FORMATTING_GUIDELINES_FOR_DOCUMENTATION.docx`)
| Element | Rule |
|---|---|
| Font | Times New Roman |
| Headings | 14pt, Bold |
| Subheadings | 12pt, Bold |
| Body text | 12pt, Regular |
| Code snippets | 10pt, Courier New |
| Margins | 1 inch, all sides |
| Page count | Minimum 50 pages total (design, data dictionary, source code, screenshots, etc.) |
| Numbering | Sequential — pages, tables, and figures all numbered |
| Tables/Figures | Every one needs a clear title, and a source where applicable |
| Header | Project title + document name (e.g. "HelpingHands — Software Requirement Specification") |
| Footer | Page number, format: "Sardar Vallabhbhai Global University \| Page X" |

### Hard-copy document order (from the same file)
1. Cover Page
2. College Certificate
3. Project Details
4. Acknowledgement
5. Table of Contents (with page numbers)
6. — then the report body (Sections 1–8 below)

### Cover page (from `CoverPage_Template.docx`)
Already has the exact layout: title block, a 3-row student table (Name / Enrolment Number / Class & Semester — MCA Semester III), Faculty Guide name, Academic Year 2026–2027, and the college letterhead. **Whoever assembles the final document just fills in the blanks** — don't redesign it.

### Reference structure (from `ProjectDocument_SEM3_-for_reference.pdf`)
Your report should mirror this index exactly, with HelpingHands content instead of Car Rental:
```
1. Introduction (1.1–1.8)
2. Requirement Determination & Analysis (2.1–2.2)
3. System Design (3.1 Use Case, 3.2 Class, 3.3 Sequence, 3.4 Activity, 3.5 Data Dictionary)
4. Development (4.1 Layouts/Screenshots)
5. Agile Documentation (5.1 Roadmap, 5.2 Project Plan, 5.3 User Story, 5.4 Release Plan, 5.5 Sprint Backlog, 5.6 Test Plan)
6. Proposed Enhancements
7. Conclusion
8. Bibliography
```

### Shared tool choice
The reference report's diagrams were made in **Visual Paradigm Community Edition** (free, watermark is fine — the reference doc has it too). Use the same tool so all diagrams look consistent. If your project's actual entities differ from what's described below, **inspect the real codebase/database first** — don't guess.

### One Google Doc / shared file, not three separate Word files
Create **one shared Google Doc** (or a shared Word file via OneDrive) today, with the section headers below already typed in. Each person writes directly into their own section. This avoids a painful merge step tonight. Use Times New Roman 12pt body / 14pt bold headings from the start so no one has to reformat later.

---

## 1. The Three-Way Split

| Person | Owns | Why this grouping |
|---|---|---|
| **Person A** | Section 1 (Introduction), Section 2 (Requirement Analysis), Section 8 (Bibliography), + assembling the front matter (Cover Page, Certificate, Acknowledgement, TOC) | Narrative/analysis writing — no diagramming tools needed, can start immediately from project description |
| **Person B** | Section 3 (System Design — Use Case, Class, Sequence, Activity Diagrams, Data Dictionary) | The one section that needs a diagramming tool and database/schema knowledge — keeping it with one person keeps the diagrams consistent with each other |
| **Person C** | Section 4 (Development/Screenshots), Section 5 (Agile Documentation), Section 6 (Proposed Enhancements), Section 7 (Conclusion) | Screenshot capture + project-management artifacts (roadmap, sprints, test plan) — needs the live app running, not the codebase |

Each part is roughly 15–18 pages, so three parts comfortably clear the 50-page minimum together.

---

## 2. Person A — Introduction, Requirement Analysis, Bibliography, Front Matter

### What you're writing
**Section 1: Introduction**
- 1.1 Existing System — how volunteering/NGO-corporate coordination happens today (manually, via calls/emails/spreadsheets, no central verification)
- 1.2 Need for the New System
- 1.3 Objective of the New System
- 1.4 Problem Definition
- 1.5 Core Components (Software/Hardware requirements — server side: FastAPI + PostgreSQL specs; client side: browser requirements)
- 1.6 Project Profile (Project title: HelpingHands, Group Number, Group Members — fill in your actual names)
- 1.7 Assumptions and Constraints (Internet connectivity required, browser dependency, etc. — adapt from the reference but keep it honest to your project)
- 1.8 Advantages and Limitations of the Proposed System

**Section 2: Requirement Determination & Analysis**
- 2.1 Requirement Determination — one paragraph explaining what requirements analysis covers (functional description of subsystems, data, processes, UI)
- 2.2 Targeted Users — HelpingHands has **4** user types (one more than the car rental reference's 3), so structure it like this:
  - **Volunteer**: Register, Login, Manage Profile, View/Apply to Requirements, View Application Status
  - **NGO**: Register, Login, Manage Profile, Post Requirements (once verified), View Volunteers who applied
  - **Company/Corporate**: Register, Login, Manage Profile, View Openings/CSR Focus Areas, Pledge Funds (once verified), Download CSR Report (PDF/CSV)
  - **Platform Operator**: Separate login, View Pending/Verified/Rejected NGOs and Companies, Approve/Reject/Flag/Suspend
  > Get the exact functionality list by opening the actual routers (`app/routers/auth.py`, `ngo.py`, `csr.py`, `requirements.py`, `platform_operator.py`) rather than guessing — list only what's actually implemented.

**Section 8: Bibliography**
- List the actual docs/resources you used: FastAPI docs, React docs, PostgreSQL/asyncpg docs, any Stack Overflow threads you leaned on for the JWT/Supabase-to-local-auth migration, AWS/Docker docs used for deployment. Follow the same plain-URL-list style as the reference bibliography.

### Front matter (do this last, once B and C are close to done)
1. Fill in the Cover Page template with your 3 names, enrolment numbers, faculty guide name
2. Add the College Certificate page (template usually provided by the college office — confirm with your faculty guide if you don't already have one)
3. Write the Acknowledgement (short, thank professors/college/each other — follow the reference's tone)
4. Build the Table of Contents **last**, once all three sections are merged and page numbers are final

### Step-by-step
1. Re-read the HelpingHands project description (you already have it) and write 1.1–1.4 first — these are pure narrative, no dependencies
2. Write 1.5–1.8 and the Project Profile
3. Write Section 2 — cross-check the user roles/permissions against the actual routers before finalizing
4. Draft the Bibliography as a running list while you work (add a link every time you reference something)
5. Once B and C confirm their sections are in the shared doc, do the front-matter assembly and TOC last

---

## 3. Person B — System Design (Section 3)

This is the most technical section. You need **Visual Paradigm Community Edition** installed, and you need to inspect the actual HelpingHands backend/database before drawing anything — don't invent fields that don't exist.

### 3.1 Use Case Diagram
Four actors instead of the reference's three: **Volunteer, NGO, Company, Platform Operator** (the reference only had Customer/Visitor/Admin). Map out use cases per actor:
- Volunteer: Register, Login, Manage Profile, Explore/Apply to Requirements, View Application History, Logout
- NGO: Register, Login, Manage Profile, Post Requirement (extension: blocked if unverified), View Applicants, Logout
- Company: Register, Login, Manage Profile, View CSR Openings, Pledge Funds (extension: blocked if unverified), Download CSR Report, Logout
- Platform Operator: Login (separate), View NGOs (Pending/Verified/Rejected), View Companies, Approve/Reject, Flag/Suspend, Logout

### 3.2 Class Diagram
Base classes on the actual DB tables. From what's already documented for this project: `User`, `NGOProfile`, `CorporateProfile`, `VolunteerProfile`, plus `Requirement` (NGO postings) and whatever pledge/funding entity exists for companies. **Inspect `app/models` or equivalent and the actual Postgres schema** to get exact field names and relationships (the reference class diagram shows fields, methods, and multiplicity — match that level of detail).

### 3.3 Sequence Diagrams
Do at least these (mirror the reference's 5):
1. Registration (with auto-login — note this differs from the reference, which redirects to a login screen; yours should show immediate authenticated session)
2. Login
3. NGO posts a Requirement (include the verification-status check — this is a meaningful difference from a simple car rental booking sequence, worth showing as an alt/opt block: verified → proceed, pending → reject)
4. Company pledges funds (same verification-gated pattern)
5. Platform Operator verification flow (Approve/Reject an NGO or Company)

### 3.4 Activity Diagrams
Do one per actor (Volunteer, NGO, Company, Platform Operator) showing their fork/join of available actions after login, same style as the reference's Visitor/Customer/Admin diagrams.

### 3.5 Data Dictionary
Table-by-table, same format as the reference (Column Name / Data Type / Size / Constraint / Description). Cover at minimum:
- `users` (id, role, name, email, phone, city, created_at)
- `ngo_profiles` (user_id, organization_name, registration_number, darpan_id, pan_number, focus_areas, verification_status)
- `corporate_profiles` (user_id, company_name, registration_number, cin_number, pan_number, csr_focus_areas, verification_status)
- `volunteer_profiles` (user_id, skill_tags)
- Requirement/posting table and any pledge/funding table — **pull the actual columns from the live database**, don't leave these out just because they weren't in your earlier notes

### Step-by-step
1. Inspect the real schema first (`\d` each table in `psql`, or read the SQLAlchemy models) — write down every table and column before drawing anything
2. Draw the Class Diagram first — it forces you to nail down every entity and relationship, and the Data Dictionary becomes almost a copy-paste from it afterward
3. Draw the Use Case Diagram next
4. Do the 5 Sequence Diagrams
5. Do the 4 Activity Diagrams
6. Fill in the Data Dictionary tables last, using the Class Diagram as your source of truth
7. Export every diagram as an image and paste into the shared doc under the right subheading, numbered as Figures (e.g. "Figure 3.1: Use Case Diagram")

---

## 4. Person C — Development, Agile Documentation, Enhancements, Conclusion

### Section 4: Development (4.1 Layouts)
Screenshot every meaningful screen, same style as the reference (one per subsection, numbered, with a short caption). At minimum:

**Volunteer**: Registration, Login, Home/Explore Requirements, Requirement Details, Apply flow, Application History, Edit Profile

**NGO**: Registration (with the 9-digit reg-number field and side-by-side password/confirm-password), Login, Dashboard (pending vs verified state — capture both if you can), Post Requirement form, View Applicants

**Company**: Registration, Login, CSR Dashboard, Pledge Funds form, CSR Report page (show both PDF and CSV download buttons)

**Platform Operator**: Login, Dashboard, NGO section (pending list, approve/reject buttons), Company section (same), Flag/Suspend actions on a verified org

> Take these screenshots from the deployed/running app once it's up (coordinate timing with whoever is doing the AWS deployment) so they reflect the final cosmetic changes, not an older local build.

### Section 5: Agile Documentation
Mirror the reference's structure exactly:
- **5.1 Agile Roadmap/Schedule** — a Gantt-style chart grouping your work into 3 phases (mirror the reference's structure): e.g. Phase 1 = Auth + Core CRUD (Volunteer/NGO/Company registration & profiles), Phase 2 = Requirements/Applications + CSR Pledge flow, Phase 3 = Platform Operator verification workflow + CSV export + polish
- **5.2 Agile Project Plan** — task table with Responsible/Start/End/Days/Status columns, one row per module (Registration, Login, NGO Module, Company Module, Requirements Module, Platform Operator Module, CSR Report Module) — use your actual dates, not the reference's
- **5.3 Agile User Story** — table: Type of User / I want to / Result — at least one row per actor per major action (you need more rows than the reference's 10 since you have 4 actor types instead of 3)
- **5.4 Agile Release Plan** — sprint table with Start/End/Duration/Status/Release Date, grouped by feature set
- **5.5 Agile Sprint Backlog** — task/responsible/story/sprint-ready/days/priority/status table
- **5.6 Agile Test Plan** — same format as the reference: Test No / Date / Action / Expected Result / Actual Result / Pass — cover registration, login (all 4 roles), post requirement (pending vs verified), pledge funds (pending vs verified), platform operator approve/reject/flag/suspend, CSV export

> You can pull actual dates from your Git commit history (`git log --pretty=format:"%ad %s" --date=short`) instead of reconstructing them from memory — this keeps the Agile section honest and saves time.

### Section 6: Proposed Enhancements
3–6 bullets in the same style as the reference (e.g. "We'll add real-time notifications for approval status", "We'll add a mobile app", "We'll add multi-language support", "We'll add a ratings/feedback system for completed volunteer work").

### Section 7: Conclusion
1 short paragraph, same tone as the reference — what the platform achieves and for whom.

### Step-by-step
1. Get the app running (coordinate with whoever handles deployment — screenshots should come from the same build being demoed)
2. Walk through every user flow end-to-end as each of the 4 roles, screenshotting as you go — this doubles as your own pre-review QA pass
3. Pull your Git log for real dates, build the Agile tables from that instead of estimating
4. Write the Test Plan last, using the actual behavior you observed while screenshotting (if something didn't work as expected, note it honestly — Pass/Fail both happen in real test plans)
5. Write Enhancements and Conclusion last, once you've seen the whole app fresh in your head from the screenshot pass

---

## 5. Merge & Finalize (tonight, once all three are ~80% done)

1. All three sections should already be in **one shared doc** — no separate merge step needed if you set it up that way from the start
2. Person A applies the front matter (Cover Page, Certificate, Acknowledgement) and builds the Table of Contents last, since page numbers only settle once everyone's content is in
3. Do one pass together (voice call, share screen) checking:
   - [ ] Every heading is 14pt bold, subheading 12pt bold, body 12pt regular, Times New Roman throughout
   - [ ] Every table and figure has a number and title
   - [ ] Header shows project title + document name on every page
   - [ ] Footer shows page number in the required format
   - [ ] Total page count is 50+
   - [ ] Section numbering is continuous and matches the TOC
4. Export to PDF, do a final skim of the PDF (not the editor) since page breaks sometimes shift things
5. Print or submit per your college's actual submission process

---

## 6. Timeline for Tonight

| Time | Person A | Person B | Person C |
|---|---|---|---|
| Now – +2h | Draft Section 1 | Inspect schema, draw Class Diagram | Get app running, start screenshotting Volunteer + NGO flows |
| +2h – +4h | Draft Section 2, start Bibliography | Draw Use Case + Sequence Diagrams | Screenshot Company + Platform Operator flows |
| +4h – +5h | Wait for B/C to finish; review own sections | Draw Activity Diagrams, fill Data Dictionary | Build Agile tables from Git log |
| +5h – +6h | Assemble front matter + TOC | Final diagram cleanup, paste into shared doc | Write Test Plan, Enhancements, Conclusion |
| +6h | **All three**: joint formatting/QA pass, export PDF | | |

Adjust the hours to your actual start time tonight — the important part is the order: narrative sections (A) and diagrams (B) can start with zero dependency on the running app, while C needs the app live first.
