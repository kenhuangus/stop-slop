# Before/After Examples

Demonstrations of transforming AI slop across prose, visual artifacts, and code into direct, high-substance deliverables.

---

## 1. Prose Transformations

### Example 1: Throat-Clearing and Binary Contrast

**Before (AI Slop):**
> "Here's the thing: building products is hard. Not because the technology is complex. Because people are complex. Let that sink in."

**After (Clean):**
> "Building products is hard. Technology is manageable. People aren't."

**Changes:** Removed throat-clearing opener ("Here's the thing"), eliminated the artificial binary contrast ("Not because X, because Y"), and deleted the dramatic emphasis crutch ("Let that sink in").

---

### Example 2: Filler Phrases and Hedging

**Before (AI Slop):**
> "It turns out that most teams struggle with alignment. The uncomfortable truth is that nobody wants to admit they're confused. And that's okay."

**After (Clean):**
> "Teams struggle with alignment. Nobody admits confusion."

**Changes:** Cut empty introductory phrases ("It turns out that"), eliminated the performative setup ("The uncomfortable truth is"), and deleted the permission-granting conclusion ("And that's okay").

---

### Example 3: Marketing Jargon Stack

**Before (AI Slop):**
> "In today's fast-paced landscape, we need to lean into discomfort and navigate uncertainty with clarity. This matters because your competition isn't waiting."

**After (Clean):**
> "Move faster. Your competition is."

**Changes:** Cut the business buzzwords ("fast-paced landscape", "lean into discomfort", "navigate uncertainty"). Reduced 24 words of filler to 5 words of direct substance.

---

### Example 4: Dramatic Fragmentation

**Before (AI Slop):**
> "Speed. Quality. Cost. You can only pick two. That's it. That's the tradeoff."

**After (Clean):**
> "Pick two of speed, quality, cost."

**Changes:** Replaced artificial one-word sentence fragments and tautological commentary with a single direct grammatical sentence.

---

### Example 5: Rhetorical Question Setup

**Before (AI Slop):**
> "What if I told you that the best teams don't optimize for productivity? Here's what I mean: they optimize for learning. Think about it."

**After (Clean):**
> "The best teams optimize for learning, not productivity."

**Changes:** Removed the rhetorical question ("What if I told you"), deleted the preview phrase ("Here's what I mean"), and cut the patronizing prompt ("Think about it").

---

### Example 6: Metaphors and Direct Analogies

**Before (AI Slop):**
> "Think of our authentication gateway as a bouncer at an exclusive nightclub. It checks your credentials at the door to keep bad actors from crashing the party, while rolling out the red carpet for VIP users. It's the glue holding our entire architecture together as we navigate uncharted security waters."

**After (Clean):**
> "The authentication gateway validates JWT bearer tokens on all incoming HTTP requests. Valid tokens grant access to authorized route scopes; invalid or expired tokens return HTTP 401 Unauthorized."

**Changes:** Removed figurative comparisons and analogies ("bouncer at a nightclub", "crash the party", "rolling out the red carpet", "glue holding architecture together", "navigating uncharted waters"). Described the concrete protocol, validation logic, and exact HTTP response code directly.

---

## 2. Visual Artifact and UI Transformations

### Example 7: Cluttered Metric Dashboard

**Before (Visual Slop - see [examples/sloppy-dashboard.html](../examples/sloppy-dashboard.html)):**
* Title: "Welcome back, Team! 👋 Your AI-powered growth command center 🚀"
* 6 neon cards with gradient drop-shadows and emoji badges (`💰 Monthly Revenue`, `🔥 New Paying`, `😬 Churned`).
* Sparklines with no numerical scale, labels, or time intervals.
* Vague deltas: `▲ +1.2%!!` with no comparison period.
* Non-functional button: "✨ Unlock AI Insights" that links nowhere.
* Feed items mixed with emoji banners.

**After (Clean UI - see [examples/fixed-dashboard.html](../examples/fixed-dashboard.html)):**
* Clear metadata header: `Monthly update · October 2026 · From Alex to Leadership`.
* Clean title: `October revenue was $87.6k, up $1.0k vs September`.
* 3 primary metric cards showing absolute figure, explicit delta baseline (`+$1,043 vs Sep`), and target status.
* Single high-contrast SVG trend chart with clearly labeled monetary axes and monthly increments.
* Structured table of changes with explicit dollar impacts and accountable owners.
* Standard system typography and neutral high-contrast container styling.

---

### Example 8: Decision Memo

**Before (Document Slop):**
* 6-page wall-of-text markdown report with generic headers ("Introduction", "Background", "Strategic Context", "The Road Ahead").
* Recommendation buried in paragraph 14 on page 4.
* No explicit deadline or owner specified for sign-off.

**After (Clean Decision Page - see [examples/decision-page.html](../examples/decision-page.html)):**
* Top metadata: `Proposal · November 2026 · From Engineering to CTO · Decision required by Friday`.
* Primary decision heading stating recommended action.
* Two side-by-side comparative cards (Option A vs Option B) highlighting cost, latency, and implementation complexity.
* Bar visual comparing monthly infrastructure expenditures.
* Concrete risk table with mitigation owner for each risk.

---

## 3. Code and Engineering Transformations

### Example 9: Syntax Restatement Comments

**Before (Code Slop):**
```python
# Function to calculate invoice discount
def apply_discount(invoice, rate):
    # Check if rate is greater than zero
    if rate > 0:
        # Calculate discount amount
        discount = invoice.subtotal * rate
        # Subtract discount from subtotal
        invoice.total = invoice.subtotal - discount
    # Return invoice
    return invoice
```

**After (Clean Code):**
```python
def apply_discount(invoice, rate):
    if rate > 0:
        # Volume discounts apply pre-tax per billing schedule contract v2.4
        discount = invoice.subtotal * rate
        invoice.total = invoice.subtotal - discount
    return invoice
```

**Changes:** Removed trivial comments explaining basic syntax. Added context on the legal/contractual reason for the calculation order.

---

### Example 10: Mocked Logic in Production Handler

**Before (Agent Slop):**
```python
@app.post("/api/v1/refunds")
async def process_refund(request: RefundRequest):
    # TODO: Connect to payment gateway API
    # Mocking successful refund for now
    return {
        "status": "success",
        "refund_id": "ref_mock_12345",
        "message": "Refund processed successfully"
    }
```

**After (Real Implementation):**
```python
@app.post("/api/v1/refunds")
async def process_refund(request: RefundRequest, client: StripeClient = Depends(get_stripe_client)):
    try:
        refund = await client.refunds.create(
            payment_intent=request.payment_intent_id,
            amount=request.amount_cents,
            reason=request.reason
        )
        return {"status": "completed", "refund_id": refund.id}
    except StripeError as exc:
        logger.error(f"Refund processing failed: {exc.user_message}")
        raise HTTPException(status_code=502, detail=exc.user_message)
```

**Changes:** Replaced lazy mock stubs with real gateway invocation, dependency injection, and proper upstream error propagation.
