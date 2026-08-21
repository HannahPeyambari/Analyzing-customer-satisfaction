# Olist E-Commerce Customer Satisfaction Analysis
# Executive Business Insights

## Evidence note

The evidence below is drawn from the executed results embedded in the original notebook. The refactored notebook corrects the delivery-eligibility and item-grain issues identified in the review, so delivery figures are described as approximate until it is rerun on the source CSVs. The direction and scale of the findings are still clear enough to prioritise investigation.

## Executive Summary

Customer sentiment is broadly positive—about 77% of submitted reviews are four or five stars—but fulfillment failures create disproportionate dissatisfaction. The original analysis shows a roughly two-point gap between late and non-late delivery ratings, and late orders account for nearly one-third of all one-star reviews despite representing only about 6.5% of reviewed orders with an observed delivery date. Cancellations are an even sharper experience risk: almost seven in ten reviewed cancelled orders received one star. The largest opportunity is therefore not a generic satisfaction programme; it is tighter control of delivery exceptions and order failures, directed first at high-volume product areas and screened seller cohorts.

## Key Business Insights

### 1. Meeting the delivery promise is the clearest customer-experience lever in this analysis

**Insight**  
The original run found an average review score of **2.27** for late orders versus **4.21** for the comparison group—a **1.94-point gap** on a five-point scale.

**Why It Matters**  
Customers appear to judge the marketplace experience through fulfillment reliability. A late order does not merely reduce satisfaction at the margin; it moves the typical experience from strongly positive to weak.

**Potential Business Impact**  
Reducing missed promised dates should lower detractor volume, improve marketplace trust, and protect repeat purchase propensity. It also focuses operational investment on the moment most visible to the customer.

**Evidence**  
The notebook recorded 6,410 late-delivery observations and the 2.27 versus 4.21 mean-score comparison. The original denominator included rows without delivery dates, so the late rate should be treated as approximately 6.5% pending the corrected rerun.

### 2. Late orders are a small operational minority but a major source of detractors

**Insight**  
Late orders accounted for **30.15% of one-star reviews** in the original run while representing only about **6.5%** of reviewed orders with measured delivery timing.

**Why It Matters**  
This is substantial over-indexing: the late-order cohort generates roughly 4–5 times the one-star-review share expected from its size. A broad satisfaction campaign would dilute effort; exception management is more targeted.

**Potential Business Impact**  
Even modest reductions in late deliveries can remove a disproportionately large pool of negative feedback, reducing service contacts and reputational damage without needing to change every aspect of the customer experience.

**Evidence**  
The notebook reported 30.15% of one-star reviews in the late cohort, 11,424 one-star reviews overall, and a 6.46% late rate calculated on all review rows. The refactor corrects the delivery population before publishing an exact rate.

### 3. Cancellations are an acute trust failure, not a routine status outcome

**Insight**  
Among reviewed cancelled orders, **69.29%** received a one-star rating. Cancelled orders made up just **0.61%** of reviewed order statuses but accounted for **3.69%** of all one-star reviews.

**Why It Matters**  
Cancellation is rare but disproportionately damaging. Customers may tolerate an imperfect delivery better than discovering that a completed purchase cannot be fulfilled.

**Potential Business Impact**  
Preventing avoidable cancellations can protect both near-term revenue and customer trust. Where prevention is impossible, rapid notification, alternatives, and a recovery offer may limit dissatisfaction.

**Evidence**  
The analysis counted 609 cancelled reviewed orders, 422 of which were one-star reviews. The overall one-star share of all submitted reviews was 11.51%, far below the cancelled-order rate.

### 4. A healthy headline rating masks a material dissatisfaction tail

**Insight**  
Five-star reviews comprised **57.78%** and four-star reviews **19.29%**, but **22.93%** of reviews were three stars or below; **11.51%** were one star.

**Why It Matters**  
The headline story is positive, but the low-score tail is too large to treat as isolated complaints. The distribution points to a marketplace that works well for many customers while failing sharply for identifiable operational cohorts.

**Potential Business Impact**  
Management can protect growth by treating one-star and two-star outcomes as an operational-risk queue rather than merely a reputation metric. This creates a measurable target for fulfillment and service teams.

**Evidence**  
The executed notebook reported review-score shares of 57.78% (five), 19.29% (four), 8.24% (three), 3.18% (two), and 11.51% (one).

### 5. High-volume categories deserve priority even when they are not the lowest-rated

**Insight**  
`bed_bath_table` (11,137 item-linked reviews, 3.90 average score), `furniture_decor` (8,331, 3.90), and `computers_accessories` (7,849, 3.93) combine large exposure with below-four-star average ratings.

**Why It Matters**  
The absolute lowest category score is not automatically the best place to act. A modest satisfaction problem in a very large category affects far more customers and can generate more negative reviews than a severe problem in a small category.

**Potential Business Impact**  
Root-cause work in these categories can reach a larger base of orders—potentially improving satisfaction at marketplace scale if the problem is delivery, assortment, packaging, or seller-specific.

**Evidence**  
The category table in the original notebook supplied these score and count pairs. Counts are item-linked review rows, not distinct customer orders, so they should guide prioritisation rather than be reported as customer counts.

### 6. Some category score gaps are large enough to justify diagnosis, not immediate blame

**Insight**  
Among categories with at least 50 item-linked reviews, `office_furniture` scored **3.49**, `fashion_male_clothing` **3.64**, and `fixed_telephony` **3.68**. At the other end, `books_general_interest` scored **4.45** from 549 reviews.

**Why It Matters**  
The spread suggests that the customer experience is not uniform across assortment. However, a category rating can reflect fulfillment, seller mix, product expectations, or review selection—not only product quality.

**Potential Business Impact**  
These categories are credible starting points for targeted diagnosis. Correctly identifying the underlying driver could improve conversion confidence and reduce customer-support burden; acting on the score alone could misdirect resources.

**Evidence**  
The original category ranking applied a minimum count of 50. Its inner joins and item-level grain are corrected in the refactored notebook before category scorecards should be operationalised.

### 7. Seller performance is actionable for triage, but the long tail requires a different management approach

**Insight**  
The original analysis identified **460** sellers with at least 50 item-linked reviews; they represented **77.17%** of the measured item-linked review volume. At the same time, **84.82%** of sellers fell below that threshold.

**Why It Matters**  
A relatively small screened cohort can cover most observed experience volume, making seller-level quality reviews operationally practical. But most sellers have too little feedback for a reliable ranking and should not be judged by raw averages.

**Potential Business Impact**  
Olist can use a two-track model: structured scorecards and investigation for high-volume sellers, and pooled/category-level monitoring for the long tail. This concentrates effort while reducing the risk of unfair interventions.

**Evidence**  
The original seller table contained 3,030 sellers, with 460 meeting the 50-review cutoff. The refactor changes the denominator to distinct order–seller pairs before any individual seller action.

### 8. The seller score range indicates meaningful experience variation, but not a final accountability answer

**Insight**  
Within the original screened seller cohort, the lowest observed average was **2.72** (206 item-linked reviews) and the highest was **4.82** (61 reviews).

**Why It Matters**  
The gap shows room for operational learning: strong performers may reveal practices worth replicating, while weak performers need a closer look. Yet seller scores combine category mix, location, delivery routes, order failures, and the shared marketplace experience.

**Potential Business Impact**  
Pairing this screen with delivery SLA, cancellation, defect/return, and category mix data can turn a descriptive league table into a fair intervention programme.

**Evidence**  
The original notebook listed these seller extremes after applying a minimum count of 50. It did not control for confounders, so the finding is a triage signal rather than a performance verdict.
