# Coding Cagent

This repository contains the configuration (`coding-agent.yaml`) needed to run a powerful coding agent using Docker `cagent`.

To get started, you will need to install Docker, `cagent`, and set up a global alias so you can execute the agent seamlessly from within any directory on your machine.

---

## 1. Install Docker

Docker is required to run the agent's isolated environment.

### macOS & Windows
Download and install [Docker Desktop](https://www.docker.com/products/docker-desktop/). Once installed, open the application to ensure the Docker daemon is running.

### Linux (Ubuntu/Debian)
Run the following commands in your terminal to install Docker and add your user to the `docker` group:
```bash
sudo apt-get update
sudo apt-get install docker.io
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER
```
*(Note: You may need to log out and log back in for the group permissions to take effect.)*

---

## 2. Install `cagent`

### macOS
The easiest way to install on macOS is via Homebrew:
```bash
brew install cagent
```

### Linux
If Homebrew is installed on your Linux machine, you may also use `brew install cagent`. Otherwise, refer to the official `cagent` documentation for curl-based installation scripts or binary downloads. 

### Windows
Depending on how `cagent` is distributed, you can typically install it via a package manager like Scoop or by downloading the executable and adding it to your System PATH. Please refer to the official official `cagent` documentation for specific Windows installation instructions.

---

## 3. Setup Configuration Folder & Alias

For the best experience, you should save the `coding-agent.yaml` file in a dedicated global folder and create a shell alias. By doing this, you can run the agent in the terminal of *any* repository simply by typing the command `ccode`.

### macOS & Linux

**1. Create the folder and copy the file:**
Run this in the repository's root folder where `coding-agent.yaml` is located:
```bash
mkdir -p ~/.cagent
cp coding-agent.yaml ~/.cagent/
```

**2. Create the alias:**
Open your shell configuration file (e.g., `~/.zshrc` for macOS/Zsh, or `~/.bashrc` for standard Linux bash) with your preferred editor, and add the following line at the end:
```bash
alias ccode="cagent run ~/.cagent/coding-agent.yaml"
```

**3. Apply the changes:**
```bash
source ~/.zshrc # Or source ~/.bashrc depending on your shell
```

### Windows (PowerShell)

**1. Create the folder and copy the file:**
Run this in PowerShell from the repository's root folder:
```powershell
New-Item -ItemType Directory -Force -Path "$HOME\.cagent"
Copy-Item ".\coding-agent.yaml" -Destination "$HOME\.cagent\coding-agent.yaml"
```

**2. Create the alias (Profile Function):**
PowerShell uses functions instead of standard aliases for commands with arguments. Open or create your PowerShell profile by running:
```powershell
if (!(Test-Path -Path $PROFILE)) { New-Item -ItemType File -Path $PROFILE -Force }
notepad $PROFILE
```
Add the following function inside the opened notepad file, then save and close it:
```powershell
function ccode { cagent run "$HOME\.cagent\coding-agent.yaml" }
```

**3. Apply the changes:**
```powershell
. $PROFILE
```

---

## 4. Run the Agent

1. Make sure your Docker daemon is running in the background.
2. Ensure you have downloaded your preferred model or configured your API keys. *(Note: you may need to check the `cagent` documentation for specific instructions regarding how to pass API keys.)*
3. Navigate to any code repository on your machine and run the agent using your newly created alias:

```bash
ccode
```
