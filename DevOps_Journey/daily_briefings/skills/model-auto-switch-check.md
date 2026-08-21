# Model Auto-Switch Check

## Purpose
Periodic check to detect active sessions using fallback models and automatically switch them back to the primary model when it becomes available.

## Trigger
Run as a scheduled cron job (e.g., every hour or multiple times daily).

## Command
```bash
python3 /root/.hermes/scripts/auto_switch_to_primary.py
```

## What It Does
1. Checks if the primary model endpoint (`agnes-2.5-flash` via `router.bynara.id`) is reachable
2. Scans all active sessions in the Hermes session database
3. Identifies sessions still using fallback models (e.g., Gemini)
4. Automatically switches those sessions to the primary model
5. Reports statistics on findings and actions taken

## Expected Output
- Primary model availability status
- Total session count
- Number of sessions using fallback models
- Number of sessions successfully switched
- Success/failure status

## Configuration
- Primary model: `agnes-2.5-flash`
- Provider: `custom`
- Base URL: `https://router.bynara.id/v1`
- Script location: `/root/.hermes/scripts/auto_switch_to_primary.py`

## Notes
- This is a non-disruptive background check that runs automatically
- Sessions are only switched if the primary model is reachable
- Falls back to silent mode if nothing needs attention
- Part of the daily automation workflow for session management
