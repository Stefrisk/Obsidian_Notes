### 🔍 What Is It?

- Simply put, a way for us to automate everything related to our code.
    
- Event-driven, with many ways to trigger workflows.
    
- Lives inside our repository alongside the code.
    
- Based on YAML syntax.
    

### 🧱 Structure

- **Runner**: The virtual machine where workflows run.
    
- **Workflow**: Contains one or more jobs.
    
- **Job**: Contains one or more steps.
    
- **Step**: Executes commands or actions.
    
- **Trigger**: Starts the workflow.
    
- **Action**: Reusable logic or tools.
    
- **Command**: Shell commands executed in steps.
    

### 🖥️ Runners

**GitHub-hosted:**

- Pre-installed tools
    
- Free for public repos
    
- 2000 minutes included for private repos
    
- Supports Windows, Linux, macOS
    

**Self-hosted:**

- Specific OS, hardware, and network
    

### ⚙️ Workflows

- Written in YAML
    
- Stored in `<project>/.github/workflows/`
    
- Define triggers, jobs, actions, and runners
    
- Should be on the `main` branch
    
- GitHub uses `${{ <expression> }}` to evaluate expressions (similar to `@` in Razor)
    

### 📄 YAML Overview

- Data serialization language
    
- Superset of JSON
    
- Popular for Infrastructure as Code (IaC)
    
- Easier to edit manually than JSON
    
- Uses indentation (typically 2 spaces)
    
- No `{}` needed
    
- Supports sequences, lists, arrays, nesting, mixed types
    

### 🧪 YAML Examples

yaml
name:
  first: Daniel
  last: Thyselius
age: 31
alive: true
jobs:
  - Programmer
  - Teacher
  - Father
  - 42


or......


block-string: |
  Everything written here
  will follow formatting
special-characters: "{now} & [<then>] : good"
datetime: 2023-12-15T02:59:43.1Z

or......


person: &person
  name: Daniel
  job: &no-job Unemployed

daniel:
  <<: *person
  age: 31
  job: programmer

ruben:
  <<: *person
  name: Ruben
  age: 2


- Anchors (`&`) define reusable blocks
    
- References (`*`) reuse them
    
- `<<:` is called "Merge Key Language-Independent Type"



### 🧑‍💻 Jobs

- Each job runs in its own runner
    
- Jobs run in parallel by default
    
- Use `jobs.<job_id>.needs` to run sequentially
    
- Steps within a job run sequentially
    

### 💻 Commands

- Shell commands
    
- You can choose the shell: `bash`, `pwsh`, `python`, `cmd`
    
- Default: Bash on Linux, PowerShell on Windows
    
- You can install tools and act like in a regular VM
    

### 🧩 Actions

GitHub Marketplace offers ready-made actions for:

- Checkout code
    
- Build code
    
- Install runtimes/tools
    
- Upload/download artifacts
    
- Deploy
    
- Linting
    
- Security scanning
    
- Pull request handling
    
- Messaging
    
- Logging
    
- And more…
    

You can also create your own actions.

### ⏱️ Triggers

- Manual
    
- Scheduled
    
- External events
    
- GitHub events:
    
    - Issues
        
    - Git (push, branch, tag)
        
    - Pull requests
        
    - Wiki
        
    - Combinations
        

### 🧠 Exercises

- Upload your Todo list to GitHub and start creating workflows
    
- Create a workflow that prints the repo name and current branch
    
- Create a workflow that builds the project
    
- Use `actions/setup-dotnet` to set the correct .NET version
    
- Trigger only on `.cs` file changes
    
- Learn about different triggers (e.g., PullRequest, push to main)
    

### 🚀 Extra Challenges

- Count number of `.cs` files
    
- Count lines of code
    
- Run the project on both Windows and Linux
    

### 🧪 Advanced Challenges

- Add input parameters to your GitHub Action
    
- Modify your Action to accept a parameter (e.g., name)
    
- Use `with` to declare the parameter in your workflow
    
- Modify your console app to read the parameter and print it
    
- Conditionally run steps based on build success
    
- Use `if` to check if the previous step succeeded
    
- Print a success message to the console
