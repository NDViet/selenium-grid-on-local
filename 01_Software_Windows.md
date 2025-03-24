## Install Chocolatey

If you haven’t installed Chocolatey yet, open PowerShell as Administrator and run:
```shell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```
After installation, restart PowerShell.

## Install Prerequisite Software

```shell
choco install -y openjdk17 docker-desktop minikube kubernetes-cli kubernetes-helm
```

Verify the installation

```shell
java -version
docker --version
minikube version
kubectl version --client
helm version
```

## Additional Setup

Install WSL (if not already installed)
```shell
wsl --install
```

Set default to version 2
```shell
wsl --set-default-version 2
```

If no distributions are installed, install Ubuntu (or any preferred distribution):
```shell
wsl --install -d Ubuntu
```

Enable Hyper-V and Virtual Machine Platform

Run the following command in PowerShell as Administrator to enable Hyper-V, Virtual Machine Platform, and Windows Subsystem for Linux (WSL 2):

```shell
dism.exe /online /enable-feature /featurename:Microsoft-Hyper-V /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

Restart your computer to apply the changes if WLS installed for the first time.

### Install for test execution
Maven, Python for sample test execution
```shell
choco install -y maven python
```

Verify the installation
```shell
mvn -v
python --version
```