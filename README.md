# Credigo

Credigo is a frontend-only financial-product discovery marketplace. It keeps the original project's cooperative-banking and inclusive-credit infrastructure story while adding a consumer journey to explore, compare, calculate, check indicative eligibility, and submit an application request.

## Run locally

For the full clean-path experience, serve this folder with any static HTTP server and open its local URL. For example, with Python installed:

```powershell
python -m http.server 8000
```

The site is a dependency-free HTML/CSS/JavaScript single-page application. It can also be opened directly as `index.html`; in that case, routes use `#/credit-cards` hash URLs so navigation does not try to open route names as files. `vercel.json` rewrites direct product URLs to `index.html`, so nested paths also load after refresh on Vercel.

Transparent Credigo logo variants are stored in `assets/logo/`: the dark wordmark is used on the light header and the white wordmark is used in the dark footer.

## Main routes

- `/` — marketplace home
- `/credit-cards` — card catalogue, bank directory, search and filters
- `/credit-cards/:bank` — cards for a selected bank
- `/credit-cards/:bank/:card` — card details
- `/credit-cards/compare` and `/credit-cards/find` — comparison and preference questionnaire
- `/personal-loans`, `/business-loans`, `/home-loans`, `/gold-loans` — lender discovery and calculators/estimates
- `/emi` and `/iphone-on-emi` — illustrative purchase-financing estimates
- `/platform` — Credigo's separate cooperative-banking credit infrastructure concept
- `/eligibility`, `/apply`, `/application-status` — frontend-only enquiry flows
- `/about` and `/faq` — Credigo context and product guidance

## Demo data and privacy

Product names are structured in the datasets near the top of the inline application script. Product fees, rates, benefits, eligibility and provider availability change; where values are not maintained and verified, the interface directs users to check current provider terms. Example provider listings do not imply a partnership.

Calculators are illustrative only. The eligibility flow is not a credit-bureau check and cannot approve an application. Application submissions and card comparison selections are stored in the browser's local storage; no backend request is made and no application data is transmitted to a lender.
