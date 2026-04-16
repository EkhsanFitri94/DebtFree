# DebtFree

DebtFree is a client-side CTOS smart debt settlement planner that helps model written-off accounts, full and final settlements, trade defaults, and active loan strategies.

## Run Locally

Open `index.html` in any modern browser.

No backend is required. All processing stays inside your browser.

## Features

- Income, commitments, debt wizard
- CTOS-oriented debt status handling
- Private local CTOS JSON upload (manual file selection)
- Avalanche and snowball strategy comparison
- Interactive Chart.js timeline and payment breakdown
- Print-ready report
- Client-side only (no backend)

## Upload CTOS Data (Private)

Use the Upload CTOS Data button in Step 3 and choose a local PDF, JSON, or CSV file.

After parsing, DebtFree shows an import preview first. You can edit status/amount fields or remove rows, and data is only applied after you click Apply Imported Data.

If you need to wipe imported debt/profile values quickly, use the Clear Imported Data button in Step 3.

Optional: enable Remember this device if you want the app to keep your draft locally in your browser. It stays off unless you turn it on.

Supported top-level formats:

- An array of debt objects
- Or an object with `debts` plus optional `profile`
- Or CSV with a header row
- Or CTOS PDF (heuristic text extraction)

Example:

```json
{
	"profile": {
		"salary": 3500,
		"savings": 1500,
		"commitments": {
			"rent": 800,
			"utilities": 150,
			"food": 600,
			"transportation": 200,
			"phone": 80,
			"insurance": 0,
			"other": 100
		}
	},
	"debts": [
		{
			"name": "CIMB Personal Financing 1",
			"status": "written-off",
			"outstanding": 1100,
			"lender": "CIMB"
		},
		{
			"name": "Car Loan",
			"status": "active",
			"outstanding": 22000,
			"interestRate": 4.2,
			"minPayment": 540
		},
		{
			"name": "Old Card Account",
			"status": "ffs",
			"outstanding": 9000,
			"ffAmount": 4200,
			"ffDeadline": "2026-09-30"
		}
	]
}
```

Status values accepted: `active`, `written-off` (or `wo`), `ffs`, `trade`, `family`, `other`.

CSV columns supported (case-insensitive):

- `name` or `debtName` or `account`
- `status`
- `outstanding` or `balance`
- `interestRate`, `minPayment` (for active debts)
- `ffAmount`, `ffDeadline` (for F&F debts)
- `lender` or `creditor`

Optional profile columns in CSV (read from first valid row):

- `salary`, `savings`
- `rent`, `utilities`, `food`, `transportation`, `phone`, `insurance`, `other`

Minimal CSV example:

```csv
name,status,outstanding,interestRate,minPayment,lender
CIMB Personal Financing 1,written-off,1100,0,0,CIMB
Car Loan,active,22000,4.2,540,Maybank
Old Card Account,ffs,9000,0,0,Public Bank
```

PDF notes:

- PDF parsing runs fully in your browser and does not upload your file.
- CTOS PDFs can vary in layout. If extracted rows are incomplete, use CSV or JSON for full control and accuracy.

## Author

Muhammad Ekhsan Fitri bin Zamrus

## License

MIT
