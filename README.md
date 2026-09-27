# NIST CSF 2.0 Gap Assessment

A gap assessment of a segmented on-premises environment against all 106 subcategories of the NIST Cybersecurity Framework 2.0, with a crosswalk to the AICPA Trust Services Criteria and a prioritized remediation roadmap.

The assessed environment is operated as a small business-to-business service provider of roughly 20 to 50 people that hosts its own infrastructure and is pursuing a SOC 2 Type II report. Every rating of Partially Implemented or above is backed by a citation to a specific artifact, most of them produced by the three projects listed at the bottom of this page.

## Status

In progress. Scope and methodology are complete. The Current Profile, crosswalk, POA&M, and gap assessment report are in development.

| Deliverable | Status |
|---|---|
| Scope and methodology | Complete |
| Current Profile, 106 subcategories | In progress |
| CSF to SOC 2 TSC crosswalk | Not started |
| POA&M and remediation roadmap | Not started |
| Gap assessment report | Not started |
| GRC platform evaluation | Not started |

## Repository structure

| Path | Contents |
|---|---|
| `docs/` | Methodology, gap assessment report, platform evaluation |
| `assessment/` | Current and Target Profile across all 106 subcategories |
| `crosswalk/` | Mapping from CSF subcategories to Trust Services Criteria |
| `poam/` | Prioritized remediation roadmap |

## Approach

Three decisions shape the assessment and are documented in full in [docs/scope-and-methodology.md](docs/scope-and-methodology.md).

Implementation status is rated per subcategory. CSF Implementation Tiers are assessed once for the Organizational Profile as a whole, in accordance with NIST SP 1302, and are not applied to individual subcategories.

Not Applicable requires a written justification naming the specific organizational function, asset class, or relationship that does not exist. Where applicability is arguable, the subcategory is rated Not Implemented and the argument is recorded.

Evidence means a committed artifact, a capturable configuration state, or a documented process. Intent, plans, and familiarity do not qualify. A rating that cannot be evidenced is lowered until it can be.

## Related work

The evidence cited throughout this assessment comes from three preceding projects:

- [Network segmentation and architecture baseline](#)
- [Detection engineering and SIEM coverage](#)
- [Vulnerability management program](#)
