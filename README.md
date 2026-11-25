# CTS POS

**An offline-first point-of-sale system for CITY TECH STORE**, a Nigerian shop selling phones, accessories and solar equipment. Cashiers, managers and head office use it. The till keeps selling offline and syncs through a cloud hub when it's back online.

> The code is private (commercial project). Screenshots show sample data, with phone numbers and addresses blurred.

## Main features

- Touch selling, barcode scanning, discounts, held tickets and returns
- Cash, transfer, card, mobile money, split payments and credit sales
- 80 mm and 58 mm thermal receipts, A4 invoices and a solar quotation flyer
- IMEI tracking from delivery to sale to return, with warranty lookup
- Stock, suppliers, purchasing, customers and loyalty points
- Staff PIN logins, roles, manager approval, shifts and an audit log
- Branches, stock transfers, reports and a head-office view
- Website orders packed and handed over at the till

## Tech stack

- **Desktop app:** Python 3.13, PySide6 (Qt), SQLite
- **Printing:** ESC/POS (python-escpos); A4 pages drawn with Qt
- **Sync hub:** FastAPI, SQLAlchemy, MySQL on shared cPanel hosting
- **Tests:** 215 app tests, 62 hub tests and end-to-end scripts

## What I built

I led CTS POS from idea to deployment over 16 phases: I set the requirements, made the product decisions, reviewed and tested every change, and deployed the hub. I built it with Claude Code as an AI pair programmer.

Challenges I solved:

- **Offline-first sync.** The hub numbers every change, so a wrong PC clock never makes a branch miss one, and sending twice changes nothing.
- **No terminal.** The hub runs on shared hosting, loads lazily to fit the process limit, and upgrades its database from the hosting panel.
- **No double-selling.** Website orders hold stock for a limited time. A delivered order becomes one sale, so stock goes down exactly once.
- **Security.** PINs are hashed, risky actions need a manager's PIN, and certificate checks are always on.
- **Speed.** Tested with 5,000 products and about 15,000 sales: a month's dashboard loads in a quarter-second.

## Status

- Built and tested. The shop is switching from sample data to real stock.
- One till per branch for now, and no installer yet (it runs from Python source).
- The website is a separate project. Its hub connection is tested against a simulated website.
- Planned: more import columns (brand, online selling, wholesale and engineer prices).

## Screenshots

**Selling**
![The selling screen with a ticket, product photos and category tiles.](01-selling-screen.png)

**Split payment**
![The payment window with part paid in cash and the rest by transfer.](02-split-payment.png)

**Receipt**
![A paid receipt coming out of an on-screen printer, with a QR code.](03-animated-receipt.png)

**IMEI lookup**
![An IMEI lookup showing a sold phone that is still under warranty.](04-imei-warranty-lookup.png)

**A4 invoice**
![An A4 invoice, part paid in cash and part on credit, with an IMEI.](05-a4-invoice.png)

**Solar quotation**
![A solar quotation flyer with an inverter, materials and the total.](06-solar-quotation-flyer.png)

**Dashboard**
![The monthly dashboard with sales, profit, a daily chart and top sellers.](07-reports-dashboard.png)

**Head office**
![The head office view comparing sales and stock across three branches.](08-head-office-all-branches.png)

**Online orders**
![The online orders screen with three website orders and a Paystack payment.](09-online-orders.png)

