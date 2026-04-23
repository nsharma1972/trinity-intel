# Trinity Intel

Published weekly regulatory intelligence from the **Trinity Regulatory Analyst**.

- **Live site:** https://intel.trinitybps.com/regulatory/ (once DNS is wired)
- **Source agent:** [trinity-content-engine/agents/regulatory_analyst.py](https://github.com/nsharma1972/trinity-content-engine/blob/main/agents/regulatory_analyst.py)
- **Cadence:** Every Sunday at 06:00 local time

## Layout

```
regulatory/
  index.html         # list of all weekly digests
  latest.html        # latest week (overwritten each Sunday)
  YYYY-Www.html      # archived weekly digests
```

## How digests get here

The `trinity-content-engine` repo on the operator's machine runs the
Regulatory Analyst weekly via launchd. After producing the digest it:

1. Renders standalone HTML via the `publish_html()` function in the agent
2. Writes HTML into this repo's working copy (sibling directory)
3. `git add`, `git commit`, `git push` to `main`
4. GitHub Pages + Cloudflare serve `intel.trinitybps.com`

## Content

Each weekly digest covers material regulatory changes across:

- **FDA** — press announcements, CDRH devices, AI/ML SaMD guidance
- **EU AI Act** — European Commission Digital Strategy, regulatory framework
- **HIPAA** — FTC consumer-protection enforcement, NIST, CISA advisories
- **SOX** — SEC press releases, EDGAR 8-K current feed, PCAOB news

Items are scored for material signal (new rule, enforcement action, comment
period) vs. procedural noise. The LLM produces an executive summary,
per-regime headlines, material-change entries, content angles, and
methodology-update suggestions for the PRISM compliance auditor module.
