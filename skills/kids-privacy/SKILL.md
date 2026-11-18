---
name: kids-privacy
description: COPPA rules for any product a child under 13 might use, taken from the law itself with every rule linked to its section. Use when building or reviewing a kids' product, or when the user says "privacy policy for a kids app", "COPPA", "children's data", "parental consent", "kids sign-up", "is this OK for kids", "parent account", "data retention for kids", or shares a privacy page, terms page, sign-up flow or consent screen for a child-facing app. Not legal advice. It gets a page ready for a lawyer's read.
---

# Kids' privacy (COPPA)

Not legal advice. This skill gets a page and a product ready for a lawyer's read. Anything marked
**[for the lawyer]** is open. Do not settle it yourself.

The law is 16 CFR Part 312, as amended by the FTC final rule at 90 FR 16918 (22 April 2025).
In force 23 June 2025. Compliance date 22 April 2026, so the amended rule fully applies now.
Cite sections like this: § 312.4(d)(2). Quote the rule. Do not paraphrase it into new duties.

## 1. When COPPA applies

- It covers an **operator** of a commercial site or app that is **directed to children**, or that has **actual knowledge** it collects personal information from a child. [§ 312.3]
- A child is anyone under 13. [§ 312.2 "Child"]
- "Directed to children" is judged on the whole picture. Subject, visuals, animated characters, child activities, music, ads, marketing plans, and evidence of who actually uses it. [§ 312.2 "Website or online service directed to children" (1)]
- A grammar and math app for 3rd graders is directed to children. Assume COPPA applies.
- A **mixed audience** service may age-screen first. The age question must be neutral. No default age and no hint to lie. [§ 312.2 "Mixed audience"]
- Service providers who hold data for you count as you. [§ 312.2 "Operator", "on behalf of" (1)]
- Collection includes passive tracking, not only forms. [§ 312.2 "Collects" (3)]

**Personal information** [§ 312.2 "Personal information" (1) to (11)]:
- First AND last name. A first name alone is not on the list.
- But a first name becomes personal information once it is combined with any identifier below. [item (11)]
- Home address down to street and city. Email or any online contact info. A screen name that works like contact info.
- Phone number. Government ID. Photo, video or audio with the child's face or voice.
- Geolocation down to street and city. Biometrics (face template, voiceprint and more). New in 2025.
- A **persistent identifier** that recognizes a user over time and across sites. The rule names a cookie customer number, an **IP address**, a device serial number and a **unique device ID**. [item (7)]
- So a sync ID, an account ID, or an IP address in server logs is personal information.

**[for the lawyer]** If only the parent types the child's name into a parent account, is that "collected from a child"? Get a written answer before relying on it.

## 2. The online privacy notice (the privacy page)

Link it clearly from the home page AND next to every place you collect data from a child. [§ 312.4(d)]
It must be clear, complete, and hold nothing unrelated, confusing or contradictory. [§ 312.4(a)]

- [ ] Name, address, phone and email of every operator collecting or keeping children's data. One may answer for all, but all must be named. [§ 312.4(d)(1)]
- [ ] What you collect from children. [§ 312.4(d)(2)]
- [ ] Whether a child can make personal information public. [§ 312.4(d)(2)]
- [ ] How you use it. [§ 312.4(d)(2)]
- [ ] Your disclosure practices, with the identities or specific categories of third parties and why. [§ 312.4(d)(2)]
- [ ] Your **written data retention policy**, in the notice itself. [§ 312.4(d)(2), § 312.10]
- [ ] If you rely on the persistent-identifier exception: the specific internal operations, and how you stop that ID being used to contact or profile a child. [§ 312.4(d)(3), § 312.5(c)(7)]
- [ ] If you take voice clips under the audio exception: how you use them, and that you delete them right after. [§ 312.4(d)(4)]
- [ ] That a parent can review, delete, and refuse further collection or use, and how. [§ 312.4(d)(5)]

The FTC says a long notice may use expandable sections or in-page links. [90 FR 16918, discussion of § 312.4(d)(2)]

## 3. Direct notice to parents and verifiable parental consent

Consent comes BEFORE any collection, use or disclosure. A material change needs fresh consent. [§ 312.5(a)(1)]

**The direct notice (the email to the parent) must say** [§ 312.4(c)(1)(i) to (vii)]:
1. That you collected the parent's contact info (and the child's name, if so) to ask for consent.
2. That consent is required, and you collect nothing from the child without it.
3. Each item you will collect, how you use it, and where it could be disclosed.
4. Third parties by name or specific category, and why. And that the parent can consent to collection without consenting to third-party disclosure, unless that disclosure is integral to the service.
5. A link to the online notice.
6. How to give consent.
7. That you delete the contact info if no consent comes within a reasonable time. [also § 312.5(c)(1)]

**Accepted consent methods** [§ 312.5(b)(2)]:
- (i) Signed form back by mail, fax or scan.
- (ii) A credit card, debit card or online payment system that **notifies the primary account holder of each discrete transaction**, used "in connection with a transaction".
- (iii) Toll-free call with trained staff. (iv) Video call with trained staff.
- (v) Government ID checked against databases, then the ID deleted promptly.
- (vi) Knowledge-based questions too hard for a child in the home. New in 2025.
- (vii) Photo ID matched to a live face photo by trained staff, then both deleted. New in 2025.
- (viii) **Email plus.** Only for an operator that does not "disclose" children's data. Email consent, then an extra step: a confirmatory email after consent, or a letter or call. You must tell the parent they can revoke the earlier consent.
- (ix) **Text plus.** Same as email plus, by text message. New in 2025.

**Payment method, what changed.** The 2025 rule deleted the word "monetary". The FTC says a card may now be used without charging and refunding the parent. [90 FR 16918, discussion of § 312.5(b)(2)(ii)] The FTC FAQ page still quotes the old "monetary transaction" text, so trust the rule.

**Email plus, the limit.** "Disclose" excludes giving data to someone who only supports your internal operations. [§ 312.2 "Disclose" (1)] So vendors that only host, send mail or secure the app do not block email plus. Any sale, ad partner, or public posting does.

**Which fits a small paid subscription app.** The parent pays through a card checkout (Stripe). That is method (ii) if the payment system notifies the cardholder of each discrete transaction.
- **[for the lawyer]** Does a $0 trial or a card saved with no charge give "notification of each discrete transaction"? Until answered, take consent at the first real charge.
- **[for the lawyer]** Does Stripe's receipt to the cardholder satisfy the notification? Or does the card's issuer have to send it?
- **[for the lawyer]** Debit cards can reach teens. Does that matter for a 3rd grader's app?
- Fallback for free tiers: email plus, if nothing is disclosed. Send the confirmatory email and the revocation line.
- The FTC recommends offering parents a couple of methods. [90 FR 16918, fn. 402]

**Exceptions to prior consent** [§ 312.5(c)(1) to (9)]: to ask for consent, a one-time reply to a child, repeated replies with parent notice, child safety, site security and legal duties, a persistent ID used only for internal operations, and voice clips deleted right after use. Each has its own limits. Read the clause before relying on one.

**Separate consent for third parties.** Disclosure that is not integral needs its own consent. [§ 312.5(a)(2)] The FTC says selling data, advertising, and training AI are never integral. [90 FR 16918, discussion of § 312.5(a)(2)]

**Do not over-collect.** You may not make a game, prize or activity depend on more data than it needs. [§ 312.7]

## 4. Parent rights

On a parent's request, the operator must give: [§ 312.6(a)]
- A description of the types of data collected from children. [§ 312.6(a)(1)]
- The chance, at any time, to stop further use or collection, and to have the child's data deleted. [§ 312.6(a)(2)]
- A way to review the data actually collected. It must confirm the requester is the parent, and must not be unduly burdensome. [§ 312.6(a)(3)]

How a product should let parents use them:
- A parent area, behind the parent sign-in, that shows every stored item about the child.
- A "Delete my child's data" control that really deletes. "Delete" means not retrievable in the normal course of business. [§ 312.2 "Delete"]
- A "Stop collecting" control. You may end the service after that. [§ 312.6(c)]
- A contact email on the privacy page for anyone who cannot use the controls.

## 5. Written data retention policy

- Keep a child's data only as long as reasonably needed for the purpose it was collected for. [§ 312.10]
- Then delete it securely. [§ 312.10]
- **No indefinite retention.** [§ 312.10] The FTC adds "including permanently". [90 FR 16918, discussion of § 312.10]
- The policy must be written and must state: [§ 312.10]
  - the purposes for which children's data is collected,
  - the business need for keeping it,
  - a timeframe for deleting it.
- It must appear in the online privacy notice. [§ 312.10, § 312.4(d)(2)]
- Timeframes must be real numbers. The FTC's example: keep data for a specific time after the child last used the service or the subscription ended. [90 FR 16918, discussion of § 312.10] "As long as necessary" with no end date is the pattern the FTC rejected.
- Write it per item. Example: "Practice history: deleted 12 months after the subscription ends."

## 6. Written information security program

Reasonable procedures to protect confidentiality, security and integrity are required. [§ 312.8(a)]
The program must be written and scaled to the data's sensitivity and the operator's size. [§ 312.8(b)] It must:
1. Name one or more people who coordinate it. [§ 312.8(b)(1)]
2. Assess internal and external risks, and the safeguards, at least once a year. [§ 312.8(b)(2)]
3. Put safeguards in place for those risks, sized to volume, sensitivity and likelihood. [§ 312.8(b)(3)]
4. Regularly test and monitor those safeguards. [§ 312.8(b)(4)]
5. Review and update the program at least once a year. [§ 312.8(b)(5)]

## 7. Service providers vs third parties

- **Support for internal operations** means: keep the service working, network communications, sign-in and personalization, contextual ads, security, legal compliance, and fulfilling some child requests. [§ 312.2 "Support for the internal operations" (1)(i) to (vii)]
- Data used for those may NOT be used to contact a specific child, build a profile, or for behavioral ads. [same definition, (2)]
- A provider that only supports internal operations, and uses the data for nothing else, is **not a third party**. [§ 312.2 "Third party" (2)] Giving it data is **not a disclosure**. [§ 312.2 "Disclose" (1)]
- So hosting, database, email delivery and payments can get data without separate consent, IF they use it only for you.
- Before any provider or third party touches children's data, check they can protect it, and get **written assurances** they will. [§ 312.8(c)] A signed DPA or the vendor's published terms. Keep a copy.
- Anything else is a third party. It must be named in both notices and needs separate consent unless integral. [§ 312.4(c)(1)(iv), § 312.5(a)(2)]

**Other states, briefly.** California's CCPA bars selling or sharing data of a consumer under 16 without opt-in, and a parent opts in for under 13. [Cal. Civ. Code § 1798.120(c)] It only binds a "business" over about $26.6M revenue, 100,000 California consumers, or half its revenue from selling data. [§ 1798.140(d)] A tiny app is usually under all three. **[for the lawyer]** Check for new state kids' laws in the states where users live.

## 8. Check a kids' privacy page

Run this against any draft. Report each line as PASS, FAIL or ASK, with the section.

1. Linked from the home page and from every screen that collects data? [§ 312.4(d)]
2. Operator name, postal address, phone and email all present? [§ 312.4(d)(1)]
3. Every data item the code stores is listed, child and parent? [§ 312.4(d)(2)]
4. Says whether a child can make anything public? [§ 312.4(d)(2)]
5. Each use stated plainly, item by item? [§ 312.4(d)(2)]
6. Every vendor or category named, with its purpose? [§ 312.4(d)(2)]
7. Says which sharing is integral and which needs separate consent? [§ 312.5(a)(2)]
8. Retention policy inside the page, with purpose, business need and a numeric timeframe per item? [§ 312.10]
9. No "indefinitely", "as long as necessary" without an end date, or "may retain"? [§ 312.10]
10. Persistent identifiers (IP, device ID, sync ID) named, with the internal-operations purpose? [§ 312.4(d)(3)]
11. Parent review, delete and stop rights stated, with exact steps? [§ 312.4(d)(5), § 312.6]
12. Consent method named, and email plus revocation stated if used? [§ 312.5(b)(2)(viii)]
13. No analytics, ad or tracking SDK that the page does not name? [§ 312.4(d)(2)]
14. No claim the code cannot back up ("we never store", "encrypted", "deleted at once")?
15. Says consent comes before collection, and what happens with no consent? [§ 312.4(c)(1)(vii)]
16. No unrelated, confusing or contradictory text? [§ 312.4(a)]
17. Direct notice email exists and carries all seven items? [§ 312.4(c)(1)]
18. Material changes trigger new notice and consent? [§ 312.4(b), § 312.5(a)(1)]
19. Effective date on the page, and matches the last change?
20. Written security program exists (not on the page, but ask)? [§ 312.8(b)]
21. Every "[for the lawyer]" item listed at the top of the hand-off?

**Facts to verify in the code before signing off.** Grep, do not trust the draft.
- Every field written to the database, per table. Which are about the child?
- Where each lives: server DB, browser storage, service worker cache, logs.
- How long each lives. Is there a job that actually deletes it? What timeframe?
- Every vendor that receives a byte: host, DB, email, payments, CDN, error logging, fonts.
- Every identifier: account ID, device or sync ID, session token, cookie, IP in function or host logs.
- What the parent delete control removes. Does it cover backups and logs?
- Any third-party script, font or request on child screens (check the CSP).
- Any free text a child can type that could hold a name or address.
- The written assurances (DPA or terms) on file for each vendor. [§ 312.8(c)]

## 9. Sources

- 16 CFR Part 312 on eCFR, text current as of 1 Oct 2026, source line "as amended at 90 FR 16977, Apr. 22, 2025": https://www.ecfr.gov/current/title-16/chapter-I/subchapter-C/part-312 (read 25 Oct 2026)
- FTC final rule, 90 FR 16918, 22 Apr 2025 (effective 23 June 2025, compliance 22 Apr 2026): https://www.federalregister.gov/documents/2025/04/22/2025-05904/childrens-online-privacy-protection-rule (read 25 Oct 2026)
- FTC, "Complying with COPPA: Frequently Asked Questions" (parts still quote pre-2025 text): https://www.ftc.gov/business-guidance/resources/complying-coppa-frequently-asked-questions (read 25 Oct 2026)
- FTC, "Children's Online Privacy Protection Rule: A Six-Step Compliance Plan for Your Business": https://www.ftc.gov/business-guidance/resources/childrens-online-privacy-protection-rule-six-step-compliance-plan-your-business (read 25 Oct 2026)
- Cal. Civ. Code § 1798.120(c) and § 1798.140(d) (CCPA): https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=CIV&sectionNum=1798.120 (the $26,625,000 revenue threshold is the 2025 inflation-adjusted figure. Check that it is still current before relying on it.)
