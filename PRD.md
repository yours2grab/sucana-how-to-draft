# How-To Draft Article Agent — PRD

## Goal

After every build session, produce a comprehensive step-by-step article that documents exactly how we built it. The article must be so detailed that someone with zero context can follow it and get the same result.

## User Story

As Virgil, after I build something in Claude Code, I want to run one command and get a complete how-to article that captures every step, every decision, and every command, so I can turn it into a blog post, newsletter issue, or LinkedIn content.

## Architecture

```
┌─────────────────────────────────────────────────┐
│              HOW-TO DRAFT AGENT                  │
│                                                  │
│  STEP 0: Context Interview                       │
│  ┌─────────────────────────────────────────┐    │
│  │ Ask: "Why did you build this?"          │    │
│  │ Ask: "What was your experience?"        │    │
│  │ Capture the story behind the build      │    │
│  └─────────────────────────────────────────┘    │
│           │                                      │
│           ▼                                      │
│  STEP 1: Load Voice                              │
│  ┌─────────────────────────────────────────┐    │
│  │ Read Virgil_Voice_MASTER.md             │    │
│  │ Internalize tone, rules, guardrails     │    │
│  └─────────────────────────────────────────┘    │
│           │                                      │
│           ▼                                      │
│  STEP 2: Analyze the Build                       │
│  ┌─────────────────────────────────────────┐    │
│  │ Read the conversation history           │    │
│  │ Extract every step taken                │    │
│  │ Extract every decision and WHY          │    │
│  │ Extract every command, file, link       │    │
│  │ Note conversations between user + AI   │    │
│  └─────────────────────────────────────────┘    │
│           │                                      │
│           ▼                                      │
│  STEP 3: Structure the Article                   │
│  ┌─────────────────────────────────────────┐    │
│  │ Title: "How We Built [Thing]"           │    │
│  │ Intro: Why we built it (from Step 0)    │    │
│  │ What we built: End result description   │    │
│  │ Steps: Every micro-step, numbered       │    │
│  │ Each step: What + Why + How (command)   │    │
│  │ What we'd do differently                │    │
│  │ The stack: Tools used                   │    │
│  └─────────────────────────────────────────┘    │
│           │                                      │
│           ▼                                      │
│  STEP 4: Write in Virgil's Voice                 │
│  ┌─────────────────────────────────────────┐    │
│  │ First person                            │    │
│  │ Simple words (7-year-old test)          │    │
│  │ Short sentences                         │    │
│  │ Real names (Victor, Vinod)              │    │
│  │ No jargon without explanation           │    │
│  │ Every step starts with a verb           │    │
│  └─────────────────────────────────────────┘    │
│           │                                      │
│           ▼                                      │
│  STEP 5: 10-Year-Old Test                        │
│  ┌─────────────────────────────────────────┐    │
│  │ Read every step                         │    │
│  │ Can a child follow this?                │    │
│  │ Are all links exact?                    │    │
│  │ Are all commands copy-pasteable?        │    │
│  │ Is any step assumed or skipped?         │    │
│  │ Would they need to ask a question?      │    │
│  │ If yes → add the missing detail         │    │
│  └─────────────────────────────────────────┘    │
│           │                                      │
│           ▼                                      │
│  STEP 6: Save                                    │
│  ┌─────────────────────────────────────────┐    │
│  │ Save to Marketing/Newsletter/Content/   │    │
│  │ Copy to Virgil Second Brain/Content/    │    │
│  │   Blog Content/                         │    │
│  │ Show in chat for review                 │    │
│  └─────────────────────────────────────────┘    │
│                                                  │
└─────────────────────────────────────────────────┘
```

## Article Template

```
# How We Built [Thing]

[2-3 sentences: what we built and why]

## Why We Built This

[Story from Step 0 interview. The problem. The frustration. Why it matters.]

## What We Built

[End result. What it does. One paragraph.]

## Step 1: [Verb] [Thing]

[What to do. Exact commands or clicks.]

[Why we did this. One sentence.]

## Step 2: [Verb] [Thing]

...

## What We'd Do Differently

[Lessons learned. Mistakes. What we'd skip next time.]

## The Stack

[Tools, APIs, services used. With links.]
```

## Quality Gates

1. Every step starts with a verb (Open, Create, Run, Paste, Click)
2. Every command is inside a code block and copy-pasteable
3. Every decision has a "Why" explanation
4. No step references something not yet introduced
5. Links are real URLs, not placeholders
6. File paths are exact
7. A 10-year-old can follow it without asking a question
8. Claude Code is always mentioned as the tool ("Open Claude Code and type...")
9. Written in Virgil's voice (first person, simple, direct)
10. No step is assumed or skipped

## Output Locations

| Location | Purpose |
|----------|---------|
| `Marketing/Newsletter/Content/how-we-built-[name].md` | Newsletter/blog source |
| `Virgil Second Brain/Content/Blog Content/how-we-built-[name].md` | Personal knowledge base |

## Dependencies

- Virgil_Voice_MASTER.md (voice file)
- The build conversation (in the current chat or a transcript)
- Claude Code as the baseline tool
