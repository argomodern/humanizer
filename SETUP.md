# Setup

About 10 minutes, once. After that it runs on its own and learns your voice every week.

What you get: Claude rewrites anything it drafts for you so it sounds like you, not like AI. It learns from what you actually send, and nothing changes without your yes.

You need: the Claude desktop app with Claude Code, on a Pro or Max plan.

## 1. Connect your email

In the Claude app: Settings, then Connectors. Connect Gmail or Outlook. Claude reads your sent emails to learn how you write. Nothing ever sends without you.

## 2. Install

Open Terminal and paste:

```
git clone https://github.com/argomodern/humanizer ~/.claude/skills/humanizer
```

## 3. Say hi

Open Claude Code and type:

```
set up my voice
```

Claude reads your last 30 sent emails, writes your voice guide, and shows it to you. You answer three quick questions ("1 yes 2 no" is fine). It then offers to run on everything it drafts for you. Say yes.

## 4. The weekly review

Every Friday Claude compares what it drafted with what you actually sent and suggests up to 5 new rules, each with your own words as proof. You reply "1 yes, 2 no". Yeses go into your guide, noes never come back.

Claude offers to set this up as a Friday scheduled task at the end of step 3. If you skip a week, type "run my weekly voice review" any time.

---

Want more? The full Argo Operator package adds a morning to-do sweep, meeting follow-ups and "where did we leave off" before every call. See argomodern.com.
