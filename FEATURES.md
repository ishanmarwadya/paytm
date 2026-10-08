# Paytm Vyapaar Pay – Concept and Features

**Team:** Velocity Squad, IIM Bangalore
**Competition:** Paytm Innovation Challenge 2026, Track B – merchants as UPI payers
**Version:** Prototype v4 (8 Oct 2026)

This document explains what Vyapaar Pay is, who it is for, and what every feature does. It is written in plain language so anyone on the team, or a judge, can follow it without opening the app.

---

## 1. The idea in one paragraph

Small shops collect money on Paytm all day. But when they **pay their suppliers**, that money moves through many routes: UPI apps, cash, cheques and bank transfers. Much of it is also **udhaar** (goods on credit), recorded in a diary or not at all. Vyapaar Pay is a business-payments space inside Paytm for Business. In it:
- a shop pays every supplier in one place;
- credit between shop and supplier is **written down once and seen by both sides**;
- payments can be made in parts;
- the hisaab (accounts) is kept automatically;
- a good payment record turns into access to credit.

The goal is to make paying suppliers simpler and more transparent, not to push people away from any other app.

---

## 2. Who it is for

### 2.1 Main user
The owner of a small shop who buys stock regularly from 5–30 suppliers, often on credit, and pays ₹0.5–10 L a month to them. The **kirana owner** is the main persona, because kiranas are the largest group and pay suppliers most often.

### 2.2 Six business types in the prototype
Each opens with its own suppliers, dues, bills and "Today's focus".

| Business type | Demo shop | What makes it different |
|---|---|---|
| Kirana / general store | Raju General Stores, Chickpet | Daily milk, weekly FMCG, credit from distributors |
| Medical store | Shifa Medicals, Frazer Town | 15–30 day credit, near-expiry returns |
| Hardware & electricals | Patil Hardware, SP Road | Big bills (₹50K–2.5 L), above the UPI limit, 30–45 day credit |
| Restaurant / cloud kitchen | Ananya's Kitchen, HSR Layout | Many small daily vendor payments, food-cost tracking |
| Salon | Glow Unisex Salon, Indiranagar | Rent and stylist commissions, few suppliers |
| Wholesaler / distributor | Manjunath FMCG Distributors | Pays brands ₹5–6 L at a time and chases 150 retailers |

### 2.3 Two sides of every relationship
Every business type also has a **Supplier view**: its main supplier (for example, Manjunath FMCG for the kirana). You switch with **Shop | Supplier** in the top bar. Both views read the **same records**. When the supplier sends a bill, the shop sees it; when the shop pays, the supplier sees it.

---

## 3. How the app is laid out

### On a phone
| Where | What it does |
|---|---|
| **Top-left menu button (grid icon)** | Opens all features. Becomes a back arrow inside a feature. |
| **Bottom bar – shop** | Home · Khata · **Scan** (big cyan button) · Dues · Book |
| **Bottom bar – supplier** | Home · Customers · **New credit** · Dashboard · Get paid |
| **Bell (top-right)** | Notifications |

### On a laptop
A left sidebar with the main sections: Home, Khata, Pay, Dues, Book, Dashboard, Credit & Score, More.

### Top bar (prototype only)
| Control | What it does |
|---|---|
| Business-type chip | Change the persona |
| **Shop / Supplier** | Switch sides |
| **Field demo** | Opens the guided demo |
| **Display** | One small menu for language (English/हिंदी), view (Mobile/Desktop) and theme (Light/Dark/Auto) |

---

## 4. Features – shop side

### 4.1 Home
Shows only what matters today:
- **New credit bills** waiting for you to accept.
- **Today's galla:** money in and money out today, and what you owe suppliers in total (with any interest so far). Tap it to open the khata.
- **Due now:** bills due today or overdue, each with a **Pay now** button.
- **Today's focus:** the one most useful action for this business. For example, "pay Manjunath by tomorrow and save ₹577", or "₹1.85 L is above the UPI limit – pay the rest by NEFT".
- **Pay again:** your most frequent suppliers with the last amount paid. You can always change the amount.

### 4.2 Supplier khata (credit agreements)
This is the core new idea.

**How a credit bill is created and accepted**
1. The supplier sends a **credit bill** with:
   - the amount and bill number;
   - interest-free days (7, 15, 30… up to 60);
   - interest after that (none, 1%, 1.5%, 2% or 3% a month);
   - an optional early-pay discount;
   - whether part payments are allowed.
2. The shop **accepts once**, with one tap. After that, both see exactly the same terms, balance and history.
3. If a shop took goods on a verbal promise, it can **record the credit itself**. The supplier then confirms it.

**What both sides can do in the chat**
- **Shop:** ask for more days (with a reason), promise a payment date, pay, or decline.
- **Supplier:** grant or refuse more days, send a reminder, waive interest, or record a cash/cheque payment received.

**How interest works**
- Interest is **simple**, counted daily, and only on the unpaid balance after the interest-free date.
- Paytm **never deducts interest on its own**. It only shows what is owed under terms the shop accepted.

**When the other side isn't on Paytm**
- The bill goes as a **WhatsApp link**. They check the terms, accept with an OTP, and can pay with any UPI app.
- The record still updates for the Paytm user.

**Legal note on the bill:** if the supplier is a registered micro/small enterprise, the bill shows a note about the MSMED Act 45-day payment rule. Paying late can also make the buyer lose the tax deduction for that year (Income Tax Section 43B(h)).

### 4.3 Pay in parts
- Every pay screen for a credit bill shows: bill balance, interest so far, any early-pay discount, and the amount to close it.
- Quick buttons: **Full**, **Half**, **Interest only** – or type any amount.
- Money goes to interest first, then to the bill. The rest stays on the khata and updates for the supplier immediately.

### 4.4 Paying suppliers
- **Scan & Pay:** works with any UPI QR. A new QR can be saved as a supplier with one tap.
- **Where the amount comes from:** scanning starts with an **empty** amount plus recent amounts as shortcuts, because the supplier usually tells you the amount. Pay again pre-fills the last amount, labelled as such.
- **Above the UPI limit:** pay up to the limit by UPI and the rest by NEFT in the same step, or split over days.
- **Bulk pay:** pay staff, daily vendors or stylist commissions together.
- **Voice pay:** "Nandini ko 12400 bhejo" → the app shows the supplier and amount → you confirm.
- **Proof to supplier:** WhatsApp receipt with UTR and bill number.
- **Credit notes:** an approved return claim is adjusted automatically on the next payment to that supplier.

### 4.5 Dues
- Everything owed, grouped as Overdue / Today / This week / Later, with a calendar on desktop.
- Every due says **where it came from**:
  - bill link from the supplier;
  - a bill you photographed;
  - a credit agreement;
  - a recurring payment the app learned;
  - a fixed monthly payment;
  - one you added yourself.
- The Soundbox reads out the day's dues every morning (time set in Settings).

### 4.6 Book, dashboard and CA export
- **Book:** every payment in and out, with what it was for and whether a bill is attached. **Tap any payment to change its category.** You can apply that category to the supplier forever, or mark a payment "Personal" so it stays out of business totals.
- **Dashboard:**
  - 30-day money in vs money out;
  - a **14-day forecast** that warns on the day dues will run ahead of expected collections;
  - price changes and simple suggestions.
- **Cash & cheques:** log cash in two taps. Log cheques, including post-dated ones; they appear in the forecast so you keep enough in the bank.
- **Export for CA:** Excel + bills, Tally, PDF or CSV, sent on WhatsApp.

### 4.7 Vyapaar Score and credit
- **Score:** 300–900, built only from activity in the app. It is not a CIBIL score.

| Part | Weight |
|---|---|
| Paying suppliers on time | 30% |
| Steady daily business | 25% |
| Money in vs money out | 20% |
| Supplier relationships | 10% |
| Clean records | 10% |
| Paying digitally | 5% |

- Each part shows its score out of 100 and one plain tip. A 6-month trend line is shown.
- **Consent first:** a single switch shares the summary with partner lenders. The screen lists what is shared and what is never shared (customer names, item-level bills, chats). Consent is for 30 days and can be revoked any time.
- **Offers (after consent):**
  - a credit line on UPI for supplier payments;
  - a working-capital loan;
  - "the lender pays your supplier today, you repay in 60 days".

  Each opens a sample Key Fact Statement. All lenders and rates in the prototype are illustrative.

### 4.8 Other tools (in the menu)
| Tool | What it does |
|---|---|
| Rate memory | Price history per item from bills; flags quiet price rises |
| Returns & claims | Raise a claim with a photo; approved claims become credit notes |
| Customer udhaar | Money your customers owe you; send a payment link on WhatsApp |
| Perks | Levels based on value paid through Vyapaar Pay and on-time dues – rental waiver, priority support, higher credit line. No cashback. |
| Charges & fees | Every rupee charged, with 30 days' notice of any change |
| Family & staff | A son, CA or helper can help with their own access; the owner approves payments |
| Agent setup | A Paytm agent saves 5 suppliers in about 10 minutes on the monthly Soundbox visit |
| Help | 30-minute call-back; one-tap proof when a supplier says "payment nahi aaya" |

---

## 5. Features – supplier side

| Feature | What it does |
|---|---|
| Home | Money to collect, collected today, and **Needs your attention**: extension requests, late payers, unaccepted bills. Ageing of money owed (not yet due, 1–7, 8–30, 30+ days late). |
| Customers | Each shop with amount owed, interest, on-time %, and whether they are on Paytm or reached by WhatsApp link |
| New credit | Create a bill with terms. A live preview shows the terms in rupees: "Pay ₹42,000 by Thu 22 Oct – no interest. After that +₹21 a day." It warns if the rate is high or the period is over 45 days for MSME suppliers. |
| Chat | The same thread the shop sees, with supplier actions |
| Dashboard | Collections over 14 days, average days to get paid, on-time %, interest received, owed by customer |
| Get paid early | Up to 70% of **accepted, not-overdue** bills can be paid out today by a partner lender (illustrative fee). This is possible only because both sides agreed to the bill – paper udhaar can't be financed. |

---

## 6. The field demo (`demo/`)

A separate, simpler app for showing the idea to shop owners and recording their reactions. It takes about 10 minutes.

1. **Before we begin (interviewer).** Your name, area, the shop owner's name (optional), business type, consent to take part, and consent to record.
2. **See the features.** Eight screens, one feature each:
   - one-tap supplier pay;
   - udhaar written for both;
   - pay in parts;
   - reminders and more time;
   - works if the supplier isn't on Paytm;
   - hisaab done for you;
   - score and credit;
   - supplier side.

   Each screen has a picture, one Hinglish line, a short explanation, and three buttons: **Useful / Not sure / Not for me**, plus a note box for what they said.
3. **Try it yourself.** The app starts **empty**. The shop owner:
   - names their shop;
   - adds their real suppliers (what they supply, how they pay them today, credit days);
   - adds one udhaar (amount, when goods came, interest-free days, interest if late).

   The app then builds *their* Vyapaar Pay. They are asked to pay part of a bill, ask for more days, and see the supplier's view. A checklist ticks these off. Example data is available if they don't want to share.
4. **Feedback.** Would they use it; most useful parts; anything confusing; would their supplier agree; is agreed interest fair; would they share data for credit; what could stop them; ease (1–5); a verbatim quote. An interviewer-only section records how each task went (alone / with help / couldn't / skipped) and notes.
5. **Saved.** A summary screen. All sessions are listed under **Saved sessions** and download as **CSV** (one row per session, 52 columns) or **JSON**.

The demo also has a "How to run a session" guide with what to say in Hindi.

---

## 7. What is real and what is simulated

| Real in the prototype | Simulated |
|---|---|
| All screens, flows and calculations: interest, part payments, due dates, forecast, score | Payments, UPI PIN, NEFT, Soundbox and WhatsApp messages |
| Data saved on the device; demo answers can be downloaded | Lenders, rates, credit offers and Key Fact Statements – all illustrative |
| | The supplier's replies in some flows (for example, agreeing to more days) arrive automatically after a moment |

---

## 8. Design principles

1. **Simple first.** One main action per screen. Big amounts, plain words, Hinglish where it helps.
2. **Both sides see the same truth.** No "I never agreed to that".
3. **No surprises.** Interest only on accepted terms, fees shown upfront, data shared only with consent.
4. **No pressure, no comparisons.** The app never tells people to stop using another app. It makes paying suppliers and keeping records easier, and the habit follows.
5. **Works with how India pays today.** Cash, cheques, other UPI apps and suppliers not on Paytm are all handled.
