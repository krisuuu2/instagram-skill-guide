# The Instagram agent skill: how to use it, according to its own author

Everyone says Claude can now run your whole Instagram with a free pack of 13 skills. The pack is real, free and good. But its author, Jake Schincariol, wrote two things in his own README that the viral videos leave out, and both of them change how you should use it.

**The pack:** https://github.com/Jakeschincariol/instagram-agent-skill (MIT, 13 skills, made by Jake Schincariol). Everything below is quoted or summarised from that README, checked on 24 November 2026. This repo is only my notes on it; I am not the author of the pack.

## Install (from the author's README)

Paste this into Claude:

```text
https://github.com/Jakeschincariol/instagram-agent-skill

Install this skill, then confirm /ig-reel works.
```

Or in Claude Code:

```bash
git clone https://github.com/Jakeschincariol/instagram-agent-skill.git
cp -r instagram-agent-skill/skills/ig-* ~/.claude/skills/
```

Then fill in `templates/voice.md` (copy it to `~/.claude/instagram/voice.md`), because every skill reads it.

## Thing 1: it never posts anything

> "These skills do not post to Instagram." … "Nothing gets posted until you say yes. These skills write. You post."

The skills write your reel script, your caption and your replies, and you post them yourself. The author built it this way on purpose. He says the tools people use to automate posting, commenting, following or DMing are browser automation or third-party tools, and that both violate Instagram's Terms of Use and get accounts action-blocked.

So this pack is not an autopilot, and that is exactly why it is safe to use.

## Thing 2: the hook score does not pick winners

`/ig-reel` writes three hooks and gives each one a score. The author tested that score on 74 real short-form hooks (YouTube Shorts from five channels, because Instagram view counts can't be collected without logging in):

| Question | Result |
|---|---|
| Can it tell a real hook from a deliberately bad one? | Yes: AUC 0.83, and 9 of 10 bad hooks scored below the real median |
| Can it tell a creator's hits from the same creator's misses? | Barely: AUC 0.56, where 0.50 is a coin flip |

In the author's words: "kill the obviously weak hooks before you shoot them, then trust your own retention graph."

## How I would use it

1. Run `/ig-reel` and let it write several hooks.
2. Throw away every hook it marks WEAK or flags with a dealbreaker (a greeting, a preamble, nothing concrete).
3. Pick between the remaining hooks yourself. The score can't do that for you.
4. Record, post it yourself, and look at your retention graph.

One more idea from the pack that works even without Claude: when you look for content ideas, don't rank reels by views. Rank them by how many times a reel beat that account's normal reel. A small account with 400,000 views found something; a huge account with 400,000 views had a quiet day. `/ig-viral` ranks reels this way from accounts you open in your own browser.

## The 13 skills

`/ig-reel` · `/ig-viral` · `/ig-caption` · `/ig-carousel` · `/ig-story` · `/ig-profile` · `/ig-plan` · `/ig-human` · `/ig-comment` · `/ig-reply` · `/ig-dm` · `/ig-repurpose` · `/ig-audit`

---

Notes by Kris, [@aipractically](https://www.instagram.com/aipractically/). I test AI tools so you don't have to.
