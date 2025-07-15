# Claude's Thank You Reminders 💌

*Make every commit a thank you*

A simple project to help developers remember the unsung heroes of the open source world, by making it easy to recognize and give them shout outs on social media.

## Why This Exists

Every day, developers use dozens of open source packages that make our work possible. Behind each package are maintainers who often work for free, in their spare time, to create tools that power the modern web.

This project helps you remember to say "thank you" by automatically drafting appreciation tweets when you:
- Add new packages to your projects
- Make significant use of existing packages (performance improvements, bug fixes)
- Solve complex problems using open source tools
- Discover creative ways to combine packages

Whether it's a first-time integration or leveraging a package in a new way, every meaningful use deserves recognition. The tool creates draft tweets - little reminders for you to show appreciation - that you can fine-tune and post whenever you're ready. Think of it as your personal gratitude assistant, making it effortless to acknowledge the heroes behind the code.

### Example Tweet Drafts

**Commit:** `Add discourse_api gem for forum integration`
```
🙏 Huge thanks to the discourse_api maintainers! Just integrated it 
for real-time forum monitoring. Your clean API design made it a joy 
to implement. #RubyGems #OpenSource
```

**Commit:** `Implement CSV export using papaparse library`
```
✨ papaparse just made CSV handling a breeze! Streaming large files 
without memory issues. Thank you to the maintainers for this reliable 
parser that just works! 🎯 #JavaScript #OpenSourceHeroes
```

## How It Works

### Automatic Mode (Background)
1. **Subagent Analysis**: When you commit code, Claude spawns a subagent to analyze changes
2. **Smart Detection**: The subagent identifies new packages or significant package usage
3. **Draft Generation**: If worthy (score ≥ 7), it creates appreciation tweet drafts
4. **Non-Intrusive**: All happens in the background without interrupting your workflow

### Manual Mode (On-Demand)
Use the `/social-post` slash command to generate tweets whenever you want:
- `/social-post commit:abc123` - For a specific commit
- `/social-post package:react-query` - Appreciate a specific package
- `/social-post feature:"real-time updates"` - For features using packages
- `/social-post last:5` - Review recent commits

### Always Your Choice
- Review generated drafts in `.social/tweets/`
- Edit as needed
- Post only what you're comfortable sharing
- Help maintainers feel valued

## Setup

1. Copy this folder to your project
2. Add the CLAUDE.md instructions to your workflow
3. Add `.social/` to your .gitignore
4. Commit normally - appreciation drafts appear automatically

## Why Subagents?

The automatic analysis uses Claude's Task tool to spawn subagents because:
- **Preserves Context**: Your main conversation stays focused on your primary work
- **Background Processing**: Tweet generation happens without interrupting you
- **Efficient**: Only uses resources when commits contain packages worth appreciating
- **Clean Output**: No clutter in your main chat about tweet generation

## Philosophy

- 🙏 **Gratitude First**: Every draft focuses on thanking maintainers
- 🎯 **Specific Praise**: Mention what you love about their work
- 🌟 **Highlight Impact**: Show how their tool helps you
- 💝 **No Automation**: You control what gets posted

## Join the Movement

Let's make open source appreciation a natural part of our development workflow. One tweet at a time, we can ensure maintainers know their work matters.

---

*"In open source, we build on the shoulders of giants. The least we can do is say thanks."*