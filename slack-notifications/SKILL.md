# Skill: Pipeline Notifications via Slack

## Purpose
Use this skill whenever a pipeline run, job completion, or analysis result should be communicated to Slack. It defines message format, channel targets, and what context to always include.

## Channel Targets
| Event Type | Channel |
|---|---|
| Pipeline success | `#fantasy-football-demo` |
| Pipeline failure | `#fantasy-football-demo` |
| Analysis complete | `#fantasy-football-demo` |
| Draft board updated | `#fantasy-football-demo` |

## Message Format — Pipeline Success
```
✅ *NFL Fantasy Pipeline Complete*
• Run: {job_name}
• Tables updated: {table_list}
• Row counts: {row_count_summary}
• Duration: {duration}
• Catalog: kyle_gilbreath.nfl_fantasy_football
```

## Message Format — Pipeline Failure
```
❌ *NFL Fantasy Pipeline Failed*
• Run: {job_name}
• Failed at: {step_name}
• Error: {error_message}
• Action needed: Check job run at {job_run_url}
```

## Message Format — Analysis Complete
```
📊 *Fantasy Analysis Ready: {analysis_name}*
• Top insight: {top_insight}
• Players flagged: {count}
• Data through: {max_season} Week {max_week}
• View results: {dashboard_url or table_path}
```

## Message Format — Draft Board Updated
```
🏈 *Draft Board Updated*
• Timestamp: {timestamp}
• Changes: {change_summary}
• Top 5 PPR RBs: {rb_list}
• Top 5 PPR WRs: {wr_list}
• Sleeper alert: {sleeper_name} ({reason})
```

## Rules
- Always include a timestamp or data freshness indicator
- Never post raw DataFrames or full tables to Slack — summarize
- If a dashboard or notebook URL is available, always include it
- Keep messages scannable — use bullet points, not paragraphs

## Example Usage
> "After the weekly stats pipeline runs, post a summary to Slack"
> "Send a Slack message with the top 10 draft board picks when analysis finishes"
> "Notify the channel if the ingestion job fails"
