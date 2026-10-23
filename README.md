# databricks_nfl

A collection of Databricks assets and Genie Code skills for NFL and fantasy football analytics, covering pipeline conventions, job reporting, and analysis output standards.

Remote: [github.com/kylegilbreath/databricks_nfl](https://github.com/kylegilbreath/databricks_nfl)

## Repository Structure

```
databricks_nfl/
├── README.md
└── slack-notifications/
    └── SKILL.md   # Slack notification standards for NFL fantasy pipelines
```

## Skills

### slack-notifications

This skill sets the message format, the channel target, and the context every Slack notification must include. It applies to NFL fantasy pipeline runs, job completions, and analysis results.

| Event Type | Channel |
| --- | --- |
| Pipeline success | `#fantasy-football-demo` |
| Pipeline failure | `#fantasy-football-demo` |
| Analysis complete | `#fantasy-football-demo` |
| Draft board updated | `#fantasy-football-demo` |

It includes templates for four message types:

- **Pipeline Success**: job name, tables updated, row counts, duration, and catalog (`kyle_gilbreath.nfl_fantasy_football`)
- **Pipeline Failure**: job name, failed step, error message, and job run URL
- **Analysis Complete**: analysis name, top insight, players flagged, data freshness (season/week), and a link to the results
- **Draft Board Updated**: timestamp, change summary, top 5 PPR RBs and WRs, and a sleeper alert

Every message follows these rules:

- Include a timestamp or data freshness indicator
- Summarize results; never post raw DataFrames or full tables
- Include a dashboard or notebook URL whenever one is available
- Use scannable bullet points, not paragraphs

Example prompts:

- "After the weekly stats pipeline runs, post a summary to Slack"
- "Send a Slack message with the top 10 draft board picks when analysis finishes"
- "Notify the channel if the ingestion job fails"

## Using a Skill in Genie Code

Genie Code loads user skills from your workspace skills folder:

```
/Workspace/Users/<your-email>/.assistant/skills/<skill-name>/SKILL.md
```

1. Clone this repo into a Databricks Git folder.
2. Copy the skill folder (for example, `slack-notifications/`) into your `.assistant/skills/` directory.
3. Ask Genie Code to do a matching task, such as posting a pipeline summary to Slack. It will apply the skill automatically.

## Data

The skills in this repo expect fantasy football data in the Unity Catalog schema `kyle_gilbreath.nfl_fantasy_football`.

## Contributing

- Give each new skill its own folder with a `SKILL.md` that covers its purpose, conventions, rules, and example prompts.
- Add each new skill to the Repository Structure and Skills sections of this README.
- Commit and push from the Databricks Git folder to `main`, or open a pull request on GitHub.

