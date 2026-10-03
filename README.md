# Credigo

Credigo is a frontend-only financial-product discovery marketplace. It keeps the original project's cooperative-banking and inclusive-credit infrastructure story while adding a consumer journey to explore, calculate, check indicative eligibility, and submit an application request.

## Run locally

For the full clean-path experience, serve this folder with any static HTTP server and open its local URL. For example, with Python installed:

```powershell
python -m http.server 8000
```

The site is a dependency-free HTML/CSS/JavaScript single-page application. It can also be opened directly as `index.html`; in that case, routes use `#/credit-cards` hash URLs so navigation does not try to open route names as files. `vercel.json` rewrites direct product URLs to `index.html`, so nested paths also load after refresh on Vercel.

Transparent Credigo logo variants are stored in `assets/logo/`: the dark wordmark is used on the light header and the white wordmark is used in the dark footer.

## Main routes

- `/` - marketplace home
- `/credit-cards` - card catalogue, bank directory, search and filters
- `/credit-cards/:bank` - cards for a selected bank
- `/credit-cards/:bank/:card` - card details
- `/credit-cards/find` - preference questionnaire
- `/personal-loans`, `/business-loans`, `/home-loans`, `/gold-loans` - lender discovery and calculators/estimates
- `/emi` and `/iphone-on-emi` - illustrative purchase-financing estimates
- `/platform` - Credigo's separate cooperative-banking credit infrastructure concept
- `/eligibility` - indicative product discovery (not an approval or credit check)
- `/apply` - product-aware handoff to Credigo's Google Form
- `/application-status` - guidance on using the confirmation from Google Forms or the provider
- `/about` and `/faq` - Credigo context and product guidance

The Credigo Assistant is available throughout the site. It searches the existing card and loan data, answers product questions, summarizes listed card differences in chat, and calculates illustrative EMI estimates locally in the browser. It does not use an AI API or send chat messages to a server.

Product application buttons open Credigo's Google Form in a new tab. Product details are not prefilled or transmitted by the website; the form is the application submission flow.

## Demo data and privacy

Credit-card product information is stored on each card record in the `creditCards` dataset in the inline application script. Catalogue and card-detail views read the same fields. Source references and review metadata are stored with each record; unavailable card-specific values are shown as "Information not available" rather than inferred. Product fees, benefits, eligibility and availability can change, so confirm current terms with the issuer before applying. Example provider listings do not imply a partnership.

Calculators and chatbot EMI estimates are illustrative only. The eligibility flow is not a credit-bureau check and cannot approve an application. Credigo Assistant chat history is stored in the browser's local storage. Application information is entered and submitted directly through the Google Form; the website does not collect it or transmit it to a lender.
