---
name: fluxresume-job-tracker
description: Use this skill when the user wants to view, add, or update jobs in the FluxResume job tracker via MCP tools (get_profiles, get_jobs, add_job, update_job_status). Triggers on "show my jobs", "add job to tracker", "update job status", "review my applications", or any job tracker workflow.
---

# FluxResume Job Tracker MCP Skill

## Available Tools

| Tool | Purpose |
|------|---------|
| `get_profiles` | List the user's resume profiles (categoryId, name, isDefault) |
| `get_jobs` | Fetch tracked jobs — supports search, statusId filter, skip/take pagination. Default returns 20 most recent. |
| `add_job` | Manually add a job to the tracker (company, title, url, categoryId) |
| `update_job_status` | Update a tracked job's status by jobV2Id and statusId |

## Status Reference

| ID | Status |
|----|--------|
| 1 | Bookmarked |
| 2 | Researching |
| 3 | Applying |
| 4 | Applied |
| 5 | Interviewing |
| 6 | Negotiating |
| 7 | Offer Received |
| 8 | Accepted |
| 9 | I Withdrew |
| 10 | Not Selected |
| 11 | No Response |
| 12 | Declined |
| 13 | Archived |
| 14 | On Hold |

## Workflow Rules

1. Always call `get_profiles` first to obtain the user's `categoryId`.
2. Pass `categoryId` to `get_jobs` and `add_job`. Never omit it.
3. When calling `update_job_status`, use the numeric `statusId` — do not pass a status name.
4. For `get_jobs` use the `search` parameter for keyword filtering and `statusId` to filter by stage.

## Built-in Prompts

- `review_tracker` — full tracker review with status summary
- `add_job_manually` — guided workflow to add an external job
- `update_application_status` — list and batch-update job statuses
