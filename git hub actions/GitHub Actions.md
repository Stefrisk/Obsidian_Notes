**GitHub Actions is a powerful automation tool built into GitHub that lets you run workflows directly from your repository.** You can use it to build, test, and deploy code automatically or manually, based on events like pushes, pull requests, or scheduled triggers.

### 🛠️ Key Concepts of GitHub Actions

- **Workflows**: Defined in `.yml` files inside the `.github/workflows` folder. Each workflow is a set of instructions that runs when triggered.
    
- **Events**: Triggers that start workflows, such as `push`, `pull_request`, or `workflow_dispatch` (manual trigger).
    
- **Jobs**: A workflow can have multiple jobs that run in parallel or sequentially. Each job runs on a virtual machine (called a runner).
    
- **Steps**: Each job contains steps, which are individual commands or actions.
    
- **Actions**: Reusable pieces of code that perform tasks like checking out code, setting up environments, or deploying apps.
    

### 🚀 What You Can Do With It

- **Continuous Integration (CI)**: Automatically build and test code when changes are pushed.
    
- **Continuous Deployment (CD)**: Deploy code to production or staging environments.
    
- **Automation**: Label issues, manage pull requests, or send notifications.
    
- **Manual Workflows**: Trigger builds or scripts manually using `workflow_dispatch`.
    
![[Pasted image 20251030115534.png]]
### 🧩 Example Use Cases

- Run unit tests on every pull request.
    
- Build and publish a Docker image when code is merged.
    
- Deploy a website to Azure or AWS.
    
- Send Slack notifications when a build fails.
    

GitHub provides runners for Linux, Windows, and macOS, and you can also host your own. It’s flexible, scalable, and integrates seamlessly with your development workflow.

**Anchors in GitHub Actions workflows let you reuse YAML configuration blocks, making your workflow files cleaner and more maintainable.** They’re part of the YAML spec and now supported in GitHub Actions with some limitations.

### 🧩 What Are YAML Anchors?

YAML anchors allow you to define a block of configuration once and reuse it elsewhere in the file.

- **Anchor (**`&`**)**: Assigns a name to a block.
    
- **Alias (**`*`**)**: References the named block.
    
- **Merge (**`<<`**)**: Merges the contents of an anchor into another block (not fully supported in GitHub Actions yet

```
defaults: &step-defaults
  shell: bash
  run: echo "Hello from anchor"

jobs:
  example:
    runs-on: ubuntu-latest
    steps:
      - name: Use anchor
        <<: *step-defaults
```


In this example:

- `&step-defaults` defines a reusable block.
    
- `<<: *step-defaults` pulls in that block into a step.
    

### ⚠️ Limitations in GitHub Actions

- GitHub Actions **supports anchors and aliases**, but **does not support merge keys (**`<<`**)** as of now


### 🧩 What Is a Step Template?

In GitHub Actions, a **step** is a single task within a job. A "step template" is not an official feature but rather a **pattern or reusable block** that developers replicate across workflows to maintain consistency.

```
For example:

- name: Echo template
  run: echo "This is a reusable step."
  shell: bash

```
This might be called an "echo template" because it's a simple, repeatable step that prints a message—often used for debugging or logging.

### 🔁 How to Create Truly Reusable Steps

To go beyond copy-pasting, GitHub Actions supports **composite actions**, which let you define a set of steps once and reuse them across workflows.

#### ✅ Composite Action Example

Create a file like `.github/actions/echo-template/action.yml`:
```
name: Echo Template
description: A reusable echo step
runs:
  using: "composite"
  steps:
    - run: echo "This is a reusable step."
      shell: bash

```
Then use it in your workflow:

- name: Use echo template
  uses: ./.github/actions/echo-template

This approach makes your steps modular and maintainable.

### ⚠️ Limitations

- GitHub Actions does **not support importing steps from external YAML files** directly.
    
- You can’t use YAML anchors (`<<`) for merging step templates due to limited support.
- ### 🧠 Summary

- **"Echo template"** is a nickname for a reusable `echo` step.
    
- For real reuse, use **composite actions**.
    
- Avoid relying on YAML anchors for step reuse in GitHub Actions.
![[Pasted image 20251030120132.png]]
	![[Pasted image 20251030115014.png]]
### 🧪 4. **Code Playground with Auto-Tests**

- **What it does:** Create a repo where you experiment with code (Python, JavaScript, etc.). GitHub Actions runs tests or linters every time you push code.
    
- **Why it’s helpful:** You get instant feedback and learn CI/CD concepts hands-on.

### 📸 2. **Photo Backup Reminder**

- **What it does:** Set up a GitHub Action that sends you a reminder (via email or webhook) every Sunday to back up your photos or sync them to cloud storage.
    
- **Why it’s useful:** Keeps your memories safe and builds a habit — all automated.
### 📬 5. **Send Yourself a Weekly Digest**

- **What it does:** GitHub Actions scrapes your repo (or even external APIs) and sends you a weekly email with updates — like your GitHub contributions, weather, or news headlines.
    
- **Why it’s cool:** It’s like building your own personal newsletter bot.