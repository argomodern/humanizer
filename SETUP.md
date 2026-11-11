# Setup

Version 1, 2026-11-11. About 30 minutes, once. After that it runs on its own and learns from you every Friday.

What you get: the humanizer from Argo Operator. It rewrites anything Claude drafts for you so it sounds like you and not like AI, and every week it learns from what you actually sent. Your rules live in your own file, on your own computer.

What you need: the Claude desktop app with Claude Code, on a Pro or Max plan.

---

## 1. Connect your email to Claude

In the Claude app: Settings, then Connectors. Connect Gmail (or Outlook) and your calendar. You sign in once. Claude can then read your sent mail, which is how it learns your voice. Nothing ever sends without you.

## 2. Install the humanizer

Open Terminal and paste:

```
git clone https://github.com/argomodern/humanizer ~/.claude/skills/humanizer
```

## 3. Fill out the voice form

Answer in plain words. Short answers are fine. Skip what you don't know, the weekly review fills it in.

1. Who do you write to most? (clients, coworkers, friends, recruiters...) Does your tone change between them? How?
2. How do you open an email? ("Hey Sam,", "Hi Sam,", straight to the point...)
3. How do you sign off? Paste your email signature exactly.
4. Words or phrases you use a lot.
5. Words or phrases you'd never use.
6. Exclamation marks: never, sometimes, often?
7. Dashes (—): do you use them?
8. Emoji or ":)" in emails: never, with some people, always?
9. Short and blunt, or warm and chatty?
10. Anything AI writing does that annoys you?
11. Paste 3 real emails or messages you sent that sound most like you.

## 4. Turn the form into your voice guide

Open Claude Code, paste your answers from step 3, then paste this underneath:

```
Above are my voice form answers. Please:
1. Create ~/.claude/my-voice.md from them. Use these sections: Which voice, when (a table of who I write to, how I open, how I end); Every voice (rules for everything I write); Mechanics (greeting, sign-off, signature, dashes, exclamation marks, length); Rules learned from my edits (empty for now); Rejected (empty); Changelog (today's date, "created from my voice form").
2. Edit ~/.claude/skills/humanizer/SKILL.md so it uses my guide, not Maria's: rename the section "Maria's voice guide" to "My voice guide", point every mention of VOICE-GUIDE.md to ~/.claude/my-voice.md and voice-guide-proposals.md to ~/.claude/my-voice-proposals.md, change "Maria" to "me", and remove the mention of the Friday edit-learning job and Todoist.
Show me both changes before you save them.
```

## 5. Make it run on its own

Still in Claude Code, paste:

```
Add this line to ~/.claude/CLAUDE.md (create the file if it's missing): "Anything you draft for me to send or publish (emails, posts, messages) goes through the humanizer skill before you show it to me."
```

From now on you never have to ask for it.

## 6. The weekly review (how it learns you)

Every Friday Claude compares what it drafted for you with what you actually sent, and suggests up to 5 new rules, each with your own words as proof. You reply like "1 yes, 2 no". Yeses go into your voice guide, noes go to the Rejected list so it never suggests them again. Nothing changes without your yes.

To set it up, in the Claude desktop app make a scheduled task (the "Scheduled" section of Claude Code) that runs every Friday at 9am with this prompt:

```
Run my weekly voice review. Read the emails I sent this week (from my connected email) and any drafts you wrote for me. Compare them and suggest up to 5 new rules for ~/.claude/my-voice.md, numbered, each with my exact words as evidence. Also show anything open in ~/.claude/my-voice-proposals.md. Change nothing until I answer. Then add my yeses to "Rules learned from my edits" with a dated Changelog line, and my noes to "Rejected".
```

It runs when your laptop is open. If you miss a Friday, just type "run my weekly voice review" any time.

---

Want more? The full Argo Operator package adds a morning to-do sweep, meeting follow-ups and "where did we leave off" before every call. See argomodern.com.
