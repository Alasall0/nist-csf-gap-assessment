# Scope and Methodology

NIST Cybersecurity Framework 2.0 Gap Assessment
Version 1.0
2026-09-26

---

## 1. Purpose

The rules below govern how the NIST CSF 2.0 gap assessment was scoped, rated, and evidenced. They were set before any subcategory was assessed, so that every rating traces back to a stated rule instead of to judgment applied after the fact.

A reviewer should be able to pull any subcategory out of the Current Profile and find the reasoning behind its rating here.

---

## 2. Organizational context

The assessed environment is operated as a small business-to-business service provider of roughly 20 to 50 people. The organization hosts its own infrastructure and does not operate in a public cloud. It is pursuing a SOC 2 Type II report because customers have begun asking for one during procurement.

Organizational size does most of the work in an assessment like this one. At 20 to 50 people the organization is large enough that questions about defined roles, written policy, and supplier management are legitimate gaps and not inapplicable ones. It is small enough that the absence of a board, a dedicated security function, and a human resources department reflects how the organization actually operates.

The SOC 2 objective is the reason a CSF assessment is being performed at all. The crosswalk in `crosswalk/csf-to-soc2-tsc.csv` is not an appendix to the work. It is the business driver behind it.

---

## 3. System boundary

### In scope

| Asset | Role | Network segment |
|---|---|---|
| OPNsense | Perimeter firewall, routing, VLAN enforcement | Gateway, 10.10.10.1 |
| Kali Linux | Management workstation, vulnerability scanner | Management VLAN (10) |
| Ubuntu Server / Splunk | SIEM, log aggregation and detection | Monitoring VLAN (20) |
| Windows Server 2022 | Domain-representative server workload | Lab-Vulnerable VLAN (30) |
| Metasploitable2 | Non-production test asset | Lab-Vulnerable VLAN (30) |

The governance processes documented in the three preceding portfolio projects fall inside the boundary as well: the network segmentation baseline, the detection engineering program and its coverage matrix, and the vulnerability management program with its prioritization methodology, remediation SLAs, and exception process.

### Out of scope

The exclusions below are named individually so that the boundary can be verified instead of assumed.

- The operator's workstation, which sits outside the firewall and is not managed as an organizational asset
- The home network upstream of the OPNsense WAN interface
- Anything on the internet service provider side of the perimeter
- Physical and environmental controls for the hosting location
- Any cloud service, software-as-a-service application, or third-party platform, since none are in use

### Note on Metasploitable2

Metasploitable2 is deliberately vulnerable and remains inside the boundary, classified as a non-production test asset. Excluding it would be the easier choice and would improve the numbers. Keeping it is more honest, because organizations of this size do run test environments and CSF asks how those environments are governed. Where a subcategory applies differently to production and non-production assets, the Current Profile records the distinction and does not average across it.

---

## 4. Assessment approach

All 106 subcategories across the six Functions receive a rating. No subcategory is skipped.

Ratings are produced at two depths.

**Evidence-backed.** Subcategories where the preceding portfolio projects produced a real artifact. Each carries an implementation status, a rationale, and a citation to the specific artifact by file path or configuration location. Anyone holding the repository links can verify these ratings independently.

**Rationale-only.** Subcategories where no artifact exists. Each carries an implementation status and a one-sentence rationale, and each is classified as either a genuine gap or Not Applicable under the rule in section 6.

The Current Profile marks which depth applies to each row, so that a reader can tell a rating backed by evidence from a rating backed by a claim. Blending the two would misrepresent how reliable the assessment is.

---

## 5. Rating scale

Each subcategory receives one of five values.

**Fully Implemented.** The outcome is achieved, evidence exists, and a documented process governs how the outcome is sustained. Both conditions are required. Evidence without process does not reach Fully Implemented.

**Largely Implemented.** The outcome is achieved and evidence exists, but the supporting process is undocumented, informal, or dependent on a single operator's recall. The control works. It would not survive that operator's departure.

**Partially Implemented.** The outcome is achieved for some assets, some of the time, or in a materially incomplete form. Credentialed vulnerability scanning implemented for one operating system and not the others is the representative case.

**Not Implemented.** The outcome is not achieved. The subcategory falls inside the boundary for this organization and the capability is absent.

**Not Applicable.** The subcategory addresses an organizational function, asset class, or relationship that does not exist within the system boundary. Requires justification under section 6.

---

## 6. The Not Applicable rule

Not Applicable requires a written justification naming the specific organizational function, asset class, or relationship that does not exist. A justification reading "does not apply to a small organization" is not sufficient.

Not Applicable and Not Implemented produce very different assessments from the same environment, which is why the justification is mandatory. Rating an absent control Not Applicable removes it from the gap count. Rating it Not Implemented keeps it visible in the remediation roadmap. An assessment that reaches for Not Applicable produces a flattering gap count and conceals real risk, which defeats the purpose of performing a gap assessment.

Where the distinction is arguable, the subcategory is rated Not Implemented and the argument is recorded in the rationale.

---

## 7. Implementation Tier assessment

CSF Tiers are assessed once, for the Organizational Profile as a whole, in accordance with NIST SP 1302. Tiers are not applied to individual subcategories.

Tiers characterize the rigor of cybersecurity risk governance and management practices. They describe how consistently risk decisions are made and integrated, not how many controls are in place. An organization can hold strong technical controls and still sit at Tier 1 when no formal risk process informs its investment decisions.

The Tier determination and its supporting rationale are recorded in the gap assessment report. The rationale must address governance formality, risk management integration, and the consistency of practice across the environment. The Tier is argued rather than assigned, and the report should present it so that a reviewer can dispute it on the merits.

---

## 8. Target Profile

Target implementation status is recorded per subcategory, but differentiated only where the organization intends to close a gap within the planning horizon. Every other subcategory targets its current state.

A target of Fully Implemented across all 106 subcategories would produce a remediation plan that no reader would believe and no organization of this size would fund. The delta between Current and Target populates the POA&M, so the Target Profile states intent constrained by resources.

Where a subcategory is deliberately left below full implementation, the reason is recorded. Accepted risk is documented as accepted risk so that it does not read as an oversight.

---

## 9. Evidence standard

The following count as evidence:

- A committed artifact in a public repository, cited by file path
- A configuration state that can be demonstrated and captured
- A documented process in a policy authored for this environment
- A dated record of recurring activity, such as a decision log, review log, or version control history showing the practice performed over time

The following do not:

- An intention to implement a control
- A plan, roadmap, or scheduled activity
- Familiarity with how the control would be implemented

Governance outcomes assert that a process is performed repeatedly, not that a document exists. A policy proves authorship. It does not prove review, decision-making under it, or sustained practice. Restricting evidence to documents and configuration states would therefore cap every GOVERN subcategory at the existence of its artifact and would systematically under-rate one Function relative to the others, producing a scorecard that measures the evidence rules rather than the environment.

Version control history is treated as a dated record of recurring activity where the commit record demonstrates the practice itself. Risk register revisions across multiple remediation cycles, policy updates with dated justification, and successive assessment versions all qualify. A single commit establishing a document does not.

Every rating of Partially Implemented or above carries at least one citation meeting the standard above. A rating that cannot be evidenced is lowered until it can be.

---

## 10. Crosswalk methodology

CSF subcategories are mapped to the AICPA Trust Services Criteria using the AICPA source document, not a third-party summary. Where a subcategory maps to more than one criterion, all mappings are recorded and no single representative mapping is selected.

The crosswalk carries a column recording which Trust Services Criteria the current environment would fail to satisfy. Without that column the crosswalk is a lookup table and not an assessment.

---

## 11. Limitations

The constraints below affect the reliability of the assessment and are stated so that a reader can weigh the results accordingly.

**Single assessor.** The assessment is performed by the same person who built and operates the environment. There is no independent review, and self-assessment bias cannot be excluded.

**Segregation of duties.** Asset owner, security, and approver roles are performed by one operator. In a production environment that condition would itself be a control failure. It is carried forward from the vulnerability management program's documented findings.

**Simulated organizational context.** Subcategories addressing workforce, supplier relationships, and executive governance are assessed against a described organization and not an operating one. Ratings in those areas rest on the stated context and not on observed practice.

**Point in time.** The assessment reflects the environment as of the assessment date. CSF outcomes addressing continuous monitoring and improvement are assessed on the evidence available at that point.

---

## 12. Open items

- Implementation Tier determination and written rationale, to be completed with the gap assessment report
- Organizational name, if one is adopted for the assessed entity

---

## Revision history

| Version | Date | Change |
|---|---|---|
| 1.1 | 2026-10-03 | Added dated records of recurring activity as an evidence type |
