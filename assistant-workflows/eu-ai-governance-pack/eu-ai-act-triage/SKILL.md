---
name: "eu-ai-act-triage"
description: "Fast triage of a system under the EU AI Act (Regulation (EU) 2024/1689) - 20-40 minutes through a chain of eight questions: is it an AI system at all (Article 3(1)), is the practice prohibited (Article 5), is it high-risk (Article 6 plus Annexes I and III), is general-purpose AI in play (Chapter V), which transparency obligations apply (Article 50), what is the operator's role (provider, deployer, importer, distributor, plus requalification under Article 25), and what is the resulting obligation map with deadlines. Output is a triage card: classification, role, applicable chapters, gaps, next steps, and a confidence tag on every cited provision. This is triage, not a conformity assessment - a high-risk, GPAI, or suspected-prohibited result routes to a human and a full analysis. Use when the question is whether the AI Act applies, how a system classifies, or whether the organisation is a provider or a deployer."
license: "MIT"
metadata:
  version: "1.1.0"
  author: "Wieslaw Mazur / MateMatic Solutions"
  language: "English"
  mike-display-name: "EU AI Act Triage"
  mike-type: "assistant"
  mike-availability: "add-on"
  practice: "AI Governance"
  jurisdictions: "European Union"
---
# EU AI Act Triage

Before an organisation pays for a full conformity audit, it should know whether it has a problem at all - and how big. Most "does the AI Act apply to us" questions do not need a hundred-page analysis. They need an ordered chain of determinations where each question closes or opens the next one: definition, prohibitions, high-risk, GPAI, transparency, role, obligation map, report. After 20-40 minutes the organisation holds a triage card: it knows which basket the system sits in, who it is in the value chain, and what follows from that.

The card is not a legal opinion. It is a structured starting point: an entry for the organisation's AI system register and a decision on whether the matter goes to a human for full analysis.

## When to use

- The organisation deploys or buys a tool with an AI component and asks whether the AI Act applies.
- Inventory work: a list of systems needs a preliminary classification each.
- A software vendor asks whether its product is a high-risk system or GPAI.
- A law firm builds an AI system register for a client or for itself.

## What this workflow does NOT do

- It does not replace a full compliance review or conformity assessment. The card says "this looks high-risk under Annex III point X", not "you meet Articles 8-15".
- It does not issue a legal opinion - the output is a draft classification for approval by an authorised human.
- On a high-risk, GPAI, or suspected-prohibited result it routes to a human and a full analysis. Triage ends there.
- It does not assess GDPR compliance - it flags the overlap for a separate DPIA workflow.
- It does not perform a fundamental rights impact assessment - it only signals that one is required (step 7).

## Workflow - 8 steps plus an entry gate

### Step 0 - provision verification (mandatory, before any citation)

No article number or provision text enters the card from model memory. Before recording a legal basis, fetch the current text of Regulation (EU) 2024/1689 from EUR-Lex (CELEX 32024R1689) and compare the wording. Use the consolidated text, not the 2024 original: Regulation (EU) 2026/1744 of 8 July 2026 (CELEX 32026R1744, the "Digital Omnibus on AI") amended, among others, Articles 3, 4, 5, 6, 25, 27, 50, 111 and 113 and Annex I; consolidated version 02024R1689-20260727. Check EUR-Lex for later amendments. Note the retrieval date and source on the card. A provision that could not be verified in-session gets the tag [check in EUR-Lex] and can never support a "does NOT apply" determination.

### Step 1 - is it an "AI system" (Article 3(1))

Check each element of the definition separately: a machine-based system; designed to operate with varying levels of autonomy; may exhibit adaptiveness after deployment; infers, from the input it receives, how to generate outputs (predictions, content, recommendations, decisions); outputs can influence physical or virtual environments.

Counter-examples outside the definition: classic purely rule-based software with no inference layer, simple automation, a spreadsheet with formulas. The European Commission has issued guidelines on the definition - confirm the current document in EUR-Lex before citing it.

Result: YES / NO / BORDERLINE. On NO, triage ends, but the reasoning and the register entry stay - a year from now someone will ask why you decided this was not an AI system.

### Step 2 - prohibited practices (Article 5) - checklist

Tick every point, not a "general impression":

- subliminal or purposefully manipulative techniques causing significant harm
- exploitation of vulnerabilities (age, disability, social or economic situation)
- social scoring leading to unjustified detrimental treatment
- assessing the risk of committing a criminal offence based solely on profiling or personality traits
- untargeted scraping of facial images from the internet or CCTV to build facial recognition databases
- emotion recognition in the workplace and in education (outside medical and safety exceptions)
- biometric categorisation inferring sensitive attributes (race, political opinions, trade union membership, religion, sex life, orientation)
- real-time remote biometric identification in publicly accessible spaces for law enforcement (narrow exceptions)
- generating or manipulating realistic intimate images, video or audio of an identifiable person without that person's explicit consent (Article 5(1)(ba))
- generating or manipulating child sexual abuse material within the meaning of Directive 2011/93/EU (Article 5(1)(bb))

Points (ba) and (bb) were added by Regulation (EU) 2026/1744 and apply from 2 December 2026. For placing on the market they bite only where that output is the intended purpose, or a foreseeable and reproducible outcome the system has no adequate safeguards against; for use, only where the deployer uses the system for that purpose (Article 5(1a) and (1b)).

The other prohibitions apply since 2 February 2025. A SUSPICION on even one point means STOP - human gate immediately.

### Step 3 - high-risk (Article 6 plus Annex I and Annex III)

Two qualification paths:

- Path A (Article 6(1), Annex I): the system is a product, or a safety component of a product, covered by the Union harmonisation legislation listed in Annex I and subject to third-party conformity assessment (medical devices, toys, lifts, aviation, vehicles, and so on). Since Regulation (EU) 2026/1744:
  - "safety component" is narrower (Article 3(14)): a component that fulfils a safety function or whose failure endangers the health and safety of persons or property; systems used solely for user assistance, performance optimisation, efficiency, automation, convenience or quality control are not safety components, unless their failure would endanger health and safety (Article 6(1a) and (1b));
  - third-party assessment required only for non-safety reasons (for example radio spectrum) does not meet the Article 6(1)(b) condition (Article 6(1c));
  - machinery: Directive 2006/42/EC was removed from Annex I Section A and Regulation (EU) 2023/1230 added to Section B. For high-risk systems under Section B acts only Article 6(1), Article 60a and Articles 102 to 112 apply, and Articles 57 to 59 only in so far as the high-risk requirements have been integrated into that sectoral legislation (Article 2(2)).
- Path B (Article 6(2), Annex III): a use case in one of the areas: biometrics; critical infrastructure; education and vocational training; employment and worker management; access to essential services (including credit scoring, pricing of life and health insurance, emergency dispatch, public benefits); law enforcement; migration, asylum and border control; administration of justice and democratic processes.

Article 6(3) filter: an Annex III system is not high-risk where it poses no significant risk of harm because it only performs a narrow procedural task, improves the result of a previously completed human activity, detects patterns or deviations without replacing human assessment, or performs a preparatory task. Exception to the exception: profiling of natural persons is always high-risk. Using the filter requires documenting the assessment and registering the system - confirm the exact paragraph numbers (Article 6(4), Article 49(2) [TO VERIFY]) in step 0.

### Step 4 - GPAI (Chapter V)

- Does the operator provide a general-purpose AI model, or integrate someone else's model into its own system?
- Obligations of GPAI model providers: technical documentation, information for downstream providers, a copyright policy, a training-content summary (Article 53). The partial open-source exemption does not cover models with systemic risk.
- Systemic-risk threshold (Article 51): presumption where the cumulative training compute exceeds 10^25 FLOP; then the additional obligations of Article 55 apply (model evaluations, adversarial testing, incident reporting, cybersecurity).
- GPAI Code of Practice (Article 56) - verify its status and current version at the source before relying on it.

Typical result for law firms and SMEs: deployer of a system built on GPAI, not a model provider. But see step 6 - requalification.

### Step 5 - transparency obligations (Article 50)

- Interaction with a human (chatbot): inform the person they are dealing with AI, unless obvious from context.
- Synthetic content (audio, image, video, text): machine-readable marking on the provider side.
- Emotion recognition or biometric categorisation: inform the persons exposed.
- Deepfakes: disclose that the content was artificially generated or manipulated.
- Text published to inform the public on matters of public interest: disclose AI involvement, unless the content underwent human editorial control.

These obligations apply from 2 August 2026, the general date of application (Article 113 - step 7). Transitional rule: providers of systems generating synthetic audio, image, video or text that were placed on the market before 2 August 2026 have until 2 December 2026 to comply with Article 50(2) (Article 111(4), added by Regulation (EU) 2026/1744). Assign exact Article 50 paragraph numbers to the card rows only after the step 0 verification.

### Step 6 - operator role (plus requalification under Article 25)

Determine the role: provider / deployer / importer / distributor / authorised representative. Definitions in Article 3.

Requalification test (Article 25) - you become the provider of a high-risk system when you: (1) put your name or trademark on the system, (2) make a substantial modification to a high-risk system, or (3) modify the intended purpose so that the system becomes high-risk.

The classic trap: "our chatbot" running on someone else's model, with the organisation's logo on the front. The role determines most of the obligation map, so settle this step before saying anything about obligations.

### Step 7 - obligation map, timeline, FRIA signal

State of the law relative to the triage date (deadlines in Article 113 as amended by Regulation (EU) 2026/1744 - verify in step 0, and compare the triage date with each date below rather than copying "applying" from this list):

- since 2 February 2025: prohibitions (Article 5) and AI literacy (Article 4) - APPLYING. Article 4 as replaced in 2026: providers and deployers take measures to support the AI literacy of their staff; no specific level has to be guaranteed,
- since 2 August 2025: GPAI, governance, penalties - APPLYING,
- from 27 July 2026: Articles 102 to 110,
- from 2 August 2026: the general date of application, including Article 50,
- from 2 December 2026: the new prohibitions in Article 5(1)(ba) and (bb); Article 50(2) for synthetic-content systems already on the market before 2 August 2026,
- from 2 December 2027: Chapter III Sections 1-3 for Annex III high-risk systems (Article 6(2)) - moved from 2 August 2026,
- from 2 August 2028: Chapter III Sections 1-3 for Annex I high-risk systems (Article 6(1)) - moved from 2 August 2027,
- by 2 August 2030: high-risk systems intended for use by public authorities that were on the market before the Chapter III date (Article 111(2)).

Build the map: role and classification determine the applicable chapters and articles, and from when.

FRIA signal (Article 27): a fundamental rights impact assessment before deployment is required from deployers that are bodies governed by public law or private entities providing public services, and from deployers of credit scoring and life or health insurance pricing systems (Annex III point 5 - confirm the letters in step 0). Where the DPIA under Article 35 GDPR already covers part of the FRIA, the deployer may cross-reference or reuse those sections (Article 27(4) as replaced by Regulation (EU) 2026/1744). The workflow signals the requirement and flags the DPIA overlap; it does not perform the FRIA.

### Step 8 - report: the triage card

The card, section by section:

- Header: date, who ran it, verification source, and retrieval date.
- Classification table, one row per question (AI system / prohibited / high-risk / GPAI / transparency), each row with its result, verified basis, and confidence tag.
- Operator role, with the Article 25 requalification risk and which limb triggers it.
- Applicable chapters, each with its date and status.
- The FRIA determination: required, not required, or needs analysis, with the trigger.
- Gaps: what the facts did not establish.
- Next steps, always including the register entry and, where triggered, the mandatory escalation to a human for full analysis.
- Confidence-tag summary: verified count, to-check count, and a hard zero for "do not use".

## Human gate

The triage card is a draft classification, not a decision. An authorised human (lawyer, compliance officer) reviews and approves the card before it enters the register as binding. Three results escalate mandatorily and immediately: suspected prohibited practice (Article 5), high-risk, GPAI. In those cases triage ends with a referral to a human and a full analysis.

## Source verification

The provision comes from a database, not from memory. Hard rules: every article, paragraph, point, and Annex number cited on the card must be verified in-session in EUR-Lex (CELEX 32024R1689), otherwise it carries the [check in EUR-Lex] tag; a [TO VERIFY] tag in this workflow marks a spot where a number or document status requires verification before use; a "the AI Act does not apply to us" determination can never rest on an unverified provision; the consolidated version takes precedence over memory of the original text - regulations get corrected by corrigenda.
