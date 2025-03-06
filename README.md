# Setting Up GitLab Runners: Local Windows & AWS EC2
A documentation of my journey setting up GitLab runners in different environments.

## 📝 Overview
I configured two GitLab runners:
- A local runner on my Windows machine
- A runner on an AWS EC2 Linux instance


## Windows Local Runner Setup - https://docs.gitlab.com/runner/install/windows/
1. Created a folder called `GitLab-Runner` on my `C:\` drive.

![c-drive](https://github.com/Princeton45/local-aws-runner/blob/main/images/c-drive.png)

2. Downloaded the 64-bit binary which contains the gitlab-runner.exe and moved it to the folder called `GitLab-Runner` on my `C:\` drive.

![exe](https://github.com/Princeton45/local-aws-runner/blob/main/images/exe.png)

3. Ran the below commands in Powershell in the GitLab-Runner folder to install, start, and check the status of the runner:

`.\gitlab-runner install`
`.\gitlab-runner start`
`.\gitlab-runner status`

![install-runner](https://github.com/Princeton45/local-aws-runner/blob/main/images/install-runner.png)


2. Registered the runner with my GitLab instance (gitlab.com)

I used the `.\gitlab-runner register` command and provided the required information:

![register](https://github.com/Princeton45/local-aws-runner/blob/main/images/register.png)

3. Verified my runner appears in GitLab's runner list

![verify-runner](https://github.com/Princeton45/local-aws-runner/blob/main/images/verify-runner.png)


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