---
name: fluxresume-job-search
description: Use this skill when the user wants to search for jobs on the FluxResume job board or save search results to their tracker via MCP tools (search_jobs, save_searched_job). Triggers on "search for jobs", "find jobs", "save job to tracker", or the search_jobs_for_role prompt.
---

# FluxResume Job Search MCP Skill

## Available Tools

| Tool | Purpose |
|------|---------|
| `search_jobs` | Search the FluxResume job board — filters: query, city, jobType, isRemote, datePostedDays, salaryMin, salaryMax, page, pageSize |
| `save_searched_job` | Save a job from search results to the tracker (status = Bookmarked) |

## Critical: Correct Field Usage

`search_jobs` returns two ID fields per job:

| Field | When to use |
|-------|-------------|
| `id` | Do NOT use for saving |
| `job_id` | **Use this** when calling `save_searched_job` |

Always pass `job_id` (not `id`) to `save_searched_job`.

## Workflow Rules

1. Call `search_jobs` with relevant filters from the user's request.
2. Present results as a numbered list: title, company, location, salary, URL.
3. Call `get_profiles` to get the user's `categoryId`.
4. For each job the user confirms, call `save_searched_job` with `job_id`, `source_id`, and `categoryId`.
5. Confirm what was saved and offer to refine the search.

## Built-in Prompt

- `search_jobs_for_role` — guided job search session for a specific role and location
