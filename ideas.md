# e-Account Design Direction

## Saddex jihadood oo suurtagal ah

### 1. Emerald Ledger
**Very Brief Intro:** Nidaam fintech ah oo nadiif ah, deggan, oo leh emerald cagaaran, ivory khafiif ah, iyo cards leh qoto-dheeri yar. Dareenku waa kalsooni, xakameyn, iyo hawl maalmeed fudud.

**Probability:** 0.07

### 2. Ink & Copper
**Very Brief Intro:** Interface madow-buluug ah oo editorial ah, oo copper orange loogu isticmaalo xaaladaha OUT iyo digniinaha. Waxay dareensiisaa buug xisaabeed casri ah oo xoog leh.

**Probability:** 0.04

### 3. Quiet Paper
**Very Brief Intro:** Qaab diiran oo paper-like ah, leh beige, charcoal, iyo olive accents. Waxa uu xoogga saaraa akhris fudud iyo khibrad cashier oo aan buuq lahayn.

**Probability:** 0.02

## Jihada la doortay: Emerald Ledger

### Design Movement
Swiss-inspired fintech minimalism: nidaam cad, typography adag, spacing deggan, iyo hierarchy muuqata, laakiin leh softness iyo warmth ku habboon PWA mobile-first.

### Core Principles
1. **Ledger-first clarity:** Total IN, Total OUT, Balance, iyo status waa in hal eegis lagu fahmi karaa.
2. **One account, one identity:** Customer-ku waa entity joogto ah; transactions-ku waa history ku xiran, ma aha cards customer oo kala go'an.
3. **Calm confidence:** Emerald wuxuu muujinayaa positive flow; coral/orange wuxuu muujinayaa OUT iyo khatar; neutrals-ku waxay ka dhigayaan interface-ka mid aan daalin.
4. **Mobile cashier speed:** Touch targets waaweyn, bottom navigation, bottom sheets, iyo actions kooban.

### Color Philosophy
Emerald-ka qoto dheer wuxuu la xiriiraa lacag, koritaan, iyo kalsooni, laakiin waxaa loo isticmaalaa si xakameysan si uusan u noqon dashboard cagaaran oo buuq badan. Off-white background-ku wuxuu siinayaa neefsasho; ink navy ayaa bixiya akhris xooggan; coral-ka diiran wuxuu kala saaraa OUT iyo negative balance. Signature brand color: `#087F68`.

### Layout Paradigm
Asymmetric ledger rail: desktop-ka sidebar dhuuban oo joogto ah iyo main canvas ballaaran; mobile-ka top header kooban iyo bottom nav joogto ah. Dashboard-ku wuxuu ka bilaabmaa greeting iyo balance pulse, ka dibna wuxuu u qulqulaa summary strip, quick actions, iyo activity stream. Customer account-ku wuxuu leeyahay identity rail yar iyo balance card weyn oo ah focal point.

### Signature Elements
- Calaamadda lowercase **e** gudaha rounded square oo leh inner cut yar.
- Balance cards leh left accent rail iyo status phrase oo si cad u sharxaya macnaha lacagta.
- Ledger activity rows leh IN emerald dot ama OUT coral dot, iyo monospaced account/transaction IDs.

### Interaction Philosophy
Action kasta wuxuu leeyahay feedback cad: press scale yar, toast marka la keydiyo, saving state marka submit la riixo, iyo modal/bottom sheet aan lumin context-ka account-ka. Navigation-ku waa direct; wax aan shaqaynayn lama qarinayo.

### Animation
Transitions 160–220ms, ease-out oo degdeg ah. Cards-ku waxay soo galaan opacity + translateY yar; modals-ku waxay ka soo kacaan bottom mobile iyo scale 0.98 desktop. Balance update wuxuu leeyahay numeric emphasis gaaban, mana jiro motion muhiim ah oo aan ku jirin prefers-reduced-motion.

### Typography System
Display: `DM Sans` 700/800 oo loogu talagalay totals, page titles, iyo balance. Body: `Inter` 400/500/600 oo loogu talagalay labels, tables, forms, iyo navigation. IDs iyo rates: `IBM Plex Mono` 500. H1 34–40px desktop / 28px mobile; card totals 26–32px; labels 11–12px uppercase with tracking.

### Brand Essence
**e-Account waa cashier-first customer ledger loogu talagalay ganacsiyada yaryar ee u baahan inay si degdeg ah u arkaan IN, OUT, iyo balance—offline, cad, oo aan customer-ka ku celcelin.**

**Personality:** Deggan, sax ah, daryeel leh.

### Brand Voice
Headlines waa toos oo kalsooni leh. CTAs waa ficil cad, ma aha jargon. Microcopy-gu wuxuu sharxaa natiijada, ma aha inuu isticmaalo accounting terms adag.

- “Know every account at a glance.”
- “Add movement to Ahmed’s account.”

### Wordmark & Logo
Wordmark-ku wuxuu isticmaalaa `e-Account` oo leh lowercase e, hyphen gaaban, iyo letter spacing yar. Mark-ku waa rounded square emerald ah oo ay dhexda ku jirto lowercase e ivory ah; e-ga wuxuu leeyahay terminal yar oo u janjeera midig si uu u muujiyo dhaqdhaqaaq.

### Signature Brand Color
`#087F68` — Emerald Ledger. Waa cagaar qoto dheer oo gaar u ah e-Account, ku filan contrast, kana shaqeeya light iyo dark surfaces.

## Implementation reminders

- Main logic must live in reusable utilities: totals, balance, date filters, grouping, and currency-aware calculations.
- Use localStorage first for a lightweight working build, with a storage abstraction that can later be replaced by IndexedDB without changing components.
- Never seed fake business data. The initial state is an intentional empty state, while the user can add real customers and transactions.
- Every file added for the app should preserve the Emerald Ledger style: calm surfaces, crisp type, strong hierarchy, and functional micro-interactions.
- Ask: “Does this choice reinforce or dilute Emerald Ledger?” before adding a new pattern.

## Style Decisions

- Use Emerald Ledger as the single visual source of truth.
- Keep the first delivery focused on a functional local ledger experience: dashboard, customer list, customer account, transactions, reports summary, settings shell, theme toggle, and backup/restore.
- Keep the architecture ready for IndexedDB migration, but do not introduce backend services for this static-first milestone.

## Content Boundaries

No fake customer reviews, ratings, or testimonials. No hardcoded business totals in production UI. Empty states should invite the user to create their first real customer.
