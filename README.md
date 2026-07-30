# Solvd AI

**An AI physics tutor that teaches on a whiteboard.**

Solvd AI is an AI tutoring platform that turns any physics problem into a real-time, step-by-step visual explanation. A student types a question or photographs their handwritten solution, and Solvd generates a live animated whiteboard walkthrough showing where the reasoning broke down and what the correct path looks like.

Most "AI tutors" today are chatbots bolted onto existing content libraries. Solvd was built the other way around: the agent architecture, the animation engine, and the feedback pipeline were all designed specifically for how physics learning actually works.

---

## SEP Project Overview

This GitHub page is the official progress and reporting page for our SEP project under the Innovation Lab (iLAB) at CCDS.

|                  |                                          |
| ---------------- | ---------------------------------------- |
| **Team Name**    | Solvd AI                                 |
| **iLAB Funding** | S$3,000 (equipment / operating expenses) |

This repository does not include the full production codebase, as parts of the project involve private product development, and a live pilot with an external partner. This page documents project direction, objectives, technical progress, financial updates, competitions, and current status.

---

## Team

| Role       | Name            | Email                   | Course of Study        | Expected Graduation |
| ---------- | --------------- | ----------------------- | ---------------------- | ------------------- |
| Co-Founder | Kashyap Ahaskar | ahaskar001@e.ntu.edu.sg | CCDS, Computer Science |
| Co-Founder | Aadi Jha        | aadi001@e.ntu.edu.sg    | CCDS, Computer Science |

**Responsibilities**

- **Kashyap Ahaskar** — Product direction, AI architecture, SolvdEngine animation library, partnerships and fundraising
- **Aadi Jha** — Backend systems, agent pipeline, infrastructure, product implementation

---

## The Problem

Across India and Southeast Asia, millions of students preparing for JEE, NEET, and board exams hit the same wall. A student gets stuck on a physics problem at 11pm and their options are: wait until tomorrow to ask a teacher, scroll YouTube hoping to find the right explanation, or give up.

This is not a content problem. There is more free physics content online than any student can consume. It is a **comprehension and feedback problem**:

- Pre-recorded videos cannot tell a student where _their_ reasoning went wrong
- Text-based chatbots explain physics in paragraphs, when physics is fundamentally visual
- Human doubt-solving does not scale, and it is not available at 11pm

Solvd exists to close the gap between confusion and clarity.

---

## The Product

### 1. Visual, step-by-step explanations

The student submits a problem (typed, or as a photo of handwritten work). Solvd produces a synchronised whiteboard explanation that builds diagrams, equations, and reasoning step by step, the way a tutor would work through it on paper.

### 2. Handwritten solution correction

Instead of only marking an answer right or wrong, Solvd localises the exact step where the student's reasoning broke down and explains the correction pedagogically.

### 3. Real-time rendering

Explanations render in **under 10 seconds**. This is the core technical bet, and the reason we abandoned Manim early on (30–120s render times, designed for offline video production rather than live tutoring).

---

## Technical Architecture

**Multi-agent pipeline on Google ADK**

| Agent        | Responsibility                                                 |
| ------------ | -------------------------------------------------------------- |
| Solver       | Parses the problem, produces the step-by-step physics solution |
| Animation    | Converts the solution into a whiteboard animation script       |
| Orchestrator | Coordinates the agents and manages conversational follow-up    |

**SolvdEngine — custom animation library**

A TypeScript SVG/DOM animation library built in-house for real-time physics diagrams, published on npm under `@ahaskar04`.

- Sub-10-second in-browser render times
- `stroke-dasharray` timing control for drawing-style animation
- Multi-contour character subpath splitting
- MathJax 3 integration for LaTeX rendering

**Supporting stack**

- Florence-2 for bounding-box localisation on handwritten solutions
- ElevenLabs TTS for voice-guided explanations

The point of building our own engine rather than wrapping an existing one is that render latency _is_ the product. A tutoring experience that takes two minutes to respond is not a tutoring experience.

---

## Traction and Current Status

**Physics Wallah pilot** — Active pilot with Physics Wallah, one of India's largest EdTech platforms (100M+ users). This began as a credit-bearing NTU internship engagement building AI doubt-solving features and has developed into a product pilot.

**NTU iLAB SEP** — Accepted into the CCDS Innovation Lab Student Entrepreneurship Programme (Mar 2026), with S$3,000 in funding for development and operating expenses.

**External grant** — Approximately US$5,000 in early grant support secured from an India-based investor.

**Go-to-market** — Currently evaluating two distribution paths:

1. **B2B2C** — licensing to coaching institutes and EdTech platforms, starting in India and Southeast Asia
2. **B2C freemium** — Solvd as a standalone student-facing product, using partner distribution as the top of funnel

Validating which of these has stronger willingness to pay and long-term revenue potential is our primary open question this quarter.

---

## Progress Updates

As required by SEP, a progress video or slide update is uploaded at least once every 2 months.

| Update Period  | Focus                                                        | YouTube Link    | Status                  |
| -------------- | ------------------------------------------------------------ | --------------- | ----------------------- |
| March 2026     | SEP kickoff: project overview, objectives, team              | _[insert link]_ | _[Completed / Pending]_ |
| May 2026       | Development progress: agent pipeline and SolvdEngine         | _[insert link]_ | _[Completed / Pending]_ |
| July 2026      | Pilot progress, handwriting correction, distribution testing | _[insert link]_ | Pending                 |
| September 2026 | MVP progress and early usage data                            | _[insert link]_ | Upcoming                |

### Supporting Materials

| Material          | Link            |
| ----------------- | --------------- |
| SEP update slides | _[insert link]_ |
| SolvdEngine (npm) | `@ahaskar04`    |

---

## Milestones

### Completed

- Multi-agent solver architecture on Google ADK
- SolvdEngine v1 built and published on npm
- Migration off Manim to in-house real-time rendering (sub-10s)
- MathJax 3 integration for LaTeX rendering
- Handwritten solution error localisation using Florence-2
- Voice-guided explanation pipeline
- Physics Wallah pilot secured and running
- Accepted into NTU CCDS iLAB SEP with S$3K funding
- External grant support secured

### In Progress

- MVP hardening ahead of the Feb 2027 SEP milestone
- Expanding topic coverage across the JEE physics syllabus
- Distribution testing: B2B2C licensing vs. B2C freemium
- Mentor engagement through iLAB (EdTech and fundraising)
- Pricing and unit economics modelling

### Next Steps

- Convert the Physics Wallah pilot into a defined commercial arrangement
- Collect structured usage and learning-outcome data from pilot students
- Finalise the initial pricing model
- Participate in at least one international hackathon (SEP requirement)
- Deploy a demo system in the CCDS Innovation Lab (SEP requirement)
- Prepare pre-seed fundraising materials

---

## Project Objectives

1. Build Solvd AI into a working, production-grade AI physics tutor with real students using it.
2. Validate that real-time visual explanation measurably improves comprehension over text-based AI tutoring.
3. Convert the Physics Wallah pilot into a commercial relationship.
4. Determine the right distribution model between institutional licensing and direct-to-student.
5. Ship an MVP and a workable business plan by Feb 2027, per SEP requirements.
6. Expand SolvdEngine's coverage so explanations generalise beyond physics into chemistry and mathematics.

---

## Financial Updates

| Source                 | Amount    | Purpose                           | Status  |
| ---------------------- | --------- | --------------------------------- | ------- |
| External grant (India) | ~US$5,000 | Product development, AI API costs | Secured |

Primary expenditure to date: LLM and AI API costs, hosting and infrastructure, development tooling.

---

## Contact

**Team Solvd AI**
Kashyap Ahaskar and Aadi Jha

Email: ahaskar001@e.ntu.edu.sg
