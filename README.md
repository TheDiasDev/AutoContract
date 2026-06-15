# AutoContract

An automatic service contract generator. Fill out a short form with the details that change from client to client, review the fully formatted contract on screen, and export it as a ready-to-sign PDF.

Originally built for **Studio LR Makeup & Beauty** ("Bridal Day" contracts), but the structure works as a base for any freelancer who reuses the same contract template and only changes a few details per client.

## How it works

The flow has three steps:

1. **Form** — client details, event details, and package/pricing.
2. **Preview** — the full contract is assembled and shown on screen, identical to the PDF output, for review before generating the document.
3. **PDF** — once confirmed, the contract is exported as a PDF (selectable text, not an image), with an automatic filename (`Contrato_DiaDaNoiva_ClientName_EventDate.pdf`).

## Fixed vs. variable content

About 80% of the contract is standard boilerplate (cancellation clauses, jurisdiction, late fees, service provider details, payment information), and stays fixed in the code. The variable fields filled in through the form are:

- Client's full name, CPF (optional), and RG (optional)
- Client's address
- Event date, time, and location
- Package name and list of included services (editable line by line)
- Total price and deposit/down payment (auto-suggests 15%, adjustable)
- Notes on payment method
- Additional notes
- Contract date

The amount written in words (e.g. "two thousand six hundred and sixty reais") and the remaining balance are calculated automatically.

## Usage

1. Open `gerador-contrato-dia-da-noiva.html` in any browser (no installation or server required).
2. Fill out the form.
3. Click **Gerar contrato** to preview.
4. Click **Confirmar e gerar PDF** to download the document.

## Customization

The service provider's fixed details (name, RG, CNPJ, address, PIX key, phone) are stored in the `CONTRATADA` constant at the top of the `<script>` tag in the HTML file. To adapt the project to a different provider or service type:

- Edit the `CONTRATADA` constant with the new provider's details.
- Adjust the clause text inside the `buildContractParagraphs()` function for the new type of service.
- Replace the default service list in `PACOTE_DIAMANTE` with the new business's default package.

## Tech stack

- Plain HTML, CSS, and JavaScript (no build step, no install dependencies)
- [jsPDF](https://github.com/parallax/jsPDF) (via CDN) for PDF generation

## License

MIT — see [LICENSE](LICENSE).
