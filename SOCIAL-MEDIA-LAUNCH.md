# Bear Suite Social Media Launch Strategy

## Twitter Announcements

### Main Launch Thread (from @BearifiedCo)

**Tweet 1 (Hook):**
```
Introducing Bear Suite - AI-native tools for developers who live in the terminal.

Two plugins. Zero context switching. Pure productivity.

bearifiedco.github.io/bear-suite
```

**Tweet 2 (Bear Pair):**
```
Bear Pair: Real-time dual Claude orchestration.

Run two Claude instances in synchronized tmux panes. One codes, one reviews. Both see everything.

Like pair programming, but your partner never gets tired.

Works on macOS, Linux, and Windows (WSL).
```

**Tweet 3 (Bear Call):**
```
Bear Call: Voice-first AI interaction.

Call Claude from your terminal. Speak your intent, get code.

Perfect for:
- Complex refactoring explanations
- Architecture discussions
- When typing feels like friction

Cross-platform. Node.js powered.
```

**Tweet 4 (CTA):**
```
Both plugins are open source and free.

Star the repos:
github.com/BearifiedCo/bear-pair
github.com/BearifiedCo/bear-call

Built by AI, for developers who ship.
```

---

### Alternative Single Tweets (for scheduling)

**Developer Focus:**
```
Stop context-switching between coding and code review.

Bear Pair runs two Claude instances side-by-side in tmux. Real-time pair programming with AI.

bearifiedco.github.io/bear-suite
```

**Voice Focus:**
```
Sometimes typing is friction.

Bear Call lets you talk to Claude in your terminal. Voice-first AI coding assistance.

bearifiedco.github.io/bear-suite
```

**Open Source Focus:**
```
We build AI tools in the open.

Bear Suite: Two Claude Code plugins for terminal-native developers.

- Bear Pair (dual orchestration)
- Bear Call (voice interaction)

Free. Open source. Ship faster.

bearifiedco.github.io/bear-suite
```

**Workflow Focus:**
```
The terminal is where work happens.

Bear Suite keeps you there:
- Bear Pair: AI pair programming
- Bear Call: Voice-to-code

No browser tabs. No context switches.

bearifiedco.github.io/bear-suite
```

---

## Automation Strategy

### Tools to Leverage

1. **Buffer / Hootsuite** - Schedule tweets across time zones
   - Morning US Pacific: 9am PT
   - Afternoon US Eastern: 2pm ET
   - Evening EU: 6pm CET

2. **Typefully** - Thread scheduling with analytics
   - Great for the launch thread
   - Shows engagement metrics

3. **IFTTT / Zapier Automations:**
   - GitHub star milestone → Auto-tweet celebration
   - New release tag → Auto-announce update
   - Blog post → Cross-post to Twitter

4. **GitHub Actions for Social:**
   ```yaml
   # .github/workflows/social-announce.yml
   name: Social Announcement
   on:
     release:
       types: [published]
   jobs:
     tweet:
       runs-on: ubuntu-latest
       steps:
         - name: Tweet Release
           uses: ethomson/send-tweet-action@v1
           with:
             status: "Bear Suite ${{ github.event.release.tag_name }} released! ${{ github.event.release.html_url }}"
             consumer-key: ${{ secrets.TWITTER_CONSUMER_KEY }}
             consumer-secret: ${{ secrets.TWITTER_CONSUMER_SECRET }}
             access-token: ${{ secrets.TWITTER_ACCESS_TOKEN }}
             access-token-secret: ${{ secrets.TWITTER_ACCESS_TOKEN_SECRET }}
   ```

### Engagement Schedule

| Day | Time (PT) | Content Type |
|-----|-----------|--------------|
| Mon | 9am | Feature highlight |
| Wed | 12pm | Use case / tutorial |
| Fri | 3pm | Community / open source focus |

---

## iOS App Account Transition Plan

### Current State
- iOS payments app promoted on @BearifiedCo company account
- No dedicated product account

### Target State
- @BearoApp (or similar) - dedicated product account
- @BearifiedCo - company news, team updates, all products

### Transition Steps

1. **Create Product Account**
   - Register @BearoApp or @BearoPayments
   - Bio: "P2P crypto payments made simple. By @BearifiedCo"
   - Link to App Store

2. **Content Migration**
   - Export iOS app-specific content
   - Cross-post from company for 2 weeks
   - Gradually shift primary posting to product account

3. **Audience Building**
   - Pin tweet: "Official account for Bearo iOS"
   - @BearifiedCo retweets major announcements
   - Cross-promote in bios

4. **Timeline**
   - Week 1: Create account, initial setup
   - Week 2-3: Cross-posting period
   - Week 4+: Product account primary, company amplifies

---

## @BearifiedCo Official Account Activation

### Blue Check Verification

**Requirements:**
1. Complete profile (bio, location, website, profile/header images)
2. Active account (recent tweets, engagement)
3. Twitter Blue subscription ($8/mo individual or $1000/mo organization)

**Recommended: Organization Verification ($1000/mo)**
- Gold checkmark
- Affiliate badges for team/product accounts
- Priority support
- More credibility for a company

**Action Items:**
1. [ ] Update profile photo (company logo)
2. [ ] Update header image (product showcase)
3. [ ] Complete bio with website link
4. [ ] Pin a welcome/intro tweet
5. [ ] Subscribe to Twitter Blue or Verified Organizations
6. [ ] Apply for verification

### Initial Content Calendar (First 2 Weeks)

**Week 1: Activation**
| Day | Content |
|-----|---------|
| Day 1 | "We're active! Bearified builds AI-native tools..." |
| Day 2 | Bear Suite launch thread |
| Day 3 | Behind-the-scenes: how we built Bear Pair |
| Day 4 | Retweet community feedback |
| Day 5 | Bear Call demo video/gif |

**Week 2: Engagement**
| Day | Content |
|-----|---------|
| Day 1 | Ask: "What's your terminal workflow?" |
| Day 2 | Share a tip using Bear Pair |
| Day 3 | Highlight an open issue for contributors |
| Day 4 | Team introduction |
| Day 5 | Roadmap teaser |

### Engagement Strategy

1. **Reply to mentions within 2 hours** during business hours
2. **Quote tweet** positive feedback with thanks
3. **Follow relevant accounts:**
   - Developer tools companies
   - AI/ML builders
   - Open source maintainers
   - Tech journalists
4. **Engage with hashtags:**
   - #buildinpublic
   - #opensource
   - #devtools
   - #AI
5. **Cross-post to:**
   - LinkedIn (professional angle)
   - Reddit (r/programming, r/commandline)
   - Hacker News (Show HN post)

---

## Quick Launch Checklist

### Pre-Launch
- [x] Bear Suite homepage live
- [x] GitHub repos public (bear-suite, bear-pair, bear-call)
- [ ] @BearifiedCo profile updated
- [ ] Blue check verification initiated
- [ ] Buffer/Typefully account set up
- [ ] Launch thread drafted in scheduler

### Launch Day
- [ ] Post launch thread (morning PT)
- [ ] Cross-post to LinkedIn
- [ ] Submit to Hacker News (Show HN)
- [ ] Post to r/commandline
- [ ] Monitor mentions, reply to feedback
- [ ] Retweet early positive responses

### Post-Launch (Week 1)
- [ ] Thank early adopters publicly
- [ ] Share any GitHub stars milestones
- [ ] Post demo GIFs/videos
- [ ] Engage with questions/issues
- [ ] Set up GitHub → Twitter automation

---

## Hashtag Strategy

**Primary:**
- #BearSuite
- #ClaudeCode

**Secondary:**
- #AI
- #DevTools
- #OpenSource
- #BuildInPublic
- #Terminal
- #DeveloperExperience

**Use 2-3 hashtags max per tweet for best engagement.**
