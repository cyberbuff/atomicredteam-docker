FROM mcr.microsoft.com/powershell:7.3-ubuntu-22.04

# -- Basics
RUN apt-get update && \
    apt-get install -y gnupg ca-certificates apt-transport-https software-properties-common wget

# -- Install test dependencies
RUN apt-get install -y build-essential at ccrypt clang cron curl ed golang iproute2 iputils-ping kmod libpam0g-dev less lsof netcat net-tools nmap p7zip python2 rsync samba selinux-utils ssh sshpass sudo tcpdump telnet tor ufw vim whois zip

# -- Setup pwsh profile
WORKDIR /root
RUN mkdir -p .config/powershell/
RUN echo '\n\
if (Test-Path -Path "/root/AtomicRedTeam") { \n\
Import-Module "/root/AtomicRedTeam/invoke-atomicredteam/Invoke-AtomicRedTeam.psd1" -Force \n\
$PSDefaultParameterValues["Invoke-AtomicTest:ExecutionLogPath"] = "/root/AtomicRedTeam/atomics" \n\
$PSDefaultParameterValues["Invoke-AtomicTest:ExecutionLogPath"]="1.csv" \n\
} ' > .config/powershell/Microsoft.PowerShell_profile.ps1


# # -- Install Atomic Red Team from pwsh
SHELL ["pwsh", "-Command"]
RUN IEX (IWR 'https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1' -UseBasicParsing); \
    Install-AtomicRedTeam -getAtomics
