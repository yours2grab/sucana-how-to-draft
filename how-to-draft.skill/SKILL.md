---
name: how-to-draft.skill
description: "After every build session, document exactly how we built it into a step-by-step article. Every micro-step. A 10-year-old can follow it."
---

# How-To Draft Article Agent

Trigger: "how to draft" or "document this build" or "write the how-to"

## What This Does

Reads the current conversation, extracts every step taken during a build session, and writes a comprehensive how-to article. The article is so detailed that someone with zero context can follow it and get the exact same result.

## STEP 0 — CONTEXT INTERVIEW

Before doing anything, ask one question and wait for the answer:

"Tell me why you built this and what problem do you like to solve?"

That's it. One question. Wait for the answer. This becomes the intro and the "why" throughout the article. Do NOT skip this step. Do NOT make up the answer.

## STEP 1 — LOAD VOICE

Read in full: `Soul/Virgil_Voice/Virgil_Voice_MASTER.md`

Internalize:
- First person always
- Simple words (7-year-old test)
- Short sentences
- No jargon without explanation
- Compression over explanation
- Real names (Victor, Vinod) with roles

## STEP 2 — EXTRACT THE CONVERSATION (THE MOST IMPORTANT STEP)

This is the core of the entire skill. Everything else is easy. This step makes or breaks the article.

### Where to look for the steps

Always read the PRODUCT.md file first. That is the source of truth. It has every feature, every decision, every file created. The README is marketing copy. The conversation history shows the journey. But the PRODUCT.md tells you what was actually built.

If a feature exists in the PRODUCT.md but you didn't find it in the conversation, it still needs a stage in the how-to. Ask the user: "The PRODUCT.md mentions [feature]. Can you tell me how you built that?"

### The principle

The reader will open Claude Code and have the same conversation. Your job is to give them the exact words to say to Claude to get the same result. That's it.

You are NOT documenting what Claude did in the background. You are documenting what the USER SAID to Claude and what CAME BACK. Like a recipe. You don't explain how the oven works. You say "put it in the oven at 180 for 20 minutes."

### How each stage looks in the article

Every stage follows this EXACT format (same as the article template in Step 3):

```
### Stage X: [Short description]

**Do this:**
1. Open Claude Code (or "In Claude Code, type:")
2. Type: "[exact prompt]"

**What happens:**
[One or two sentences. What Claude gives back. Not test results.]

**We tested this by:**
[What you checked. What you found. If it failed, what you told Claude to fix.]

**Why we did this:**
[One sentence.]
```

If the user changed direction:

```
### Stage X: [Short description]

**Do this:**
1. In Claude Code, type: "[first instruction]"

**What happens:**
[Result]

**Then we said:**
"[The correction or new direction]"

**What happened instead:**
[The better result]

**We tested this by:**
[Test details]

**Why we did this:**
[One sentence.]
```

### What to extract from the conversation

**Multi-session builds:** If the build happened across multiple sessions, ask the user: "Did this build happen in one session or multiple?" If multiple, ask which sessions to document. If you only have the current session, document what's here and note "The initial build happened in a prior session" where relevant. Never guess what happened in a session you can't see.

Read the FULL conversation from beginning to end. Go message by message. Pull out:

**1. Every question or instruction the user gave to Claude.**
These are the steps. Write them as natural speech. "I want to build a dashboard that shows my newsletter metrics." Not "The user requested a dashboard implementation."

The reader copies these prompts into Claude Code. Same words, same result.

**2. Every direction change.**
"No, not like that. Make it simpler." These are the most valuable moments. They show what didn't work and what replaced it. Include both the first attempt and the correction.

**3. Every decision the user made.**
When there were options, show what was picked and why in one sentence.

**4. Every test and its result.**
"I tested it and the action items were pulling priorities as tasks. So I told Claude to add a filter." Show the problem and the fix.

### What NOT to do

- Do NOT explain what Claude did behind the scenes (API calls, file reads, code logic)
- Do NOT write technical descriptions of the build process
- Do NOT use developer language ("parsed the response", "iterated over subscribers")
- Do NOT list commands unless the user actually typed commands
- Do NOT skip the messy parts. Wrong directions and corrections are the most useful stages.
- Do NOT summarize. If the user asked 12 questions to build something, document all 12 questions.

### Explain the key files

Every build creates files that the reader might not understand. When one of these files appears in the how-to for the first time, add a short explanation of what it is and why it matters. One or two sentences max. Then move on.

Files that always need explaining:

**.env file** — "This file stores your passwords and API keys. It stays on your computer and never gets shared. Every time the script runs, it reads this file so you don't have to paste your keys again."

**PRODUCT.md file** — "This is your project's memory. It documents what you built, what decisions you made, and where everything lives. When you come back to this project in three weeks and forgot what you did, this file tells you everything. We create one for every build."

**SKILL.md file** — "This is the instruction file that tells Claude what to do. Think of it as a recipe card. Claude reads it and follows the steps."

**PRD.md file** — "This is the plan. What we're building, why, and in what order. We write this before building so we know where we're going."

**GitHub repo** — "GitHub is where we store the finished skill so anyone can download it. Think of it as a public folder on the internet. We push the files there so they're always available and backed up."

**API** — "An API is how two tools talk to each other. When we say 'Beehiiv API,' it means Claude can look up subscribers and add tags without you logging into Beehiiv yourself."

**Next.js** — "Next.js is the tool that builds the website. Think of it as the engine behind the page. You don't need to understand it to follow the steps."

**Vercel** — "Vercel is the service that puts the website on the internet. When Claude pushes a file, Vercel sees the change and updates the website automatically. You don't need a Vercel account to follow along."

**MCP** — "MCP is how Claude connects to external tools like Fireflies or Beehiiv. Think of it as plugging in a cable between Claude and another app."

**CTA** — "CTA means Call to Action. It's the line that tells people what to do next, like 'Email us' or 'Download this.'"

**Funnel** — "A funnel shows how people move through stages. From subscriber to downloading the gift to starting a trial. Each stage has fewer people than the one before."

**Guardrails** — "Guardrails are writing rules. A list of banned words and patterns that make content sound like AI wrote it instead of a human."

**API route** — "An API route is a small piece of code on the website that runs when someone clicks a button. It does something in the background, like tagging a subscriber in Beehiiv."

**CSV** — "A CSV is a spreadsheet file. When you export data from a tool like Meta Ads Manager, it downloads as a CSV. You don't need to open it. Just drag it into the chat."

Only explain each file/concept the FIRST time it appears. Don't repeat the explanation in later stages.

**IMPORTANT:** This list will grow over time. Every time the checker flags a term a 10-year-old wouldn't understand, add the explanation here permanently so future articles don't repeat the same mistake.

### Two mandatory stages in every how-to

No matter what we built, these two stages ALWAYS appear:

**Early in the build (after the first working piece):** A stage where we create the PRODUCT.md file. Frame it as: "Before we keep building, we save what we have so far."

**The very last stage (always):** A stage where we update the PRODUCT.md with everything we built, every decision we made, and the current status. Frame it as: "Now when we come back to this project in a week or a month, we open this file and know exactly where we left off and how everything works."

These are not optional. Every how-to includes both.

### The test

After extracting, read each stage and ask: "If someone copies the prompt from 'Do this: Type:' into Claude Code, will they get the same result?" If yes, the stage is good. If no, add more detail to the prompt.

## STEP 3 — STRUCTURE AND WRITE THE ARTICLE

**CRITICAL:** Use the FULL output from Step 2. Every stage. Every test result. Every direction change. Do not shorten. Do not skip. Do not summarize with "..." or "continues above." The article must contain every single stage written out in full. If Step 2 produced 10 stages, the article has 10 stages. No exceptions.

### READ THESE RULES FIRST (before writing anything)

1. **Claude Code is always the tool.** Say "Open Claude Code" or "In Claude Code, type..." Every time.

2. **Prompts are copy-pasteable.** The reader copies the exact text from "Type:" and pastes it into Claude Code. Same words, same result.

3. **"What happens" is ONLY what Claude gives back.** Max 2 sentences. Test results go in "We tested this by." Not here.

4. **"We tested this by" must be specific.** "We confirmed it worked" is NOT a test. Show what you checked and what you found. "We checked the file and found 6 new passages, 2 duplicates were correctly skipped." That's a test.

5. **"Why we did this" is always ONE sentence.** If it takes two, compress.

6. **Show direction changes.** "We first tried X. It didn't work because Y. So we typed Z instead." Failed attempts are as valuable as working ones.

7. **No assumed knowledge.** First time a technical concept appears, use the explanations from the mandatory jargon list in Step 2. If the term isn't in the list, explain it in one sentence and add it to the list for future articles.

8. **Links are real.** Every URL must be real and working. No placeholders.

9. **Testing is mandatory.** Every stage that produces output gets tested before moving on. Build, test, find problem, fix, test again, move on.

### Now write using this structure

```
# How We Built [Thing]

[2-3 sentences: what we built and why. From Step 0 answers.]

## Why We Built This

[The story. The problem. The frustration. From Step 0 interview. This is the human part.]

## What We Built

[End result. What it does. What the user sees. One paragraph max.]

## Before You Start

[List everything the reader needs before Stage 1. Accounts, tools, access. Keep it short.]

## The Steps

### Stage 1: [Short description]

**Do this:**
1. Open Claude Code
2. Type: "[exact prompt to give Claude]"

**What happens:**
[What Claude gives you back. Max 2 sentences. ONLY the result. No test results here.]

**We tested this by:**
[What you specifically checked. What you found. If something failed, what you told Claude to fix. Not "we confirmed it worked" — that's not a test. Show what you looked for and what you found.]

**Why we did this:**
[One sentence. Not two. Why this stage matters.]

### Stage 2: [Short description]

[Continue for every stage. Same format. Build → Test → Fix → Move on.]

### Last stage: [always] Update the PRODUCT.md

[Update the project file with everything built, all decisions, all status.]

**Why we did this:**
When you come back to this project, this file tells you everything.

## What We'd Do Differently

[Lessons learned. Mistakes made. What to skip or do first next time.]

## The Stack

[Every tool, API, service used. With links where possible.]

## Files

[Every file created. With paths.]
```


## STEP 4 — CHECKER (RUN THIS BEFORE SHOWING)

Go through the entire article stage by stage. For each stage, run these 7 checks:

| # | Check | Question | If FAIL |
|---|-------|----------|---------|
| 1 | Action clear | Does "Do this" tell me exactly what to click, type, or open? | Add the missing action |
| 2 | Prompt copyable | Can I copy the prompt text and paste it into Claude Code? | Rewrite as exact text |
| 3 | Result verifiable | Does "What happens" tell me what I should see? | Add what the reader should expect |
| 4 | No gap | Is there a jump between this stage and the next where I'd be lost? | Add the missing bridge stage |
| 5 | No jargon | Is there a word a 10-year-old wouldn't understand? | Explain it in one sentence |
| 6 | Tested | Does "We tested this by" show a real test with a real result? | Add the test |
| 7 | Prerequisites | Does "Before You Start" list every account, tool, and file needed before Stage 1? | Add the missing prerequisite |

**Show the checker results in chat before showing the article:**

```
CHECKER RESULTS:
Stage 1: ✅ ✅ ✅ ✅ ✅ ✅ ✅
Stage 2: ✅ ✅ ✅ ❌ ✅ ✅ ✅ — Gap between Stage 2 and 3 — adding bridge
Stage 3: ✅ ✅ ✅ ✅ ❌ ✅ ✅ — "API" not explained — adding explanation
...
```

Fix all failures. Run the checker again. Only proceed to Step 5 when all stages pass all 7 checks.

**PRODUCT.md cross-check (MANDATORY):**
Before running the 7 checks, do TWO comparisons:

**Check 1: PRODUCT.md → Article.** Compare every feature in the PRODUCT.md against stages in the article. If something exists in the PRODUCT.md but has no stage, ADD IT immediately.

**Check 2: Article → PRODUCT.md.** Compare every stage in the article against the PRODUCT.md. If you built something that's NOT in the PRODUCT.md, flag it: "PRODUCT.md is missing: [feature]. Will be added in the final update stage."

Never leave gaps in either direction. Never produce steps from the README. The PRODUCT.md is the source of truth, but it must also be kept up to date.

**The ultimate test:** If a stranger who has never used Claude Code reads this article, can they follow every step from beginning to end and get the same result without asking a single question? If yes, it passes. If no, find the gap and fix it.

## STEP 5 — GENERATE HTML PREVIEW AND SAVE

### A) Generate formatted HTML

Generate the article as a clean HTML file with these formatting rules:

- White background, clean typography (system fonts)
- 2-3 sentence blocks with blank lines between them. Never blobs.
- Bold labels on their own line, description on next line
- Numbered lists with spacing between items
- Punch lines stand alone
- No dashes anywhere
- Max width 720px, centered, generous padding
- Stage headers in purple (#9333EA)
- "Do this" steps in a light gray box
- "We tested this by" in a subtle bordered section
- "Why we did this" in italic

Save to: `Marketing/Newsletter/Content/how-we-built-[short-name].html`

Open in browser automatically.

### B) Ask for review

Show in chat: "Article preview opened in your browser. Review it."

Then ask: "Should I save the final .md version or do you want changes?"

**Wait for explicit approval.** Do NOT save the .md until the user says to save.

If changes requested → make them → regenerate HTML → open again → ask again.

### C) Save after approval

Save the .md version to both locations. Use the SAME root as the current working directory for both paths:

1. `{ROOT}/Marketing/Newsletter/Content/how-we-built-[short-name].md`
2. `{ROOT}/Virgil Second Brain/Content/Blog Content/how-we-built-[short-name].md`

Where `{ROOT}` is the current project root (e.g. `/Users/virgilbrewster/My Drive/Sucana Test Drive Sandbox/`).

**IMPORTANT:** Also copy to the real Obsidian vault if it's at a different path: `/Users/virgilbrewster/My Drive/Virgil Second Brain/Content/Blog Content/`. Always verify both locations exist. If a folder doesn't exist, create it.

Show in chat:
- "HOW-TO SAVED"
- File 1: [path]
- File 2: [path]
- HTML preview: [path]
- Stages documented: X
- Word count: Y
- Checker: all checks passed

## WHAT THIS DOES NOT DO

- Does not write the final blog post (that's the SEO skill)
- Does not create LinkedIn posts (that's the writer skill)
- Does not publish anything
- This is the raw material. The detailed draft. Other skills turn it into published content.

END.
