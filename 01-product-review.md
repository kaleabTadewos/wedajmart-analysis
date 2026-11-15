# 01 · Product Review

Tested 14 November 2026 on the preview build, in a desktop browser (1024px wide) and at iPhone size (375px).

## What the system is

WedajMart (ወዳጅ ማርት) is a web app styled like Amazon. It presents itself as an "Ethiopia & Diaspora unified platform" with six core services:

| # | Service | What it promises |
| --- | --- | --- |
| 1 | Retail & artisans | Habesha kemis, coffee, leather, electronics, with "2-hour Addis Express" delivery |
| 2 | Second-hand exchange | Used phones, laptops and cameras with /10 condition scorecards and trade-in |
| 3 | Channel escrow vault | Buying and selling Telegram channels, TikTok, YouTube and Instagram accounts |
| 4 | Communities & academy | Creator-led classes (import business, AI, digital growth) |
| 5 | Instant downloads | Ge'ez fonts, e-books, music beats and stems |
| 6 | Creator tools & ads | "Buna tips" for creators, Meta ads paid in Birr |

There are also: Wedaj Video, Live Shopping, Community Wall, AI Listing Studio, gift cards, coupons, wholesale/B2B, a seller dashboard, a currency converter (ETB, USD, EUR, GBP, AED), and browser storage for **equb circles**, **group-buying pools** and gift cards.

### How it's built (observed from the browser)

- Built and hosted with **Google AI Studio** on Google Cloud Run (the `ais-pre-…run.app` address). The internal project name is "arifmartethiopia", so the product seems to have been renamed from ArifMart.
- Data lives in **Google Firebase Firestore**, a cloud database. Exchange rates come from a public API. A Telegram script is loaded.
- Products, reviews, sales numbers and seller stats are **demo data**. The seller page shows "1,340,820 Br total sales, 428 orders", and the reviews are written as if by verified buyers.
- Much of the state (search history, gift cards, equb circles, group pools) is kept in the visitor's browser, not in a shared backend.
- The app is one page with no routing: the address never changes as you move around.

This is a good, fast prototype. It is not yet a system that can take real orders: there are no real payments, accounts, seller onboarding or order handling behind it.

## Bugs and UX fixes

All of the handwritten review notes checked out. My additions are marked **(new)**.

| Priority | Issue | What I saw | Fix |
| --- | --- | --- | --- |
| High | Browser Back button does nothing useful | The URL never changes, so browser history stays at 1 entry. Back exits the site, refresh loses your place, and product links can't be shared. | Add routing: one URL per page (`/product/kemis-123`, `/search?q=coffee`). The in-page "Back to Results" link does work. |
| High | "See all" / "See more" links are dead | "See all top rated" did nothing when clicked. | Link each to a filtered results page, or remove it. |
| High | Recent Searches shows fake history | Shows "TikTok Monetized Accounts", "Addis Tech Telegram" before the user has searched anything. | Show only the user's own searches; put "Popular in Addis" in a separate list. |
| High | Amharic search is weak | "coffee" → 6 results, "ቡና" → 5. Amharic only matches products that happen to have Amharic text. | Store Amharic name, English name and common spellings (kemis / qemis / ቀሚስ) for every product; search all of them. |
| High | Header language switch does nothing **(new)** | Clicking EN in the header opens no menu. Only a footer selector exists. | One working toggle, remembered per user. |
| High | Amharic and English mixed everywhere | Labels and headings switch language mid-page. | One interface language per user; keep product names in both scripts. |
| High | Fake traction on the seller page **(new)** | "Hundreds of thousands of shoppers", "428 orders this month", "join hundreds of thriving artisans". | Remove before showing to real sellers or investors; it reads as misleading. |
| Medium | Wrong product photos **(new)** | Kemis gallery shows a "SALE" banner and a coffee bag; Mesob card shows a wristwatch; Shemane shirt shows a man in a suit. | Real seller photos only. |
| Medium | Filter counts don't match results **(new)** | A "coffee" search lists "Clothing & Kemis (4)" and "Tech & Electronics (4)". | Compute counts from current results. |
| Medium | Header breaks at laptop widths | At 1024px the search box shrinks to a few characters wide. | Test at 1024 / 1280 / 1440px, including Mac Safari. |
| Medium | Home cards should open the product | Quick "Add to cart" skips size, photos and seller info. | Whole card opens the product page; keep quick-add only for items without options. |
| Medium | Heavy for mobile data **(new)** | About 5 MB of JavaScript; photos still blank after 3 seconds at phone size. | Split code per page, compress images. Most buyers pay per MB. |
| Medium | Data stored outside Ethiopia **(new)** | The database is hosted in a London (europe-west2) region. | Ethiopia's data protection law requires local storage of locally collected personal data; see [03-payments-and-legal.md](03-payments-and-legal.md). |
| Low | Pop-up overload | Location pop-up, welcome banner and install prompt all appear at once. | Show one, later. |
| Low | Fake reviews | Every product rated 4.7–5.0; one review appears twice. | Remove before launch. |

## Page-by-page feedback

| Page | What's good | What I'd change |
| --- | --- | --- |
| Overall look & brand | Clean, professional; the Ge'ez ወዳጅ tag is a nice touch. | It copies Amazon almost one-for-one (logo arrow, "Hello, sign in", "Returns & Orders"). That invites a trademark complaint and hides its own identity. Build a look from Ethiopian colours, tibeb patterns and coffee culture. |
| Home | Category tiles are clear. | The same ~10 products repeat across 5 rows. Lead with one promise, then 2–3 rows. |
| Product page | The best page: bilingual title, Birr + USD price, telebirr/CBE Birr badges, voice and video reviews. | Add a size guide and made-to-measure for kemis, real multi-angle photos, seller location and response time. Move "Bargain with Seller" up; it fits local habits. Remove "AI Virtual Try-On" until it works. |
| Search results | Good filters and sort; Amharic subtitles. | Fix Amharic matching and counts; 2-column grid on phones; sub-city filter (Bole vs. Merkato). |
| Cart | Instant add with confirmation. | Show delivery fee and total before checkout. |
| Used Goods | Most differentiated idea: condition grading, defect disclosure, trade-in. | Show who inspects, where, and a sample scorecard. Without real inspection, it's just Jiji. |
| How It Works | Clear 3-step story and buyer / seller / creator paths. | It explains six businesses at once; a newcomer can't tell what WedajMart is for. |
| Seller Central | Fee calculator and 3-step onboarding are well designed. | Remove fake stats and promises ("instant payouts", "2-hour delivery") that can't be kept yet. |
| Escrow Accounts | Clear 4-step flow. | Remove it. Selling TikTok/Instagram/YouTube accounts breaks those platforms' rules. |
| Video, Beats, Academy, Live, AI Studio, Equb, Group pools | Show technical skill. | Hide them. Equb (rotating savings) also touches regulated financial services. |
| Phone view | Header and search fit well; no sideways scroll. | Make it lighter and faster. |

## Bottom line

As a design prototype it is strong. As a business it needs three things before anything else: **focus** (one service), **real data** (real sellers, photos, prices), and **real plumbing** (accounts, payments through a licensed gateway, orders, delivery). See [04-strategy-options.md](04-strategy-options.md).
