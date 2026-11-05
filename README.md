# Ledger PH — React accounting workspace

React 19, TypeScript, Vite and Lucide. Responsive dashboard with Philippine peso formatting, eight-level account tree, setup modules, linked financial documents, balanced journal posting, financial reports and CSV export.

## Development

Requires Node.js 22+ and the PostgreSQL-backed backend running on port 5080.

```bash
npm ci
npm run dev
```

Vite forwards `/api` requests to the local .NET 10 API. Development server runs on port 5173. `npm run build` checks TypeScript and produces `dist/`. For a deployed build, serve frontend assets and `/api` behind one origin; Vite's development proxy is not included in production output. No credentials belong in Vite environment variables.

## Using the workspace

1. Review the account tree and posting accounts in Chart of Accounts. Create cards, goods/services with GL mappings and document signatory assignments.
2. Create a Purchase Request and link a Purchase Order to it. Both remain nonposting.
3. Create a Sales Invoice or Accounts Payable document. A goods/service selection prepopulates price and default journal lines; review the lines before saving. Amounts and manual GL entries must be checked for accounting suitability.
4. Open a draft and select Post to ledger. Debits and credits must balance and equal the amount. A posted sale/bill can be partially settled with a linked Collection/Disbursement. Settlement lines are entered manually.
5. Inspect the Trial Balance, Balance Sheet, General Ledger and Subsidiary Ledger. Use card filtering for an individual customer's or supplier's subsidiary ledger. Reports include posted entries only; export CSV where needed.

Seed data uses a January 2026 sample accounting period and includes legitimate generic journal patterns. All amounts are PHP. Sample postings intentionally exclude VAT and withholding.

## Important scope

Local prototype, no login or enforced authorization. Module permissions are configuration only, signatory assignments are not electronic approvals, and all connected users can access the ledger. The ATC view explicitly marks the supplied examples unverified: online BIR retrieval was blocked, so the latest official list and rates have **not** been loaded. See the backend README for validation, data persistence and remaining capabilities required for production.

## Downloadable sample

From the sibling backend directory run `python3 scripts/start_sample.py`. It builds this frontend and serves it from the .NET API at localhost port 5080, backed by PostgreSQL. Requires Docker Compose, Python 3, Node.js 22+ and .NET SDK 10.0.403. See the sample archive README for the test walkthrough.
