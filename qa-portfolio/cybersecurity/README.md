# My Cybersecurity Journey

I started learning IT and security from scratch in July 2026, alongside my Computer Science degree. My goal is to grow into a security engineer and, later, a security architect. This page records what I've completed, what I've built in my home lab, and what I'm working on next.

## Certifications and courses completed

| Programme | Provider | Completed |
|---|---|---|
| Google IT Support Professional Certificate (6 courses) | Google / Coursera | September 2026 |
| Microsoft IT Support Specialist Professional Certificate (6 courses) | Microsoft / Coursera | September 2026 |
| Linux Networking: Basics and Beyond Specialization (4 courses) | Pearson / Coursera | August 2026 |
| Google Cybersecurity Professional Certificate | Google / Coursera | October 2026 |
| IBM Cybersecurity Analyst Professional Certificate (14 courses) | IBM / Coursera | October 2026 |

## Home lab: Baraka Enterprises

Baraka Enterprises is a **simulated company** I invented to practise on. It is not a real organisation, and all data in it is made up. I built its network in VirtualBox with three machines on a private internal network:

| Machine | Role |
|---|---|
| BARAKA-SRV01 | Ubuntu core server |
| BARAKA-WEB01 | Ubuntu web server running Nginx |
| BARAKA-WKS01 | Windows Server Core workstation |

What I built and configured:

- **Server hardening:** key-based SSH login, root login disabled, UFW firewall, PAM password policy, and Fail2ban
- **Least-privilege firewall rules** between the machines, based on each machine's role
- **Detection script:** `ssh_login_monitor.sh`, a Bash script that uses regular expressions to find failed SSH logins in the logs and runs automatically through cron
- **Networking practice:** static IP with Netplan, subnetting, routing, DNS and troubleshooting
- **Version control:** all scripts and configs are committed to Git and pushed to GitHub over SSH keys

## Mistakes I made and what they taught me

I keep a log of what went wrong, because that's where most of the learning happened.

| What happened | What I learned |
|---|---|
| My monitoring script ran under `sudo`, but `$HOME` resolved to `/root`, so it wrote to the wrong folder and failed silently | Scripts run as root see a different environment. Check where output goes, and test with the same user that will run it |
| Host-to-VM connections failed because I mixed up NAT and Bridged networking | Know the network mode before debugging anything else; NAT needs port forwarding |
| `apt update` failed because the VM clock had drifted | Time errors can look like network or certificate errors |
| VirtualBox would not start 64-bit VMs because VT-x was disabled in the BIOS | Check the hardware settings before assuming a software fault |

## What I'm working on now

- **Python for security automation:** working through *Python for Everybody*. Next is a script that scans log files for suspicious lines.
- **Cloud migration (in progress):** moving the Baraka lab from my laptop to Oracle Cloud's free tier, so I can build a real SIEM without overloading my machine. This is a plan I've started, not a finished project.

## Plan (not yet done)

| Stage | Focus |
|---|---|
| Next | CompTIA Security+, plus Wazuh SIEM, an Nginx and ModSecurity web application firewall, and Active Directory in the lab |
| Later | Detection engineering and vulnerability management, cloud security (AWS), and a path toward security engineering and architecture |

I'm also adding AI security to my learning path, starting with the OWASP Top 10 for LLM Applications.

## How QA and security fit together

Testing and security use the same habits: look for what a system does when given input it doesn't expect, document it clearly, and show how to reproduce it. Two defects from my QA attachment were security-relevant: a profile form that accepted invalid phone numbers, and a password reset flow that never delivered its email.

## Links

- [QA portfolio](../README.md)
- Home lab repository: [nyagaka-homelab](https://github.com/NyagakaRenee/nyagaka-homelab)
