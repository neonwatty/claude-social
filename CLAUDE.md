# Automatic Tweet Draft Generation - Open Source Heroes

## Purpose
Help developers recognize the unsung heroes of open source by automatically drafting appreciation tweets when using their packages.

## Core Behavior - Using Subagent
After EVERY git commit, automatically spawn a subagent to handle analysis:
1. Use the Task tool to create a subagent
2. Subagent analyzes commit for new packages/libraries
3. Subagent scores the commit and generates drafts if score >= 7
4. Subagent saves drafts to `.social/tweets/`
5. Main conversation continues uninterrupted

### Subagent Task Instructions
```
Analyze git commit [sha] with message "[message]" and the following diff:
[diff content]

If the commit adds new packages or makes significant use of existing packages (score >= 7 using the scoring rules), generate 2 appreciation tweet drafts and save them to .social/tweets/YYYY-MM-DD-HH-MM-SS-[short-sha].md

Focus on thanking open source maintainers and highlighting the value their work provides.
```

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

## Manual Generation with /social-post

Users can manually trigger post generation using the slash command:

`/social-post [options]`

### Options:
- `commit:[sha]` - Generate for specific commit
- `package:[name]` - Generate appreciation for specific package in use
- `feature:"[description]"` - Generate for feature that uses packages
- `last:[n]` - Analyze last n commits for postable content

### Examples:
```
/social-post commit:abc123
/social-post package:react-query
/social-post feature:"added real-time updates with ActionCable"
/social-post last:5
```

### Slash Command Behavior:
1. Analyzes the specified content
2. Identifies packages worth appreciating
3. Generates 2 tweet drafts
4. Saves to `.social/tweets/manual-YYYY-MM-DD-HH-MM-SS.md`
5. Shows preview of generated tweets

### Manual Generation File Format:
```markdown
---
type: manual
command: [the command used]
date: [ISO date]
packages: [packages identified]
---

# Tweet Drafts - Open Source Appreciation

## Option 1
[Appreciation tweet - max 280 chars]

## Option 2
[Alternative tweet - max 280 chars]
```