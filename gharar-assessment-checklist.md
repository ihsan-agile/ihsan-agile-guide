# Gharar Assessment Checklist
An ethical assessment tool for technical uncertainty and disclosure

---

## Purpose

This checklist helps teams evaluate **technical uncertainty introduced by delivery decisions**, using *gharar* as a **juristic lens** drawn from Islamic commercial jurisprudence.

The focus of this register is **not technical debt as such**, but whether uncertainty created by technical decisions has been:

- adequately disclosed
- responsibly stewarded
- fairly borne
- and, where appropriate, consented to

The aim is **not** to eliminate all uncertainty.  
It is to prevent **harm caused by undisclosed or unjustly transferred uncertainty**.

Throughout this checklist:

- *Technical debt* refers to a common signal that uncertainty exists
- *Gharar* refers to harmful uncertainty arising from lack of disclosure or consent
- This checklist supports ethical discernment and escalation, not moral verdicts

---

## Relationship to the Technical Uncertainty Register

This checklist does **not** replace the Technical Uncertainty Register.

- **All** technical uncertainties should be recorded in the Technical Uncertainty Register.
- The **Gharar Assessment** is used selectively to determine whether a documented uncertainty:
  - creates unjust risk
  - requires stakeholder disclosure or consent
  - demands escalation, mitigation, or refusal

In short:

> The Technical Uncertainty Register records what exists.  
> The Gharar Assessment evaluates whether that uncertainty is ethically dangerous if left as-is.

---

## When to Use This Checklist

Use the Gharar Assessment when a technical uncertainty:

- affects users, customers, or communities
- transfers risk beyond the development team
- involves safety, security, financial, legal, or religious consequences
- may mislead others about system reliability or completeness
- feels ethically uncomfortable, even if technically expedient
- is being inherited and may be perpetuated

---

## Core Assessment Questions

These questions surface **who bears uncertainty and whether they know it**, regardless of intent.

---

### 1. Disclosure
Is the uncertainty made visible to those who will bear it?

**Select all that apply:**

- [ ] The uncertainty is explicitly documented
- [ ] Limitations are described in plain language
- [ ] The rationale for the shortcut is recorded
- [ ] Future maintainers can immediately understand the risk

If none apply:

- [ ] No indication of the shortcut or its consequences exists
- [ ] Future maintainers or users are likely to be surprised

Undisclosed uncertainty preserves ignorance (jahalah) and creates conditions for harmful gharar.

---

### 2. Knowledge
Do those who bear the risk actually know it exists?

**Internal awareness:**

- [ ] Product leadership is aware of the uncertainty
- [ ] Technical leadership is aware of the uncertainty
- [ ] Ownership for this uncertainty is explicit

**External awareness (where applicable):**

- [ ] Users or customers are informed of relevant limitations
- [ ] No misleading claims of completeness or reliability are made
- [ ] Decisions can be made with informed understanding

Note: Internal awareness alone does **not** resolve disclosure if uncertainty is borne externally.

---

### 3. Impact
What harm could arise if the uncertainty materialises?

**Select the highest applicable impact:**

- [ ] Low impact  
  - Minor inconvenience or inefficiency  
  - Clear workarounds exist  
  - Limited scope and reversibility  

- [ ] Moderate impact  
  - Affects a subset of users or scenarios  
  - Non-trivial consequences if misunderstood  
  - May require escalation or safeguards  

- [ ] Severe impact  
  - Safety, security, financial, or religious harm  
  - Data loss, corruption, or misuse  
  - Users misled into harmful reliance  

At severe impact, time pressure does not justify non-disclosure or lack of consent.

---

### 4. Necessity
Is there a legitimate reason for introducing this uncertainty now?

**Legitimate necessity:**

- [ ] Critical incident or emergency
- [ ] Time-bounded external constraint
- [ ] Learning required before irreversible investment

**Not necessity:**

- [ ] Chronic over-commitment
- [ ] Convenience or vanity
- [ ] Deferring responsibility to others
- [ ] "We'll fix it later" without intent or capacity

Necessity may justify introducing uncertainty.  
Necessity never justifies concealing it.

---

### 5. Mitigation (Stewardship)
Is the uncertainty actively stewarded?

**Select all that apply:**

- [ ] Explicit owner assigned
- [ ] Concrete mitigation or resolution plan exists
- [ ] Timeline or review trigger defined
- [ ] Interim safeguards documented

If none apply:

- [ ] No owner
- [ ] No plan
- [ ] No review mechanism

Abandoned uncertainty violates amanah (trust).

---

### 6. Consent
Where appropriate, has consent been obtained with full knowledge?

**Valid consent indicators:**

- [ ] Stakeholders understand material risk
- [ ] Implications were explained honestly
- [ ] Consent is documented
- [ ] Consent obtained at the appropriate level (team, product, organisation, user-facing)

**Invalid consent indicators:**

- [ ] Agreement given without understanding
- [ ] Risks minimised or obscured
- [ ] Affected parties excluded

Consent without knowledge does not remove gharar.

---

## Uncertainty Classification
Using gharar as a juristic heuristic

Select the category that best fits after completing the assessment above:

- [ ] Category 1: Disclosed and stewarded uncertainty  
- [ ] Category 2: Concerning uncertainty requiring attention  
- [ ] Category 3: Harmful undisclosed uncertainty  
- [ ] Category 4: Inherited uncertainty (ethical to surface, unethical to perpetuate)

---

## Decision Guidance

- Severe impact: do not proceed without disclosure, consent, and safeguards
- Moderate impact: proceed only with explicit disclosure and review
- Low impact: document and steward
- No necessity: do not introduce uncertainty
- Weak stewardship: pause and repair governance

---

## Integration with Practice

- Sprint planning: assess uncertainty before committing
- Code review: verify disclosure and stewardship
- Retrospectives (muhasabah): surface patterns of concealed uncertainty
- Product stewardship: ensure responsibility does not dissolve over time

---

## Conclusion

The ethical distinction this checklist surfaces is **not** between clean and messy code.

It is between:

- shared, disclosed uncertainty, and
- concealed uncertainty that transfers harm to others

In Islamic commercial jurisprudence, the latter is named *gharar*,
not as a moral verdict, but as a signal that injustice (zulm) becomes possible
when ignorance (jahalah) is allowed to persist.

This register exists to surface that distinction **early**,
while responsibility can still be held and harm avoided.

---

## Related Resources

- [Technical Uncertainty Register Guide](./technical-uncertainty-register.md) - Structured approach to documentation of technical uncertainties and disclosure
- [Ethical Definition of Done Checklist](./ethical-dod-checklist.md) - Expand your DoD with Islamic criteria
- [Muhāsabah Retrospective Template](./muhasabah-retrospective-template.md) - Reflect on ethics in retrospectives
- [Technical Debt as Gharar (Article)](https://ihsanagile.org/technical-debt-as-gharar) - Full framework basis

---

License: CC BY-SA 4.0  
Maintained by: Ihsan Agile
