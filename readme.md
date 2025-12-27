SSH Brute Force Detection Lab (SIEM)
Project Overview

This project demonstrates the setup and execution of a Security Information and Event Management (SIEM) system using the Elastic Stack. The goal was to monitor, detect, and visualize a live SSH Brute Force attack simulated from a Kali Linux machine.
Tools Used

    SIEM: Elastic Stack (Elasticsearch, Kibana)

    Target/Source: Kali Linux (VM)

    Attack Tools: Hydra, Bash scripting

    Detection Logic: Elastic Security Signal Rules

Implementation Steps
1. Log Ingestion

Configured the Elastic Agent to collect system logs from the Kali Linux host and ship them to the Elastic Cloud/Server.
2. Attack Simulation

Executed a brute force attack against the local SSH service using two methods:

    Manual Loop: A bash script attempting 50 rapid logins.

    Automated Brute Force: Used Hydra with the rockyou.txt wordlist to simulate a high-speed dictionary attack.

3. Detection & Visualization

    Signal Rule: Configured a rule named "LAB - Local SSH Brute Force" to trigger when more than 5 failed login attempts occur within a minute.

    Kibana Dashboard: Created a Lens visualization using @timestamp and Count of records to show a clear spike in activity during the attack.

Results

The SIEM successfully identified the automated attack pattern. The dashboard (see screenshots below) clearly highlights the "Attack Spike" where logs jumped from baseline activity to over 1,000 events per minute during the Hydra execution.