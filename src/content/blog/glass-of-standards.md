---
title: "🍷 A Glass of Standards: Step-by-Step Guide 💻"
description: "Explore how to maintain coding standards and prevent unstandardized code from being pushed to GitHub. By leveraging tools like Husky, Commitlint, and git-cz, you can ensure commit message standardization, branch name protection, automatic linting, formatting, and successful test runs before committing code. This step-by-step guide helps you implement these best practices, improving code quality and workflow efficiency."
pubDate: "Oct 09 2024"
heroImage: "/blogs-images/glass-of-standards.webp"
tags: [Coding Standards, Git Hooks, Commit Linting, Husky, Frontend Development, Code Quality, JavaScript, Automation, Web Development, Dev Tools]
badge: Coding Standards
---

In modern software development, maintaining code quality and consistency is essential for long-term project success. Unstandardized code, inconsistent commit messages, and messy branches can slow down development and make it harder to track progress. To address these issues, I adopted a systematic approach to ensure that only clean, standardized code gets pushed to GitHub.

In this blog, I’ll walk you through my process of implementing standardization using tools like [**Husky**](https://typicode.github.io/husky/), [**Commitlint**](https://commitlint.js.org/guides/getting-started.html), and [**git-cz**](https://www.npmjs.com/package/git-cz). By using these tools, you can enforce branch naming conventions, ensure proper commit message formatting, and automatically run code linting, formatting, and tests before any code is committed.

### Key Practices to Standardize 📝
Here are the main aspects of the development process that I aimed to standardize:

- 📝 **Commit Message Format:** Ensuring all commit messages follow a specific, clear format.
- 🌿 **Branch Name Format:** Ensuring branches are named according to a standard convention.
- 🔍 **Linting:** Ensuring code is linted (clean and error-free) before it is pushed.
- 🎨 **Formatting:** Enforcing proper code formatting before pushing to GitHub.
- ✅ **Testing:** All tests should pass before the code is committed and pushed.


### Tools for the Job 🛠️
To enforce these practices, I used the following tools:

- [**Commitlint:**](https://commitlint.js.org/guides/getting-started.html) Enforces standardized commit message formats.
- [**Husky:**](https://typicode.github.io/husky/) Hooks that run scripts before commits, such as linting or running tests.
- [**git-cz:**](https://www.npmjs.com/package/git-cz) Provides a user-friendly interface for creating commit messages.
 

Let’s dive into how to set up these tools and enforce these standards in your project.

### Step-by-Step Setup 🛠️

#### 1. Install [**Husky**](https://typicode.github.io/husky/) 🐶

First, we’ll install [**Husky**](https://typicode.github.io/husky/) to manage Git hooks. [**Husky**](https://typicode.github.io/husky/) allows us to automate tasks like linting, running tests, or checking branch names before a commit is made.

```bash
npm install --save-dev husky 
```

Next, initialize [**Husky**](https://typicode.github.io/husky/) in your project:

```bash
npx husky init
```

The init command sets up [**Husky**](https://typicode.github.io/husky/) by creating a **.husky/** directory and adding a **pre-commit** hook. This hook ensures that the code is checked before committing.

#### 2. Set Up Pre-Commit Hooks 🛑

Now, let’s define what should happen before every commit. In the **.husky/pre-commit** file, you can write the following script:


```bash
# Extract branch name
BRANCH_NAME=$(git rev-parse --abbrev-ref HEAD)

# Define the regex pattern for branch names
PATTERN="^([A-Z]+-[0-9]+)-(feat|story|task|bug)-([a-z-]+)$"

# Check if the branch name matches the pattern
if ! [[ $BRANCH_NAME =~ $PATTERN ]]; then
  echo "error: Invalid branch name format. Please follow the format: <ticketid>-(feat|story|task|bug)-<description> or use 'staging' branch"
  exit 1
fi

# Run linting, formatting, and tests
npm run lint
npm run format:fix
npm run test
```

🔒 This script checks the branch name format and ensures **linting**, **formatting**, and **testing** are performed before allowing the commit.

#### 3. Configure Commit Message Standardization with [**git-cz**](https://www.npmjs.com/package/git-cz) 🎨

To help developers write standardized commit messages, we use [**git-cz**](https://www.npmjs.com/package/git-cz). It provides a helpful CLI interface that guides the user through writing a commit message according to conventions. 📋

Install [**git-cz**](https://www.npmjs.com/package/git-cz)

```bash
npm install --save-dev git-cz
```

Next, add the following configuration to your package.json:

```bash
{
  "config": {
    "commitizen": {
      "path": "git-cz"
    }
  }
}
```

You can now add a script to your package.json for creating commits:

```bash
{
  "scripts": {
    "commit": "git cz"
  }
}
```

By running **npm run commit**, you’ll be prompted to follow a structured commit message format, ensuring consistency across the project. 🧑‍💻

#### 4. Enforcing Commit Message Standards with ✅ [**Commitlint**](https://commitlint.js.org/guides/getting-started.html)

To ensure that no one bypasses the standard commit message format, we use [**Commitlint**](https://commitlint.js.org/guides/getting-started.html). This tool checks every commit message and prevents non-standard commits.

First, install [**Commitlint**](https://commitlint.js.org/guides/getting-started.html)

```bash
npm install --save-dev @commitlint/{cli,config-conventional}
```

Next, create a configuration file **commitlint.config.js** with the following content:
```js
export default { 
  extends: ['@commitlint/config-conventional']
};
```

or by running

```bash
echo "export default { extends: ['@commitlint/config-conventional'] };" > commitlint.config.js
```

Finally, add the commit message hook to [**Husky**](https://typicode.github.io/husky/) by running:

```bash
echo "npx --no -- commitlint --edit \$1" > .husky/commit-msg
```

Now, every time a commit is made, [**Commitlint**](https://commitlint.js.org/guides/getting-started.html) will check if the message follows the standard format. If the message does not comply, the commit will be blocked. 🔒


### Conclusion 🎯
By setting up these tools, we’ve successfully automated code quality checks, enforced standardized commit messages, and protected the branch naming convention. This approach not only improves code quality but also makes the workflow more efficient and professional. 💪

By applying these techniques in your project, you can ensure consistency, avoid errors, and foster good development practices. 🚀


##### Useful Links 🔗

- [**Husky Documentation**](https://typicode.github.io/husky/)
- [**Git-cz on npm**](https://www.npmjs.com/package/git-cz)
- [**Commitlint Guide**](https://commitlint.js.org/guides/getting-started.html)


By incorporating these tools, your project can align with industry-leading standards and ensure smooth collaboration among your team members. Happy coding! 🎉