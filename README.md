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

Use the `Upload CTOS Data` button in Step 3 and choose a local `.json` file.

Supported top-level formats:

- An array of debt objects
- Or an object with `debts` plus optional `profile`

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

## Author

Muhammad Ekhsan Fitri bin Zamrus

## License

MIT
