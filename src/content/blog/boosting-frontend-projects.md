---
title: "Boosting Frontend Projects: A Journey of Improvement"
description: "Improving the frontend development process by introducing tools and best practices. Key changes included standardizing commit messages with Commitlint and Husky, ensuring code quality with ESLint, Prettier, and Jest, and monitoring production errors with Sentry. We improved state management using Zustand, automated releases with Semantic Release, and optimized performance by reducing bundle size with Bundle Analyzer and Sharp. By integrating these tools, we made our project more efficient, scalable, and easier to maintain."
pubDate: "Oct 04 2024"
heroImage: "/blogs-images/boosting-frontend-projects.webp"
tags: [Frontend Development, Code Quality, Commit Standardization, ESLint, Prettier, Testing, Jest, Semantic Release, Husky, Zustand, Performance Optimization, Sentry, Bundle Analyzer, TailwindCSS, TypeScript, Caching, CI/CD, Web Performance, Error Monitoring, State Management]
badge: "Frontend Development"
---

As a lead at [PocketFM](https://pocketfm.com/), I faced a host of issues when I joined: messy commit messages, code without proper linting or formatting, unnoticed production bugs, repetitive code, and performance bottlenecks. There was also a lack of standardization around releases, and no real caching strategies, which led to slower performance and frustrated users.

Rather than being overwhelmed, I saw these as opportunities for improvement. Over the course of a year, I introduced a set of practices and tools that transformed the way we worked. These tools not only helped us build faster but also ensured robustness and scalability in our frontend project.

#### Challenges I Faced:
- **No Commit Message Standardization:** Without clear, structured commit messages, it was hard to understand what was being changed or why. We couldn’t tell if a commit was a bug fix, a feature, or a hotfix, and this made managing releases extremely difficult.
- **Code Pushed Without Linting, Formatting, or Tests:** Developers often pushed code without ensuring it was properly linted, formatted, or tested. This resulted in inconsistent code quality and bugs slipping into production.
- **Unnoticed Production Bugs:** Production bugs often went unnoticed, leading to broken user experiences and delayed fixes.
- **Repetitive Code Without Modularity:** Our codebase lacked modularity, resulting in a lot of repetitive code, which made scaling difficult.
- **No Release Maintenance or Tagging:** There was no structured versioning or release process, making deployments difficult to manage and track.
- **Performance Bottlenecks Due to Lack of Caching:** We weren’t using caching effectively, leading to poor performance and increased server load.
- **Bloated Bundle Size:** We had several unnecessary packages in our bundle that increased load times. These could be replaced with lighter alternatives to improve performance.


## The Approach: A Year of Transformation
Over the year, I introduced a series of tools that addressed each of these issues, and today I’ll walk you through how they can help boost your frontend projects.

#### 1. **Standardizing Commit Messages with [Commitlint](https://www.npmjs.com/package/@commitlint/config-conventional) & [Husky](https://typicode.github.io/husky/)**
One of the first things we tackled was commit message standardization. Using [**Commitlint**](https://www.npmjs.com/package/@commitlint/config-conventional), we enforced a structured format like ***feat:, fix:, chore:***, which helped categorize commits. This made it easy to understand whether a commit was a bug fix, feature addition, or something else.

We paired this with [**Husky**](https://typicode.github.io/husky/), which allowed us to run **Git hooks**. Husky ensured that these commit checks, along with linting and tests, were automatically run before a commit could be made.

**Result:** This made release management smoother, as we could easily identify changes in each release, ensuring a more stable deployment process.

#### 2. **Ensuring Code Quality with [ESLint](https://eslint.org/), [Prettier](https://prettier.io/), and [Jest](https://jestjs.io/)**

To maintain code quality, we introduced [**ESLint**](https://eslint.org/) for **linting** and [**Prettier**](https://prettier.io/) for **formatting**. Both tools ensured that our code followed consistent standards, making it easier to read and maintain.

For **testing**, we integrated [**Jest**](https://jestjs.io/) to write **unit tests**, ensuring that new features were well-tested before they went live. We enforced these practices using **Husky’s pre-commit hooks** to prevent bad code from being pushed.

**Result:** This improved the overall quality of our codebase, making it cleaner, more readable, and less prone to bugs.


#### 3. **Real-Time Error Monitoring with [Sentry](https://docs.sentry.io/)**

To handle **unnoticed production bugs**, we integrated [**Sentry**](https://docs.sentry.io/). It provided us with real-time error monitoring, detailed stack traces, and alerts whenever an error occurred in production. This allowed us to react quickly to issues before they affected too many users.

**Result:** Production bugs were **caught and resolved** much faster, greatly improving user experience.

#### 4. **Modular Code with [Zustand](https://zustand-demo.pmnd.rs/) and [Tanstack Query](https://tanstack.com/query/latest)**

The lack of modularity in the codebase was a major pain point. To address this, we started using [**Zustand**](https://zustand-demo.pmnd.rs/) for **state management**, which offered a **lightweight**, **easy-to-use** solution compared to more bloated libraries. For **data fetching** and **synchronization**, we adopted [**Tanstack Query**](https://tanstack.com/query/latest) (formerly React Query), which **simplified data management and caching**.

**Result:** This enabled us to write **reusable**, **scalable code**, improving both **performance** and **maintainability**.


#### 5. **Automated Releases with [Semantic Release](https://semantic-release.gitbook.io/semantic-release)**

Release management was inefficient and prone to human error. We implemented [**Semantic Release**](https://semantic-release.gitbook.io/semantic-release), which automated the entire process. Based on **commit messages**, it automatically determines the version bump (**major**, **minor**, **patch**), generates **release notes**, and **tags** the version.

**Result:** This streamlined our **versioning process** and made releases more **predictable** and **consistent**.

#### 6. **Reducing Bundle Size with [Bundle Analyzer](https://www.npmjs.com/package/webpack-bundle-analyzer) and [Sharp](https://sharp.pixelplumbing.com/)**

Our bundle size was larger than necessary, causing slower load times. We used [**Bundle Analyzer**](https://www.npmjs.com/package/webpack-bundle-analyzer) to visualize the bundle and identify bloated packages. Where possible, we replaced heavier packages with lighter alternatives. For example, we used [**Sharp**](https://sharp.pixelplumbing.com/) to optimize image loading by converting images to more efficient formats like **WebP**.

**Result:** These changes **reduced load times** significantly, **improving** both **performance** and user **experience**.

#### 7. **Performance Boost with Tailwind CSS and Plugins**

As I’ve mentioned in my [**previous blog**](https://sawannirala.netlify.app/blog/efficient-css-in-the-modern-era-unlocking-tailwind-css-and-plugin-ecosystem/), we transitioned to [**Tailwind CSS**](https://tailwindcss.com/) to **improve styling consistency** and **reduce custom CSS**. We also used several **Tailwind plugins** to extend its functionality without adding too much weight to our bundle.

**Result:** This **reduced development time** by eliminating custom styles and ensured a **consistent, responsive design** across our platform.


#### 8. **Environment Configuration with [Dotenv-Vault](https://www.dotenv.org/)**

Managing **environment variables** securely is always a challenge, especially in production environments. We integrated [**dotenv-vault**]((https://www.dotenv.org/)) to **securely manage** and share environment variables across different environments (development, staging, and production) without risking exposure.

**Result:** This made it easier to **maintain environment configurations** across multiple stages of development without risking security.


#### 9. **Sorting Imports with [Import Sort](@ianvs/prettier-plugin-sort-imports)**

To maintain a clean codebase, we introduced [**Import Sort**](@ianvs/prettier-plugin-sort-imports), which automatically sorts imports in a standardized way. This eliminated any confusion or mess caused by poorly ordered imports, improving code readability.

**Result:** The code was easier to navigate, making it more maintainable.

#### 10. **Optimizing State and Logic with [Zod](https://zod.dev/) and [TypeScript](https://www.typescriptlang.org/)**

We also leveraged [**Zod**](https://zod.dev/) for **schema validation**, which ensured that the data flowing through our application was correctly validated. [**TypeScript**](https://www.typescriptlang.org/) was another major addition to our stack, enabling us to catch type-related bugs at compile-time, leading to more robust code.

**Result:**  [**Zod**](https://zod.dev/) and [**TypeScript**](https://www.typescriptlang.org/) together **improved type safety**, **reduced runtime errors**, and helped in catching bugs during the development phase itself.

#### 11. **End-to-End Testing with [Cypress](https://www.cypress.io/)**

For end-to-end testing, we introduced [**Cypress**](https://www.cypress.io/). It allowed us to simulate user interactions and verify that the app worked as expected from a user’s perspective. By automating this testing, we ensured that the most critical user flows were bug-free before every release.

**Result:** This **reduced** the number of **production bugs** and **improved user experience**.


## Conclusion

The journey to improving our **frontend development** process was a long one, but it was well worth it. By introducing tools like **Commitlint, Husky, ESLint, Prettier, Jest, Sentry, Zustand, Semantic Release**, and **many others**, we have transformed the way we work. These changes didn’t happen overnight, but by gradually adopting these practices, we’ve significantly boosted the speed, efficiency, and quality of our development process.

> **Note:-** If you’re looking to level up your own frontend project, I encourage you to start integrating some of these tools and practices. Not only will it make your development process smoother, but it will also result in a more robust, maintainable, and scalable product.
