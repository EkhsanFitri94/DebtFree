# DebtFree

DebtFree is a client-side CTOS smart debt settlement planner that helps model written-off accounts, full and final settlements, trade defaults, and active loan strategies.

## Run Locally

Open `index.html` in any modern browser.

No backend is required. All processing stays inside your browser.

## Features

- Income, commitments, debt wizard
- CTOS-oriented debt status handling
- Private local CTOS PDF upload (manual file selection)
- Live auto-refresh on the results screen when you edit data
- Optional age-at-settlement preview using date of birth
- Avalanche and snowball strategy comparison
- Interactive Chart.js timeline and payment breakdown
- Print-ready report
- Client-side only (no backend)

## Upload CTOS Data (Private)

Use the Upload CTOS Data button in Step 3 and choose a local CTOS PDF file.

After parsing, DebtFree shows an import preview first. You can edit status/amount fields or remove rows, and data is only applied after you click Apply Imported Data.

If you need to wipe imported debt/profile values quickly, use the Clear Imported Data button in Step 3.

Optional: enable Remember this device if you want the app to keep your draft locally in your browser. It stays off unless you turn it on.

You can also export a private backup JSON file and import it on another device. This does not require local storage.

Supported input:

- CTOS PDF (heuristic text extraction)

For portable JSON backup and restore, use the Export Backup and Import Backup buttons instead.

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

PDF notes:

- PDF parsing runs fully in your browser and does not upload your file.
- CTOS PDFs can vary in layout. If extracted rows are incomplete, edit the preview rows before applying them.
- The PDF parser is tuned for common labels such as Written-Off, F&F/Settlement, Trade Default, Active, Current, and Good Standing.

## Author

Muhammad Ekhsan Fitri bin Zamrus

## License

MIT
