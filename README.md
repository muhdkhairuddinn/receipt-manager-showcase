# Receipt Manager

Snap a receipt, check the amount, claim at the end of the month. A small mobile-first web app I built for fun because I got tired of a pile of paper receipts. It started on free hosting, and now it runs on my own server.

<p align="center"><img src="docs/hero.png" alt="Dashboard, receipt list and receipt detail" width="760"></p>

> Showcase repo: screenshots and notes only. The source code is private, and everything in the screenshots is fake demo data.

## Why I made it

Claiming expenses meant keeping paper receipts, typing amounts into a spreadsheet at month end, and exporting PDFs by hand. I wanted to do it in a few taps from my phone while the receipt is still in my hand. So I built it, and it turned into a fun side project that I keep improving.

## What it does

- **Snap or upload receipts**, one or many at once, from the camera, the gallery, or the Android share sheet.
- **Reads the receipt for you.** The server runs OCR (software that reads text from images) and suggests the total and the date. If the server cannot read the image, the browser tries on its own. You always confirm before anything is saved.
- **Picks Lunch or Dinner from the time printed on the receipt**, so you do not have to tap it every time.
- **Digital PDF receipts too**, like a bank or e-wallet payment PDF. The PDF is read in your browser and never leaves your phone.
- **Claim rules built in:** a meal claim is capped per meal, and one claim per month goes out.
- **Monthly dashboard** with total claimed, a Food and Petrol split, and a six month trend. Tap a bar to jump to that month.
- **Receipt archive** with search, category filter and a month picker. A warning shows up if the same receipt is added twice, but a lunch and a dinner on the same day are fine.
- **Exports** for the month: claim PDF, claim Excel and a PDF of the receipt photos, grouped by date.
- **Claim history**, so the same month does not get submitted twice, and a one-tap send to the company expense portal.
- **Works on bad signal.** Failed uploads wait on the phone and send when the connection is back.
- **Admin page.** There is no public sign-up. An admin creates accounts, resets passwords and can log someone out or disable them.

## Screens

| Dashboard | Receipts | Receipt detail |
| --- | --- | --- |
| <img src="docs/dashboard.png" alt="Dashboard" width="230"> | <img src="docs/receipts.png" alt="Receipts" width="230"> | <img src="docs/detail.png" alt="Detail" width="230"> |

| Add a receipt |
| --- |
| <img src="docs/upload.png" alt="Add a receipt: the date, amount and Dinner are filled in from the photo" width="230"> |

The receipts in these screenshots are made-up samples, and the names are fake.

## Built with

- **Frontend:** Next.js 16, React, TypeScript, Tailwind CSS
- **Backend:** FastAPI (Python)
- **OCR:** RapidOCR on the server, tesseract.js in the browser as a backup
- **Data:** PostgreSQL, with every query limited to the signed-in user's own receipts
- **Exports:** ReportLab (PDF) and openpyxl (Excel)
- **Hosting:** my own Linux server, with Docker containers and Caddy in front for HTTPS. It moved here from free hosting tiers.
- **Alerts:** Telegram messages for new receipts and server problems

Made by **KH4I**
