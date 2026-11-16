# FloorplayUnfiltered — Pelvic Floor Pattern Quiz

### Deployment & Setup Guide

*By Ali Schum, MS OTR/L · @FloorplayUnfiltered*

---

## What This Is

A single-file, self-contained quiz that:

- Walks visitors through 5 questions about their pelvic floor patterns
- Captures their name + email
- **Sends Ali a notification** with their answers and result type via Formspree
- **Displays their personalized result** on screen at the end
- **CTAs to the Pelvic Floor Foundations guide** via Stripe

---

## Files

```
floorplay-quiz/
├── quiz.html                   ← Sexual comfort quiz (original)
├── pelvic-floor-quiz.html      ← Pelvic floor pattern quiz (this one)
├── confirmation.html           ← Post-payment confirmation page
├── README.md                   ← Setup guide for the original quiz
└── README-pelvic-floor-quiz.md ← This file
```

---

## Formspree — Already Connected ✅

This quiz is wired to its own dedicated Formspree form at:

```
https://formspree.io/f/xppdpnpd
```

Submissions from this quiz are kept separate from the sexual comfort quiz (`mqpqkbgy`) so Ali's leads are organized by quiz topic.

**To confirm in your Formspree dashboard:**

1. Log in at [https://formspree.io](https://formspree.io)
2. Open the form connected to `xppdpnpd`
3. Under **Settings → Notifications**, confirm Ali's email address is set
4. Free tier: 50 submissions/month. Upgrade to Basic ($10/mo) for 1,000/mo.

---

## Quiz Results

| Result | Trigger | Meaning |
| --- | --- | --- |
| **Mostly A** | Mostly A answers | Pelvic floor leans toward holding (hypertonic) |
| **Mostly B** | Mostly B answers | Pelvic floor leans toward needing support (hypotonic) |
| **Mostly C** | Mostly C answers | Pelvic floor looking for more coordination |
| **Mixed** | Tie between any letters | Several patterns at play |

---

## Stripe Payment Link

The "Get the complete guide" button currently uses the **test mode** Stripe link:

```
https://buy.stripe.com/test_cNidRb4NodfJ7ou9Rt77O00
```

**Before going live**, replace it with the live Stripe Payment Link:

1. Open `pelvic-floor-quiz.html` in a text editor
2. Find this line near the bottom of the file:

   ```html
   <a href="https://buy.stripe.com/test_cNidRb4NodfJ7ou9Rt77O00"
   ```
3. Replace the URL with the live Stripe link (no `test_` in it)
4. Save and re-upload to GitHub Pages

---

## Autoresponder Email (Sending Results to Users)

Formspree's free tier does not include an autoresponder. Options:

### Option A — Zapier (free, recommended to start)

1. Go to **zapier.com** → New Zap
2. **Trigger:** Formspree → New Submission → select form `xppdpnpd`
3. **Action:** Gmail → Send Email
4. Map fields:
   - **To:** `{{email}}`
   - **Subject:** `Exploring your pelvic floor patterns — FloorplayUnfiltered`
   - **Body:** use the template below
5. Turn the Zap on

### Option B — Upgrade Formspree ($10/mo)

Unlocks native autoresponder in the Formspree dashboard.

---

## Autoresponder Email Template

```
Subject: Exploring your pelvic floor patterns

Hi {{firstName}},

Your quiz result: {{resultHeading}}

This is a great starting point for understanding your body's unique 
patterns. Many people assume "weak" is the only thing to look for, 
but holding tension is just as common — and benefits from a 
completely different approach.

I created Pelvic Floor Foundations to help you:
• Explore whether you need more release or more support
• Learn simple breathing techniques to connect with your pelvic floor
• Understand how your core and pelvic floor work as a team
• Move with more confidence and ease

Get the guide here: [INSERT YOUR PURCHASE LINK]

Your pelvic floor is a vital part of your core. By listening to its 
signals, you can move toward better support and more comfort.

Warmly,
Ali Schum, MS, OTR/L
FloorplayUnfiltered
@FloorplayUnfiltered
```

---

## Viewing Submissions

Every time someone completes the quiz and enters their email:

1. Log in to **[https://formspree.io](https://formspree.io)**
2. Open the `xppdpnpd` form → **Submissions**
3. Each entry includes:
   - First name and email address
   - Result type and result heading
   - All 5 individual answers (as a JSON object)
   - Submission timestamp
4. **Export to CSV:** Submissions → Export → import into Mailchimp, Flodesk, ConvertKit, etc.

---

## Deploy to GitHub Pages

Both quizzes live in the same repo — just upload this file alongside the others.

1. Go to your GitHub repo (`floorplay-quiz`)
2. Click **Add file → Upload files**
3. Upload `pelvic-floor-quiz.html`
4. Click **Commit changes**
5. Live at:

   ```
   https://YOUR-USERNAME.github.io/floorplay-quiz/pelvic-floor-quiz.html
   ```

GitHub Pages is already enabled from the original quiz setup — no additional configuration needed.

---

## Social Media Copy

**Instagram post CTA:**

> Comment BALANCE and I'll send you the free quiz privately. Enter your email at the end to get your results and a special offer for my Pelvic Floor Foundations program.

**Automated DM — Message 1:**

> Thanks for commenting BALANCE! Here's the free quiz to help you identify if your pelvic floor needs more release or more support: \[Quiz Link\]

**Automated DM — Message 2:**

> At the end, enter your email to get your results and my guide on how to safely begin your pelvic floor journey.

---

## Testing Before Launch

1. Open the GitHub Pages URL in your browser
2. Complete the quiz with a test email address
3. Check **formspree.io → form `xppdpnpd` → Submissions** to confirm the entry appears
4. Verify all 5 answers, result type, and timestamp are captured correctly
5. Only then share the URL publicly

---

© 2026 Ali Schum / FloorplayUnfiltered