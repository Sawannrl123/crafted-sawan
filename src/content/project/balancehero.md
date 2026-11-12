---
title: "Balance Hero"
description: "I'm the lead and architect for TrueBalance's web journeys: KYC, Account Aggregator, loan offers, lead generation, partner loans, repayments, credit cards, insurance, and an AI chat assistant. They run inside our Android and iOS apps and on the open web. Since I joined in July 2025, offer-list click-through is up 58%, web repayments have grown 284%, monthly disbursals on web are up 6x, and the auth guard I built cut error sessions by 32%."
period: "Jul 2025 - Current"
heroImage: "/projects-image/balancehero-logo.png"
badge: "Fintech"
order: 13
tags:
  [
    Next.js,
    React,
    TypeScript,
    Tailwind CSS,
    Shadcn,
    Radix UI,
    Zustand,
    REST APIs,
    SSE,
    Webhooks,
    Vitest,
    React Testing Library (RTL),
    Storybook,
    Figma,
    Github,
    Github Actions,
    Jenkins,
    Docker,
    Kubernetes,
    AWS,
    Athena,
    Elastic Search,
    Kibana,
    Sentry,
    Whatap,
    Google Analytics,
    Google Console,
    SonarQube,
    Jira,
    Claude Code,
    AI Agents,
  ]
---

# [True Balance](https://www.truebalance.io/)

I joined True Balance in July 2025 as Lead Software Engineer for the web. True Balance is a lending app for people the big banks usually skip. A big part of the app isn't native at all: KYC, loan offers, partner loans, repayments, credit cards and more are web journeys that open inside our Android and iOS apps. Whatever I ship reaches every user on both platforms the same day, with no app-store release in between. That's a great lever, and it means a bug on the web is a bug for everyone.

I'm the lead and architect on almost every major web project we've run since then. I design the structure, write a big share of the code myself, review the rest, and stay on it after release until the numbers say it's working. Most of these were team efforts with product, design, backend and the app teams. The results below are what the features delivered, and the frontend is the part I owned.

## By the numbers

- **6x** growth in monthly loans disbursed through the web (January to October 2026). On web, the share of loan applications that end in a disbursal went from **1.5% to 5.4%**.
- **596%** more people using True Balance in a browser, year on year (October 2025 to October 2026).
- **58%** higher click-through from the offer list to a loan offer after the unified offer list, and **115%** higher on the open web.
- **284%** growth in repayments made on the web in the first five months of the journey.
- **32%** fewer error sessions after the site-wide auth guard.
- **Nine journeys started from scratch**: Lending Insights, repayments, credit cards, insurance, the unified offer list, gold loan, the AI chat, coupons and the auth guard.

## Projects I led

**Lending Insights Partner (LIP).** On my first day at True Balance I started building the Discover screen for LIP, which gives users credit insights, a short survey and matched partner offers. In the first month of rollout, the share of users who finished the journey from the home card climbed from **12.9% to 23.3%**, and about **80%** of new users who finished it went on to apply for a loan. In March 2026 I led a full rebuild. In its rollout, **37%** of eligible users started LIP, **90%** of them finished it, and **40%** went on to apply for a partner loan. Sessions that include LIP grew **6.6x** between February and July 2026.

**LIP chat (AI loan assistant).** I built the chat from scratch. A reusable streaming client over SSE means answers appear as they're written. I also built the first chat page, and later an entry point on the offer lists that opens the in-app chat. It launched to 5% of LIP users and is now rolling out to 30%. I gave an internal tech talk on the architecture in October 2026.

**Unified offer list (UOL).** One list that shows our own loan offers next to partner offers, with filters and unlock cards. I started it and built it together with a colleague. After it rolled out, click-through from the offer list to an offer went from **33% to 53% (+58%)**, and on the open web from **21% to 46% (+115%)**. It now serves about **95%** of users who see an offer list. I also added a redirect, so users rejected everywhere land on gold loan instead of a dead end.

**Single Entry Point (SEP).** The one home-screen card that sends each user into the right loan journey. I built the amount-selection screen, the infrastructure for test variants B and D, and the navigation. Across variants B and D, SEP brought **2–3% more disbursal volume** on our own loans and **10–15% more lead-gen volume**. That was enough to roll it out to everyone and retire the old loan-application journey.

**Lead generation.** This is our partner-loan marketplace: landing page, survey, offer list and apply. I led the "Lead Gen 2.0" revamp of the landing page. Afterwards, the share of visitors who clicked through to apply went from **83% to 91%**. I handled the frontend for six new lending partners, taking us from **4 to 10** partners with real monthly volume. Customers applying through lead gen grew **392%** year on year, and I was part of the team that grew lead-gen disbursals about **10x** in the same period. I also built the **gold-loan** journey from scratch.

**Repayments.** I started the web repayment journey from scratch: choosing a method, going through the payment gateway, and seeing the result. I also extended the no-login payment link for overdue users. Between May and October 2026, repayments made on the web grew **284%** and the number of people paying grew **263%**. The share of visitors to the repayment page who went on to pay rose from **17% to about 27%**.

**Credit cards.** I started this journey from scratch in June 2026: browsing card offers, a survey, applying, and tracking the application. In the launch window, **58%** of users who were shown a card offer applied, and the product team called out the frontend UX as core to the launch. Applications grew **168%** in the first two months, and survey completion improved by **10%**.

**Insurance.** An optional insurance add-on inside loan offer details and approval. I built it from scratch. About **43%** of users who see the offer add it to their loan, with no significant effect on the disbursal rate. Within a month of the full rollout it was attached to **3.6%** of all disbursed loans.

**Level-Up Loan (LVL) experiments.** LVL works as a credit-limit ladder: repay early and your limit goes up. I built the LVL home card and page, the repayment bottom sheet, the "repay early, unlock more" nudge experiment, and the screens for the level-based pricing test. In that pricing test, a zero processing fee brought **11.7%** more disbursals.

**KYC.** I took over identity verification, added DigiLocker onboarding and offline KYC, and split the module into a cleaner structure. KYC completion on the open web went from **57.5% to 62.2%** between August and November 2026.

**Account Aggregator.** Users share bank statements through AA, net banking or a PDF upload. I added the net-banking and PDF paths and a guard against double submits. When the AA standard started requiring device authentication (passkeys), I built that check before the AA redirect.

**Embedded partner-loan journey.** A partner's personal loan, done entirely inside our app: PAN, details, offer, video KYC, bank and the loan agreement. I designed the architecture, wrote most of the code, and split it into seven small stages so the team could review it step by step. It's in final review.

**Coupons.** Processing-fee discount coupons on offer details and the offer list. I built it from scratch, and it's in review.

**Site-wide auth guard.** Before this, each page handled login on its own, and some didn't. I moved it into one guard: every page is protected by default, with only a short list of public routes. I also added proper session handling: an idle warning, a heads-up before the session runs out, and a clean "session expired" sheet. In the first five days after release:
- Error sessions fell **32%** (**69%** on the open web).
- Session-expiry errors fell **94%**, and loan-approval errors fell **90%**.
- Users sent back to the exact page they were on after logging in went up **128%**.
- Login conversion rose **6.1 points** on iOS and **3.4 points** on web.

## Platform work

- **Tailwind CSS v3 to v4.** I migrated the whole app in a week in August 2025: a new PostCSS setup, the theme moved into CSS (the config file went from 248 lines to 81), token names cleaned up, and an ESLint rule added to catch bad theme classes.
- **Storybook 8 to 9.** I upgraded Storybook in my second week and updated every story to match. Since then the component library has grown about **5x**, from 31 to 156 stories.
- **PR checks in CI.** I set up the GitHub Actions workflow every PR goes through: lint, formatting, type check, unit tests and a Storybook build.
- **Next toolchain upgrade.** I proposed and tested TypeScript, Vitest, Storybook 10, ESLint and Node upgrades, with the full test suite passing. A security patch for a critical Next.js advisory goes first.
- I wrote our frontend coding standards and a stacked-PRs guide in Hinglish and Korean for our India and Korea teams.

## Fixing things in production

Each fix starts with logs and ends with numbers.

- **Loan-approval errors.** Tens of thousands of errors a day came from users tapping again after their loan had already been disbursed. I fixed it on web, agreed contract changes with the backend, and split the remaining work across Android and iOS. The share of approval visitors who saw any error went from **about 13% to 2.2%**, and approval timeouts dropped from **2 to 0.1 per 100 visitors**.
- **A download that only broke in production.** A URL helper worked on dev and stage but not on prod, and it broke the pilot of the loan-agreement download. I found the difference and shipped a hardened fix. After that, every download reached the backend.
- **"Refresh does nothing" errors.** Users were tapping Refresh up to 36 times on a chunk-load error. I showed a simple retry could never recover and wrote a fix that does a one-time automatic reload instead.
- **Lost survey answers.** I matched our logs to Android WebView crash markers and showed the system was killing the page before answers were saved.
- **"Payload not found" errors.** I showed that 95% of them came from Android's hardware back button after submitting. It was a navigation problem, not lost data.
- **Dashboards.** I built Kibana funnels for onboarding, credit cards and insurance, plus a release-monitoring kit run at 15 minutes, 2 hours, 24 hours and 7 days after each big release. Our event funnels match the data warehouse within **0.06%**.

## Where AI fits in

I use AI for real work, and I've built the tools to make that repeatable for me and the team:

- **Feature prep workflow.** One command takes a product ticket through analysis, implementation plan, data model, test plan and sign-off in nine reviewed steps. I've run 29 features through it since April 2026.
- **My own Slack assistant.** A bot I run on my machine. It answers questions about our journeys from real logs, tickets and stage data, triages frontend production alerts, and drafts replies. Nothing goes out without my approval.
- **11 reusable skills** for alert triage, debugging user journeys, business metrics, privacy checks and peer-review writing.
- AI helped me crunch logs, run 40 test cases before the auth guard release, and pull the business numbers on this page from our data warehouse. The decisions and the fixes were mine.

## Recognition

- **Three-time B-Thanks winner in 2026.** B-Thanks is our peer appreciation award. Teammates nominated me **20 times** between December 2025 and June 2026, for LIP, Lead Gen 2.0, SEP and UOL, the chatbot, DigiLocker and hackathon support.
- **Part of the winning team at Hackathon 2026** (team TrueNeurons). I also helped two other teams get set up and deployed.
- Internal tech talk on the AI chat architecture (October 2026).
- A few lines from teammates I'm proud of: *"Strong ownership shown on the chatbot feature, handled from FE despite BE limits"*, *"going beyond your scope to support backend development and QA"* and *"Managing scalable solution for complex scenarios is remarkable."*

#### Tech Stack

- **Frontend:** Next.js, React, TypeScript, Tailwind CSS v4, Shadcn, Radix UI, Zustand, SSE
- **Backend & Data:** REST APIs, Webhooks, Java, PostgreSQL, Athena
- **Testing:** Vitest, React Testing Library, Storybook
- **CI/CD:** GitHub Actions, Jenkins, Docker, Kubernetes, AWS
- **Monitoring:** Kibana / Elasticsearch, Sentry, Whatap, Google Analytics, Google Search Console, SonarQube
- **AI:** Claude Code, custom skills and agents, Slack bots

#### Websites

- [Web journey](https://app.truebalance.io/)
- [Website](https://www.truebalance.io/)
