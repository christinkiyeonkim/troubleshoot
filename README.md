# Ubuntu Troubleshooting Log (TTY Only Mode)

This project documents how I diagnosed and resolved three critical system issues using only the terminal (TTY), due to extreme system lag and GUI unresponsiveness.

---

## Overview of Issues

|No. |                          Problem Description            |   Status                     |
|----|---------------------------------------------------------|------------------------------|
| 1  | System extremely slow / GUI frozen                      | Resolved                     |
| 2  | System could not be updated (apt hang)                  | Resolved                     |
| 3  | Could not switch Korean/English input with Shift + Space| Resolved (pending GUI check) |

## Issue 1: System Lag (TTY Only Usable)

### Symptoms
-Ubuntu GUI froze completely, mouse lagged, and only TTY terminal was usable. 

### Diagnosis Logs
'''bash
top -n 1 -b > logs/top_log.txt
df -h > logs/disk_usage.txt
free -h > logs/memory_log.txt

## Issue 2: System Would Not Update

Cause

-apt update froze at Get:123...likely due to mirror timeout or server lag.

Steps Taken

sudo apt clean
sudo apt update | tee logs/update_log.txt
sudo apt upgrade -y | tee logs/upgrade_log.txt

## Issue 3: Shift + Space Input Switch Not working

Problem 
- could not switch between Korean and English without clicking the input bar, which wasn't accessible due to GUI freezing.

Actions Taken

ibus-daemon -rd
cat ~/.config/ibus/config > logs/ibus_config.txt 2)/dev/null

Note

Due to GUI unavailability, ibus-setup could not be launched. Screennshot will be added after GUI is restored.

echo "Unable to run ibus-setup due to TTY-only environment." > logs/crtlspace_note.txt

## SystemEnvironment
-OS: Ubuntu 22.04 LTS
-Input system: IBus
-Kernerl updated to: 6.11.0-25
-Troubleshooting environment: TTY only (GUI unavailable)

## Summary

This log demonstrates:
-Real-world system troubleshooting using only terminal tools
-How to handle frozen GUIs and unresponsive desktops
-How to capture and document logs for later reference or portfolio use.

This repository serves as a real, hannds-on example of Linux system recovery under pressure, and will be part of my professional IT help desk documentation.

