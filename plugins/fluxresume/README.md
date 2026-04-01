# FluxResume AI Agent Plugin

Connects Cursor to the [FluxResume](https://fluxresume.io) MCP server — enabling AI-assisted job tracking, job search, and daily career goal management directly from your editor.

## Features

- **Job Tracker** — view, add, and update jobs in your tracker
- **Job Search** — search the FluxResume job board and save results to your tracker
- **Career Goals** — read and update career preferences, track daily application targets
- **Built-in Prompts** — one-click sessions for reviewing applications, searching jobs, and running a full daily applying session

## Setup

1. Sign up at [fluxresume.io](https://fluxresume.io) and go to **Settings → AI Agent**.
2. Generate an MCP API key.
3. Install this plugin — Cursor will prompt you to paste your key.

## MCP Prompts

| Prompt | Description |
|--------|-------------|
| `review_tracker` | Review all tracked applications by status |
| `search_jobs_for_role` | Search for jobs by role and location |
| `add_job_manually` | Add an external job to the tracker |
| `update_application_status` | Batch-update job statuses |
| `start_applying_goal` | Run a full daily job-applying session |

## Skills

| Skill | Triggers |
|-------|---------|
| `fluxresume-job-tracker` | "show my jobs", "add job", "update job status" |
| `fluxresume-job-search` | "search for jobs", "find jobs", "save job to tracker" |
| `fluxresume-career-goals` | "start applying", "check my goal", "career preferences" |

## Requirements

- A FluxResume account with the AI Agent feature enabled
- Cursor with MCP support
