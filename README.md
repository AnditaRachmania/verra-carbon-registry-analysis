# Data Quality Risk in the Verra VCS Registry

A scoring framework for assessing registry data quality and its implications for corporate carbon credit due diligence, applied to 1,700 energy sector projects in the Verra Verified Carbon Standard (VCS) public registry.

**Full working paper:** [report/verra-vcs-data-quality-report.pdf](report/verra-vcs-data-quality-report.pdf) ([Word version](report/verra-vcs-data-quality-report.docx))

**Live dashboard:** [anditarachmania.github.io/verra-carbon-registry-analysis](https://anditarachmania.github.io/verra-carbon-registry-analysis/)

## Background

Voluntary carbon markets depend on registries to certify that credits represent genuine, verifiable emissions reductions, but the quality dimensions that actually matter for credit validity, additionality, permanence, and leakage prevention, are not directly observable from registry fields alone. Corporate buyers making net-zero commitments rely on carbon credits as transitional instruments, yet have no reliable way to independently verify project-level claims before purchase. This asymmetry is well described by Akerlof's (1970) theory of markets under asymmetric information, and Wang and Strong's (1996) data quality framework offers a way to operationalize what "good" registry data should look like.

Public carbon registries record structured, auditable data on project registration, methodology, verification status, and credit issuance and retirement. This paper treats registry field completeness and internal consistency as a proximate, measurable signal of how reliable that information infrastructure actually is, distinct from (and not a substitute for) the underlying environmental integrity of any given project.

## Research question

What data quality patterns are detectable in the Verra VCS public registry, and what do these patterns signal about the verifiability of energy sector carbon credits?

## Data source

The Verra VCS public registry (registry.verra.org), exported 26 March 2026. The dataset covers all 1,700 Energy Industry projects across every lifecycle stage: 1,387 Registered projects (including Late-to-Verify), 176 Pipeline projects, and 102 Inactive projects. Data was exported manually from the public registry interface; no API access or non-public information was used.

## Methodology

A structured scoring framework operationalizes completeness and consistency (per Wang and Strong, 1996) as measurable attributes of each project record. Eight registry fields are weighted by their criticality to credit verifiability under the VCS Standard (methodology, registration date, crediting period start and end dates, emission reductions, region, project name, and proponent), with a bonus for internally consistent date ordering, for a maximum score of 100 points per project.

Risk classification proceeds in two steps: a raw quality score assigns each project to a Good, Fair, or Poor/Critical band, and status flags (Late-to-Verify status, missing methodology, missing crediting period dates, Withdrawn/Rejected status) then adjust that band into a final High, Medium, or Low data-quality-risk tier. The analysis is descriptive: frequency distributions, risk tier proportions, and a temporal spotlight on Late-to-Verify registrations. All analysis was conducted in Python (pandas, numpy, matplotlib); the full code is in `src/verra_eda.ipynb`.

The weighting scheme is author-defined rather than empirically derived, and all reported associations are correlational. No causal claims are made about project-level environmental performance; a high data-quality-risk classification reflects registry record verifiability, not a judgment on whether a project's emission reductions are genuine.

## Findings

**Late-to-Verify prevalence.** 597 projects (35.1%) carry Late-to-Verify status, meaning their records have not been updated with verification outcomes within the VCS Standard's five-year monitoring window. These projects collectively represent approximately 51 million tCO2e in stalled annual emission reductions, credits that cannot be issued until verification completes. Late-to-Verify projects score notably lower on data quality (mean 74.4) than actively Registered projects (mean 83.5).

**The 2020 CDM migration spike.** Of the 597 Late-to-Verify projects, 349 (58.5%) registered in a single year, 2020, coinciding with the sunsetting of the UN Clean Development Mechanism and the resulting migration of legacy CDM projects to VCS. This cohort shows only 28.4% crediting period date completeness, versus 45% across the full dataset, confirming that the incompleteness was inherited from legacy migration rather than caused by current administrative failure. The remaining 238 pre-2020 Late-to-Verify projects represent a materially different risk profile: genuine multi-year stalls, averaging 13.9 years in the registry without a completed verification cycle.

**Systematic field completeness gaps.** 55% of all projects are missing crediting period dates, the single most consequential gap for any time-based analysis of project performance. Registration date is missing for 17% of projects and region classification for 8%. Overall, only 32.4% of projects achieve Low Risk classification, meaning the registry as a whole carries material completeness limitations as a due diligence input.

**Methodology-level concentration.** AMS-I.D. (small-scale renewable energy projects, including small wind and hydropower) carries a 53.2% Late-to-Verify rate, well above the dataset-wide average of 35.1%, most likely reflecting that periodic third-party verification is a fixed cost that scales poorly against the smaller emission volumes these projects produce.

Geographically, risk is proportional to project volume rather than concentrated in any one country: India, China, and Turkey together account for 74% of the dataset, and their High Risk rates (6.0%, 7.7%, and 6.1% respectively) sit close to the dataset-wide average of 6.1%.

## Limitations

Data quality risk, as scored here, is a proxy for registry record verifiability, not a measure of environmental integrity; a project can carry a complete, internally consistent record and still misrepresent its actual emissions impact, and vice versa. The scoring weights are author-defined rather than empirically validated, and the analysis covers the energy sector only, at a single snapshot in time, from one registry. All associations reported are correlational; no causal mechanism is claimed, and confounding factors not examined here may explain observed patterns.

## Future research directions

The framework is intended as a foundation rather than a finished tool. Natural extensions include applying it to other project categories (AFOLU, Waste Management), validating it against other registries (Gold Standard, American Carbon Registry, Australian Carbon Credit Unit scheme), tracking quality metrics longitudinally across successive registry exports, and extending the descriptive scoring approach into a predictive classification task, work already underway separately using registry metadata as features.

## Repository structure

```
data/     raw registry exports (projects by status: registered, pipeline, inactive; plus a combined export)
src/      exploratory data analysis notebook
report/   formal working paper (Word and PDF)
index.html   interactive dashboard (GitHub Pages)
```

## Citation

Rachmania Dwipayani, A. (2026). *Data Quality Risk in the Verra VCS Registry: A Scoring Framework for Corporate Carbon Credit Due Diligence.* Working paper.
