# How-To Draft Article Agent

Every time we build something, we document exactly how we built it.

Not a summary. Not a changelog. A step-by-step article so detailed that someone who has never used Claude Code can follow it and get the exact same result.

This skill reads the conversation, pulls out every question we asked, every direction change, every test we ran, and turns it into an article that anyone can follow.

## Why This Exists

We build things fast. Dashboard one day. Newsletter automation the next. Landing page the day after.

A week later, someone asks "how did you build that?" and we've already forgotten half the steps.

This skill catches everything before it disappears. Every micro-step. Every wrong turn. Every fix. Written so simply that a 10-year-old could follow it.

We also use these articles as raw material for our blog. The SEO skill turns them into published posts. The LinkedIn writer pulls stories from them. But this skill creates the foundation: the detailed, honest, step-by-step draft.

## How To Use It

### The simple version

After you finish building something in Claude Code, type:

```
how to draft
```

or

```
document this build
```

or

```
write the how-to
```

Claude reads the conversation, asks you one question, and writes the article.

### What happens step by step

**1. Claude asks you one question**

"Tell me why you built this and what problem do you like to solve?"

Answer in your own words. This becomes the intro of the article.

**2. Claude reads your voice file**

It loads your writing style so the article sounds like you, not like a robot.

**3. Claude extracts every step from the conversation**

This is the big one. It goes through the entire conversation and pulls out:

- Every question you asked Claude
- Every time you changed direction ("no, not like that, do it this way")
- Every decision you made when there were options
- Every test you ran and what you found

It reads your PRODUCT.md file first to make sure nothing gets missed.

**4. Claude writes the article**

Every step becomes a stage with four parts:

- **Do this** - the exact words to type into Claude Code
- **What happens** - what Claude gives you back
- **We tested this by** - how we checked if it worked
- **Why we did this** - one sentence, why this step matters

**5. Claude runs the checker**

Before showing you the article, it checks every stage:

- Is the action clear?
- Can someone copy the prompt and paste it?
- Will they know what to expect?
- Is there a gap between stages?
- Is there jargon that needs explaining?
- Is the test real (not just "we confirmed it worked")?
- Are all prerequisites listed?

If anything fails, Claude fixes it and checks again.

**6. Claude shows you the article**

It generates an HTML preview and opens it in your browser. Clean formatting. White background. Purple headers. Easy to read.

You review it. If you want changes, say what to change. Claude updates and shows you again.

When you approve, it saves the final .md file to two locations:

1. `Marketing/Newsletter/Content/`
2. `Virgil Second Brain/Content/Blog Content/`

Done.

## What You Need

- Claude Code
- A PRODUCT.md file for whatever you built (if you don't have one, the article will note what's missing)
- A voice file at `Soul/Virgil_Voice/Virgil_Voice_MASTER.md`

## What This Does NOT Do

- Does not write the final blog post (the SEO skill does that)
- Does not create LinkedIn posts (the writer skill does that)
- Does not publish anything
- This creates the raw material. Other skills turn it into published content.

## Tips

- Run this right after you finish building. The conversation is still fresh.
- The longer and messier the build session, the better the article. Wrong turns and fixes are the most valuable parts.
- If the build happened across multiple sessions, Claude will ask which sessions to include.
- Every article starts with creating a PRODUCT.md and ends with updating it. That's how future sessions know what happened.

## Files

```
how-to-draft.skill/
  SKILL.md       - the skill instructions
  PRODUCT.md     - what this skill does and why
  PRD.md         - the original plan
  README.md      - you're reading it
```
