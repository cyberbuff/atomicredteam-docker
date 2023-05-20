FROM mcr.microsoft.com/powershell:mariner-2.0-arm64

# Install net-tools which is used by Install-AtomicRedTeam
RUN tdnf install net-tools cronie build-essential iputils curl wget at clang ed golang kmod less lsof nmap p7zip rsync sshpass sudo zip iptables -y


# -- Setup pwsh profile
WORKDIR /root
RUN mkdir -p .config/powershell/
RUN echo -e '\n\
if (Test-Path -Path "/root/AtomicRedTeam") { \n\
Import-Module "/root/AtomicRedTeam/invoke-atomicredteam/Invoke-AtomicRedTeam.psd1" -Force \n\
$PSDefaultParameterValues["Invoke-AtomicTest:ExecutionLogPath"] = "/root/AtomicRedTeam/atomics" \n\
$PSDefaultParameterValues["Invoke-AtomicTest:ExecutionLogPath"]="1.csv" \n\
} ' > .config/powershell/Microsoft.PowerShell_profile.ps1


# -- Install Atomic Red Team from pwsh
SHELL ["pwsh", "-Command"]
RUN IEX (IWR 'https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1' -UseBasicParsing); \
    Install-AtomicRedTeam -getAtomics
