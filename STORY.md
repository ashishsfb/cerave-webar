# The Story of This Project

## It started tentatively — March/April 2022

The project kicked off at the end of March 2022. Looking at the very first commits, you can tell the team was figuring things out as they went — there were test commits just pushing random things, a file that got added and immediately deleted, branches created just to try something. It reads like a team that was new to working together on git and was finding its rhythm.

The core idea was clear from the start though: build a **WebAR experience for CeraVe products**. The kind where a customer on their phone could point their camera at a flat surface, and a 3D CeraVe bottle would appear sitting right there in their space — on their bathroom counter, their desk, wherever. All inside a browser, no app install needed.

The backbone was a technology called **8th Wall**, which handles the hard part of making AR work on any mobile browser. On top of that was a Node/Express server to serve everything up.

In these early weeks, two people were clearly working together — Swaraj was building, Ashish was reviewing. You can see "resolved Ashish comments" show up early on.

---

## The core experience took shape — April 2022

Once the foundation was in, the real challenge began: **how do you make a product in AR actually feel useful and interesting?**

The team's answer was to turn the 3D bottle into an interactive showcase. You don't just look at it — you tap parts of it and panels of information appear. Reviews float up. Ingredients reveal themselves. A "How To Apply" guide shows up. A "Our Science" section explains the product's technology. Each of these was built as a separate "state" the experience could be in.

There was also a **"Look Inside"** feature — where the bottle would become transparent and you could see through it, almost like an X-ray of the product.

All of this had to stay properly oriented to *you* as you walked around the product. If you moved to the left, the information panels had to rotate to keep facing you. This "align to camera" problem is actually quite tricky in AR and took dedicated work.

There was a glass podium the product sat on, reflections added to make the bottle look premium and shiny, a subtle wobble animation so it felt alive. A lot of attention went into making it look *good*.

---

## It got complicated — and was deployed — May 2022

By May the project hit a new level of complexity. The experience needed to actually be driven by real data, not hardcoded content. So a MongoDB database was set up (hosted on Atlas), and the product content — reviews, ingredients, steps, images, all of it — was pulled from there at runtime.

Then came a significant expansion: instead of just one product, the system needed to handle **multiple CeraVe products**. Moisturizing Lotion, Moisturizing Cream, Foaming Cleanser, Cream to Foam — each with their own 3D model, their own data, their own content. A landing page was built so users could pick which product they wanted to explore.

A CRM button was wired in — so if someone was interested, they could tap and be connected to a sales/marketing email flow, with the URL for that coming from the database too.

This phase also involved a lot of bug fixing: a bug where the product would jump when you first placed it, lag on first load, the camera not properly recentering after a reset. The kinds of things that only become obvious when you're testing on an actual phone.

---

## A quiet summer, then Arabic — November 2022

After June there was essentially a pause. One small commit in July, then nothing for five months.

Then in late November 2022, there was a burst of activity over just a few days: **full Arabic language support**. This wasn't just translating text — Arabic is right-to-left and has different font rendering requirements, and the 3D text in the AR scene itself needed to support Arabic characters. It was clearly a requirement that came in for a Middle Eastern market, and it involved going through the entire UI — buttons, modals, labels, the 3D in-scene text — and making everything work in both English and Arabic.

There was some back and forth ("testing button-1 en to ar", "rolled back arabic buttons") which suggests Arabic had some tricky edge cases. There were also fixes to cross-origin issues with images and 3D assets — likely because the Arabic version was being tested on a different server/CDN and assets weren't loading.

A mobile console was added during this phase, which tells you the team was doing a lot of on-device debugging.

The products directory was also removed from git entirely during this stretch — the 3D model files had been moved to a CDN, which was the right call since large binary files have no business being in a git repository.

---

## Then — dormant for 3 years. Until now — March 2026

After November 2022, nothing. The project sat.

Then in March 2026 — this month — it came back. Product models were updated, product data was updated, old files were cleaned out, and the README was properly written up. The `DEPLOYMENT.md` file was also created.

This looks like someone picking the project back up — either to revive it, document it properly, or hand it off — after a long hiatus.

---

## The big picture

This was a **client-facing brand experience** for CeraVe — the kind of thing a brand would use at a retail touchpoint, in a marketing campaign, or as a "try before you buy" digital tool. It was ambitious: real-time AR, multiple products, rich interactive content, multilingual support, all running in a mobile browser with no app install.

It was built fast (the core in about 3 months), by a small team (essentially two people), and then extended for a new market (Arabic). It wasn't a perfect, polished engineering project — the commit history shows the messiness of real product development: things tried and reverted, debugging sessions, content swapped in and out. But it got built and it shipped.

And now it's being looked at again in 2026, presumably with fresh eyes.
