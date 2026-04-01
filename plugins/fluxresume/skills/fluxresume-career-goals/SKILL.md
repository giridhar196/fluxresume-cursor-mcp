---
name: fluxresume-career-goals
description: Use this skill when the user wants to view or update career preferences, check daily application progress, or run a daily applying session via MCP tools (get_career_preferences, update_career_preferences, get_daily_goal_progress). Triggers on "start applying", "check my goal", "career preferences", "daily target", or the start_applying_goal prompt.
---

# FluxResume Career Goals MCP Skill

## Available Tools

| Tool | Purpose |
|------|---------|
| `get_career_preferences` | Get career preferences for a profile: jobTitles, preferredLocations, jobType, workMode, salaryMin, salaryMax, dailyApplicationTarget |
| `update_career_preferences` | Partially update career preferences — only pass fields to change |
| `get_daily_goal_progress` | Check today's applied count vs target. Returns applied, target, remaining, goalMet |

## Workflow Rules

1. Always call `get_profiles` first to resolve the `categoryId`.
2. Pass `categoryId` to `get_career_preferences` and `update_career_preferences`.
3. `update_career_preferences` is a partial update — omit fields that should not change.
4. Use `get_daily_goal_progress` before and after each application to track progress.

## Daily Applying Session

Use the `start_applying_goal` prompt to run a full session:

1. Loads career preferences and daily goal
2. Searches for matching jobs using preferences as filters
3. Guides the user to apply one by one with confirmation for each submission
4. Updates tracker status to Applied (4) after each confirmation
5. Rechecks daily goal after each — stops when the goal is met

## Notes

- The user applies manually using their own resume PDF.
- Never mark a job as Applied without the user's explicit confirmation.
