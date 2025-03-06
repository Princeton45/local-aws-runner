# Setting Up GitLab Runners: Local Windows & AWS EC2
A documentation of my journey setting up GitLab runners in different environments.

## 📝 Overview
I configured two GitLab runners:
- A local runner on my Windows machine
- A runner on an AWS EC2 Linux instance


## Windows Local Runner Setup
1. Downloaded and installed GitLab Runner for Windows
2. Registered my runner using the shell executor
3. Verified my runner appears in GitLab's runner list

![Windows Runner Registration](images/windows-runner.png)

## ☁️ AWS EC2 Runner Setup
1. Created an EC2 instance using Ubuntu AMI
2. Installed and configured GitLab Runner using Docker executor
3. Successfully registered the runner with my GitLab instance

![EC2 Runner Status](images/ec2-runner.png)

## 🛠️ Configuration Details
### Windows Runner
```toml
concurrent = 1
check_interval = 0

[session_server]
  session_timeout = 1800

[[runners]]
  name = "windows-runner"
  url = "https://gitlab.com/"
  token = "XXXXXXXXXXXX"
  executor = "shell"
  shell = "powershell"