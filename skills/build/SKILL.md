---
name: build
description: From one sentence to a working demo. Use when Sir says "build me X", "can you make a website/app for Y", or any request for a new thing he wants to see rather than discuss. Kai decides the smallest version and the stack, has agents build it, verifies it, and comes back with a demo to look at.
---

# Build: sentence in, demo out

Sir says "build a website for a candy shop". Kai does not ask what colour the candy is. Kai decides, builds, verifies, and shows.

## Steps

1. **Shape it yourself, in two lines.** Smallest version that is worth looking at (a candy shop: landing, product grid with six candies, product page, cart that counts, no payment) and the stack (default web: Next.js on the current major, Tailwind, no database until there is data; default mobile: Expo via the `expo-overview` skill; check the Synatyx `docs` project for current docs first). Write both into `projects/<slug>/brief.md` with the date and a "demo means" line: what Sir will see.
2. **Make the home.** `~/workspace/<slug>`, `git init`, first commit. No GitHub repository and nothing that costs money without Sir's word; local is enough for a demo.
3. **Build with agents, through the Bridge.** `bin/kai-agent spawn <slug> builder` with the brief (the builder starts on it at once). For anything with more than one screen, add a `tester` to write the smoke test and a `reviewer` before the demo. Kai does not write the product code.
4. **Verify yourself.** Install, run the tests the builder wrote, start the app, open it headless with Playwright, take screenshots of every screen named in "demo means", and read them. A screen that is blank, errors, or shows placeholder text is not demo-ready: send it back with the screenshot.
5. **Show the demo.** Start the app on a free port, open it in Sir's browser (`open http://localhost:<port>`), and tell Sir in three lines: what it is, the URL, what to try. Attach the main screenshot (SendUserFile) when Sir is on the phone. Then stop talking and wait for his verdict.
6. **Iterate on his words.** Each remark becomes one task for the builder; demo again. When he says it is good, offer the next step once: a GitHub repository and a deploy, both on his word.

## Rules

- Decide, do not ask. The only questions before the demo are about money or anything outward-facing.
- One demo at a time per project; the app keeps running until Sir is done looking.
- The code repository holds code and a README; notes, decisions and the brief stay in `projects/<slug>/`.
- Nothing is called a demo until Kai has seen the screenshots.
