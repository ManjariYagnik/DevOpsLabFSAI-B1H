Lab 1: Basic Linux, Git, and CI/CD 
Commands
 1. Installing Ubuntu via WSL
 Open PowerShell as Administrator and run:
 bash
 CopyEdit
 wsl --install -d Ubuntu
 Restart your computer after installation.
 Launch Ubuntu from the Start Menu to set up your username and password.
 2. Installing NixOS (Single-User Mode)
 Follow the official NixOS documentation for setup instructions.
 Single-user mode is ideal for simple experimentation and personal use.
 Using Git Bash
 Overview
 Git Bash is a terminal for Windows that supports Linux-style commands.
 Common Commands
 bash
 CopyEdit
 ls            # List files and directories
 pwd           # Show current directory
 1
 DevOps Lab File
cd Desktop    # Navigate to Desktop
 Basic Git Commands
 Cloning a Repository
 bash
 CopyEdit
 git clone https://github.com/yourrepository.git
 Checking Remotes
 bash
 CopyEdit
 git remote -v
 Viewing Branches
 bash
 CopyEdit
 git branch
 Viewing Commit History
 bash
 CopyEdit
 git log
 2
 DevOps Lab File
Checking Status
 bash
 CopyEdit
 git status
 Viewing File Changes
 bash
 CopyEdit
 git diff
 Staging and Committing
 bash
 CopyEdit
 git add filename
 git commit -m "Your message"
 Configuring Git
 bash
 CopyEdit
 git config --global user.name "jaanhvisaxena"
 Creating Files with Git Bash
 bash
 CopyEdit
 3
 DevOps Lab File
touch home
 touch office
 This creates empty files named 
CI/CD Basics
 What is CI/CD?
 home and 
office in the current directory.
 CI Continuous Integration): Automatically builds and tests code after each push.
 CD Continuous Delivery/Deployment): Automatically delivers tested code to 
production or staging environments.
 Popular CI/CD Tools
 GitHub Actions  Built into GitHub, easy for students
 Jenkins  Powerful and highly customizable
 GitLab CI/CD  Integrated in GitLab
 CircleCI and Travis CI  Easy GitHub integration and automation
 Typical CI/CD Pipeline
  Build  Compile code and install dependencies
  Test  Run automated test cases
  Deploy  Send code to production/staging
  Monitor  Track application health and respond to failure
