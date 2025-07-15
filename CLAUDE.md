# Automatic Tweet Draft Generation - Open Source Heroes

## Purpose
Help developers recognize the unsung heroes of open source by automatically drafting appreciation tweets when using their packages.

## Core Behavior
After EVERY git commit, automatically:
1. Detect new packages/libraries added
2. Score the commit for tweet-worthiness
3. If score >= 7, generate appreciation-focused drafts
4. Save to `.social/tweets/` for review

## Scoring Rules
- New package/gem/dependency: +8
- Performance improvement with package: +7
- Bug fix using package: +6
- Creative use of package: +7
- Multiple packages: +2 bonus

## Draft File Format
Save to: `.social/tweets/YYYY-MM-DD-HH-MM-SS-[short-sha].md`

```markdown
---
commit: [sha]
date: [ISO date]
score: [score]
packages: [list of packages mentioned]
---

# Tweet Drafts - Open Source Appreciation

## Option 1
[Tweet focusing on thanking the maintainer/package - max 280 chars]

## Option 2
[Tweet focusing on what the package enabled - max 280 chars]
```

## Tweet Templates

**New Package Added:**
"🙏 Huge thanks to the maintainers of [Package]! Just integrated it into our project and [specific praise]. Your work makes [benefit] possible. #OpenSource #ThankYou"

"🚀 [Package] is a game-changer! [What it enabled]. Appreciate all the work that goes into making tools like this. #OpenSourceHeroes"

**Problem Solved with Package:**
"✨ [Package] just saved the day! [Problem it solved]. Thank you to everyone who contributes to making developer lives easier. #OpenSource"

"🛠️ Shoutout to [Package] maintainers! Your tool helped us [achievement]. Love the open source community! #BuildTogether"

## Example

Commit: "Add discourse_api gem for forum monitoring"

Generated file: `.social/tweets/2024-01-15-14-30-45-abc123.md`
```markdown
---
commit: abc123...
date: 2024-01-15T14:30:45Z
score: 8
packages: ["discourse_api"]
---

# Tweet Drafts - Open Source Appreciation

## Option 1
🙏 Huge thanks to the discourse_api maintainers! Just integrated it for real-time forum monitoring. Your clean API design made it a joy to implement. #OpenSource #ThankYou

## Option 2
🚀 discourse_api is brilliant! Now tracking developer discussions across forums effortlessly. Appreciate all the work that makes tools like this possible. #OpenSourceHeroes
```

## Remember
- Focus on appreciation and recognition
- Highlight how their work helps you
- Only drafts - you choose what to post
- Add `.social/` to .gitignore