# 03 · Payments & Legal

**Main finding:** WedajMart should never hold customer money itself. It should use a licensed gateway (e.g. Chapa) with split payments, register as an e-commerce operator, follow the consumer disclosure rules, store personal data in Ethiopia, and drop social-account trading and equb.

> This is research, not legal advice. Confirm each point with an Ethiopian lawyer before taking payments.

## Payment rails available

| Option | What it gives you | Notes |
| --- | --- | --- |
| **telebirr** | The most widely used wallet (~57M subscribers) | Merchant/mini-app integration via Ethio Telecom; also the rail Zemen Gebeya runs on ([EBR](https://ethiopianbusinessreview.net/?p=17563), [Shega](https://mediav3-dev.shega.co/news/ethio-telecom-transforms-mobile-money-platform-telebirr-into-super-app)) |
| **CBE Birr** | 34.2M users | Bank wallet of the Commercial Bank of Ethiopia |
| **Chapa** (gateway) | One integration for telebirr, CBE Birr, M-Pesa, banks and cards; NBE gateway licence since 2022 | **Split payments:** each seller gets a subaccount and the platform takes a commission per transaction (percentage or flat), so the platform never holds seller money ([Chapa docs](https://developer.chapa.co/integrations/split-payment)). Onboarding needs a trade licence, TIN and business bank account. Published fees vary by source (about 1.5–3.5%), so confirm directly ([Shega launch](https://shega.co/news/chapa-officially-launches-payment-gateway-service), [third-party guide](https://zirzir-docs.pages.dev/providers/chapa)). |
| **Other gateways** | ArifPay, SantimPay and similar | Compare fees, settlement time and diaspora card support |
| **Cash on delivery** | Still the most trusted option for many buyers | Works for an Addis pilot; the courier collects |

### Why not run your own "Adera Escrow"

- Issuing or holding e-money is a licensed activity under the **NBE Licensing and Authorization of Payment Instrument Issuers Directive** (ONPS/01/2020, replaced by ONPS/09/2023, amended by ONPS/10/2025) ([Digital Policy Alert](https://digitalpolicyalert.org/event/25646-implemented-nbe-licensing-and-authorisation-of-payment-instrument-issuers-directive-no-onps092023), [Fana](https://www.fanabc.com/english/?p=4619)).
- Minimum paid-up capital is **ETB 50 million**, held in a blocked account, plus security audits and a 6–9 month pilot before a full licence ([DM Ethio Lawyers](https://dmethiolawyers.com/?p=3087), [RegAlert](https://regalert.today/document/410e68b4-fd2a-49e0-baef-825bfca43ba7/text)).
- Zemen Gebeya can offer escrow because it sits on telebirr. A startup gets the same effect, legally, by holding funds with a licensed gateway or bank and releasing on delivery confirmation.

**Wording on the site:** don't call it "WedajMart Escrow Vault". Say "Payments processed and held by [licensed partner] until you confirm delivery."

## E-commerce law

**Electronic Transaction Proclamation No. 1205/2020** ([Reporter commentary, Jun 2026](https://www.thereporterethiopia.com/51498/), [Shega resource](https://digitalfinance.shega.co/resource/policy-and-regulations/policy-and-regulation-7)):

- **Before a sale, disclose:** seller identity and address, total price including taxes and fees, product description, delivery time, refund/return policy, payment methods, privacy policy, and dispute process.
- **Order review:** buyers must be able to check, correct and withdraw an order before confirming.
- **Withdrawal rights:** 14 days if disclosure rules weren't met; 7 days to return without cause (buyer pays return cost).
- **Delivery:** within 30 days unless agreed otherwise; refund unavailable items within 7 days.
- **Payment security:** the supplier is liable for harm from an insecure payment system.
- **Platforms must verify sellers'** identity, address and legitimacy.
- **Local content:** at least 50% of products/services offered should be local. This suits a platform built around Ethiopian goods.
- The commentary notes enforcement is weak ("a framework waiting to be applied"), but a funded or partnered business should comply from day one.

**Licensing:** Register and license through the Ministry of Trade's online system ([DM Ethio Lawyers on OTRIS](https://dmethiolawyers.com/?p=1984)). Most "e-commerce" licences so far are service-provider (commission/delivery) licences rather than full platform licences ([Addis Fortune 2023](https://addisfortune.news/unlicensed-e-commerce-sites-prompt-timid-digital-world), [Addis Fortune 2024](https://addisfortune.news/online-market-thrives-during-festive-season)). Ask a lawyer which category fits the chosen model. A TIN is expected for e-commerce operators.

## Data protection

**Personal Data Protection Proclamation No. 1321/2024**, in force since 24 July 2024 ([Mondaq guide](https://www.mondaq.com/privacy-protection/1766200/ethiopian-personal-data-protection-law-proclamation-13212024-business-compliance-guide), [Dablo Law](https://dablolawfirm.com/ethiopia-enacts-personal-data-protection-proclamation-no-1321-2024/), [Digital Policy Alert](https://digitalpolicyalert.org/event/24922-implemented-personal-data-protection-proclamation-proclamation-no-13212024-including-data-localisation-requirements)):

- Applies to any controller or processor established in Ethiopia, wherever the processing happens.
- **Data localization:** locally collected personal data should be stored on servers in Ethiopia. The prototype's database is in London; plan to move customer data to a local host or get legal advice on the transfer conditions.
- Collect only the data you need; publish a privacy policy; get consent.
- Regulator: the Ethiopian Communications Authority.

## Foreign exchange (relevant for diaspora sales)

- The birr was floated in **July 2024**; exporters no longer have to surrender all FX, and remittance receivers can hold FX accounts ([Semafor](https://www.semafor.com/article/07/29/2024/ethiopia-floats-birr-to-stabilise-economy), [Shega](https://shega.co/news/ethiopian-currency-regime-overhaul-opens-new-frontiers-for-fintechs-amid-market-uncertainty)).
- Diaspora card payments are easier than before, but FX rules still apply to how foreign-currency revenue is received and converted. Confirm the setup with the payment gateway and your bank.

## Platform rules

- **TikTok, Instagram and YouTube** terms prohibit selling or transferring accounts; sold accounts are regularly banned ([summary](https://handles.gg/blog/is-buying-social-media-account-legal-2026-guide), [Climb the Ladder](https://climbtheladder.com/can-you-sell-a-tiktok-account-risks-and-steps/)). The "Escrow Accounts" section should be removed.
- **Equb / savings circles** and **group-buying pools** that hold members' money are financial activities; don't run them without a licensed partner.

## Compliance checklist before taking real money

- [ ] Business registered, trade licence in the right category, TIN
- [ ] Payments through a licensed gateway (split payments), no money held by WedajMart
- [ ] Seller verification (ID, address, trade licence where applicable)
- [ ] Product pages show full price, delivery time, return policy, seller identity
- [ ] Terms of use, privacy policy, refund and dispute policy published in Amharic and English
- [ ] Customer data hosted in Ethiopia (or legal sign-off on the transfer)
- [ ] Social-account trading, equb and fake reviews removed
- [ ] One paid hour with an Ethiopian commercial lawyer
