# Receipt Manager

A mobile-first web app for keeping work expense receipts and turning them into a monthly claim. Snap a receipt, check the amount, and export the month when it is time to claim.

![Dashboard, receipt list and receipt detail](docs/hero.png)

> This repository is a showcase: screenshots and notes only. The source code is private. All data in the screenshots is demo data.

## Why I built it

Claiming expenses meant keeping a pile of paper receipts, typing amounts into a spreadsheet at month end, and exporting PDFs by hand. I wanted to do that part in a few taps from my phone, when the receipt is still in my hand.

## What it does

- **Snap or upload receipts**, one or many at a time. The date and time are read from the photo.
- **Reads the total for you.** OCR runs in the browser, crops to the paper area first so dark backgrounds do not confuse it, and fills in the amount for you to confirm.
- **Monthly dashboard** with total claimed, a Food and Petrol split, and a six-month trend. Tap a bar to jump to that month.
- **Receipt archive** with search, category filter and a month picker.
- **Exports** for the month: claim PDF, claim Excel and a PDF of the receipt photos.
- **Claim history**, so a month that was already submitted is not submitted twice.
- **Works on a weak connection.** Uploads that fail are queued on the phone and sent when the signal returns.
- **Share to the app** from the phone gallery or WhatsApp (Android).

## Screens

| Dashboard | Receipts | Receipt detail |
| --- | --- | --- |
| ![Dashboard](docs/dashboard.png) | ![Receipts](docs/receipts.png) | ![Detail](docs/detail.png) |

## Built with

- **Frontend:** Next.js, React, TypeScript, Tailwind CSS, tesseract.js (in-browser OCR)
- **Backend:** FastAPI (Python)
- **Data and auth:** Supabase (Postgres, Auth with email and Google sign-in, Storage) with row-level security, so each user only sees their own receipts
- **Hosting:** Vercel (frontend), Render (API), GitHub Actions for scheduled health checks

## What I learned

- OCR on phone photos fails for odd reasons. A dark table around the receipt made the engine return nothing at all, and cropping to the paper fixed it. I benchmarked the options instead of guessing.
- Reading from the database directly in the browser, and keeping the last result on screen while the fresh one loads, made the app feel much faster than waiting for a free-tier server to wake up.
- Making a "submit" action safe to retry matters more than making it fast: block duplicates, resume half-finished work, and show a clear message when a login has expired.

## Contact

Built by Muhd Khairuddin. [GitHub](https://github.com/muhdkhairuddinn)
