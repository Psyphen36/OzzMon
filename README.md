# Continuous Recon & Attack Surface Monitoring Pipeline

A lightweight reconnaissance pipeline built using GitHub Actions to continuously monitor target domains for changes in attack surface.

Unlike traditional one-time recon workflows, this system focuses on tracking what changes over time — surfacing newly exposed assets and helping prioritize what actually matters.

---

## Overview

The pipeline runs on a scheduled basis and performs:

- Subdomain discovery and expansion
- Service enumeration and HTTP probing
- Detection of newly discovered assets (delta tracking)
- Basic JavaScript collection for visibility
- Alerting via Discord for new findings

The goal is to reduce manual recon effort and provide a consistent view of how a target evolves.

---

## Key Features

- **Continuous Recon**  
  Runs on a schedule using GitHub Actions (no infrastructure required)

- **Delta-Based Tracking**  
  Identifies newly discovered subdomains and endpoints instead of repeating known data

- **Service Enrichment**  
  Captures HTTP status, titles, and basic technology fingerprints

- **JavaScript Monitoring (Basic)**  
  Collects JS files for further analysis

- **Real-Time Alerts**  
  Sends notifications for newly discovered assets via Discord

---

## Workflow

1. Load target domains
2. Discover subdomains (passive + TLS expansion)
3. Resolve and probe live services
4. Compare results with previous runs
5. Alert only on new findings

---

## Why This Exists

Most recon setups generate large amounts of data, but very little signal.

This pipeline is designed to:
- reduce noise
- highlight changes
- make recon more actionable

---

## Setup

### 1. Add Targets

Create a file:
```
targets/domains.txt
```
Example:
```
example.com
target.com
```

---

### 2. Add Discord Webhook

Set a repository secret:
```
DISCORD_WEBHOOK
```

---

### 3. Enable GitHub Actions

The workflow runs:
- on a daily schedule
- or manually via `workflow_dispatch`

---

## Notes

This is a simplified public version of a larger internal workflow.

Some detection logic and heuristics have been intentionally reduced.

---

## Disclaimer

This project is intended for authorized security testing and research only.  
Do not use it against systems without permission.

---

## Author

ozz