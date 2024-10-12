---
title: "🚀 GitHub Actions to the Rescue! 🛠️ Say Goodbye to Linting Nightmares and Failed Builds 💥"
description: "How to set up GitHub Actions for automating checks like linting, formatting, testing, and building in a frontend project. It details how to create a .yml workflow file to ensure code quality by running these checks on every push and how to enforce branch protection rules to disable the merge button until all checks pass. The article also covers the settings required to prevent bypassing these rules, ensuring code standards are maintained even if pre-commit hooks are skipped."
pubDate: "Oct 12 2024"
heroImage: "/blogs-images/github-actions-to-the-rescue.webp"
tags: [GitHub Actions, Frontend Development, CI/CD, Code Quality, JavaScript, Automation, Linting, Workflow, DevOps, Continuous Integration]
badge: "Automation"
---

Welcome back, awesome devs! 🎉 In my [***previous post***](/blog/a-glass-of-standards-step-by-step-guide/), I discussed how to standardize commit messages and branch names, and ensure linting, formatting, and testing are handled before committing code. That was a great start to keeping your repo clean and organized. But let’s be real for a second — anyone can bypass those hooks with a simple `--no-verify` flag while committing. 🤯 Uh-oh, right?

Imagine someone sneakily commenting out the checks in their **pre-commit** hook and committing messy code without linting, formatting, or passing tests! 😱 Even though their branch name and commit messages look neat, the code quality is still a mess. Don’t worry! We’ve got a superhero here – **GitHub Actions**! 🦸‍♂️

In this post, we’ll create a **GitHub Action** that automatically checks for:
- Proper **linting** ✔️
- Correct **formatting** 🧹
- Passing **tests** ✅
- Successful **build** 🏗️
- **Code coverage** threshold maintained 📊

We’ll ensure the **merge button** stays disabled 🛑 until all checks pass! Ready? Let’s dive in! 🌊


## 🛠️ Step 1: Create the GitHub Action File

First, we need to create the action that runs every time a push is made to the repo. We’ll create a file called `frontend-checks.yml` in the `.github/workflows/` folder in the root of our project.

### **Here's what the action code looks like:**

```yaml
name: Frontend Checks

on: 
  push:
    branches:
      - '**'

jobs:
  frontend-checks:
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20.x'
          
      - name: Install Dependencies
        run: npm install

      - name: Lint Code
        run: npm run lint

      - name: Format Code
        run: npm run format -- --check

      - name: Run Tests
        run: npm test -- --coverage --watchAll=false

      - name: Build Project
        run: npm run build
```



### 🎯 **Explanation of the Code:**

1. **`name: Frontend Checks`**: This is just the title of the workflow. Give it any fun name! 🎨
   
2. **Trigger on Push**: We’ve set the action to trigger on any push to any branch (`branches: '**'`).
   
3. **`runs-on: ubuntu-latest`**: This tells GitHub to use the latest Ubuntu environment to run our jobs.
   
4. **Checkout Repository**: The action checks out your repo code using the `actions/checkout@v4` action. It's like, "Let me grab that code first!" 🛒
   
5. **Set up Node.js**: It sets up Node.js (v20 here) so you can run all your JS scripts.
   
6. **Install Dependencies**: Next, it installs all your project dependencies using `npm install`. Gotta love fresh packages! 📦
   
7. **Lint Code**: This step runs your lint command (`npm run lint`). If your code has linting issues, it will catch them! 🚨

8. **Format Code**: This checks if your code formatting is proper using `npm run format -- --check`. If you’re not properly formatted, it’s a red flag. 🚩

9. **Run Tests**: The action runs your tests (`npm test -- --coverage --watchAll=false`). Let’s make sure everything works as expected! 🧪

10. **Build Project**: Finally, we build the project to ensure it doesn’t break during the build process. 🏗️


## 🛡️ Step 2: Set Up Branch Protection Rules

This is where we make sure that NO ONE can merge unless ALL checks have passed. 🚫

1. Go to your GitHub repository **Settings** ⚙️.
2. Navigate to **Branches** 🛤️ and scroll down to **Branch Protection Rules**.
3. Click **Add Rule** ➕.
4. Set a pattern for your target branches, like `main` or `dev`.
5. Check the **Require status checks to pass before merging** option ✅.
6. Use the search bar to find your checks. These are essentially your action files. Locate the one you created and add it. In our case it's `frontend-checks`
7. Set **Required pull request reviews** if you want additional reviews before merging. 👥
8. Optional: Set rules to **dismiss stale approvals** when new commits are pushed, so no one sneaks past your rules! 🕵️‍♂️


## 🎉 **Conclusion:**

With these GitHub Actions in place, you’ll never have to worry about sneaky code quality issues again! 🤖 Even if someone bypasses the pre-commit checks, our **runtime GitHub Action** will catch them red-handed. 🚔 And with branch protection rules, no one can merge without passing all tests!

If you’ve enjoyed this post, spread the love! 💌 And hey, don’t forget to share! Let’s keep the coding fun and efficient. 💪✨

Happy coding, and keep that lint clean! 🧽

