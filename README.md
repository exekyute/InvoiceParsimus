# 🏛️ InvoiceParsimus

**A private, browser-based invoice parser and financial dashboard.**

InvoiceParsimus lets you drag and drop PDF invoices or scanned images directly into your browser. It reads the document using machine vision (OCR), pulls out the key financial details automatically, and organizes everything into a sortable, filterable ledger. No accounts. No uploads. No server. Everything runs locally on your machine.

## 🔍 What It Does

Drop a PDF or image invoice into the app and it will try to extract:

- **Date** (normalized to DD-MM-YYYY)
- **Vendor name**
- **PO Number** (scans for labels like "P.O.", "Purchase Order", "PO #")
- **Invoice Number** (scans for labels like "Invoice #", "Inv No")
- **Subtotal, Tax (GST/HST/VAT), and Total**

If the scanner cannot find a specific field, it marks it as **N/A** with a small icon you can hover over that reminds you to review it manually. Nothing gets silently dropped.

## ✨ Features

**Invoice Table**
- Eight columns: Date, Vendor, PO #, Invoice #, Description, Subtotal, Tax, Total
- Click any column header to sort ascending, descending, or back to default
- Type in the filter row under each header to narrow results by substring. This works on dollar amounts too (typing "24" will match $24.25 and $124.50)
- A sticky totals row at the bottom of the table always shows the sum of whatever is currently visible. If you filter down to three vendors, the totals reflect only those three.
- A "Clear Sort/Filter" button resets everything back to default in one click

**Dashboard Cards**
- Four summary cards at the top: Total Invoiced, Total Tax, Processed count, and Unique Vendors
- These update in real time as you apply filters, so the numbers always match what is visible in the table

**Charts**
- Spend Timeline (line chart): shows monthly spend over time. Range toggles let you scope it to 1 Month, 3 Months, 6 Months, YTD, 1 Year, or All time
- Vendor Distribution (pie chart): shows each vendor's share of total spend with the name and percentage labeled directly on each slice, always visible without needing to hover

**Mock Data**
- An "Insert Mock Invoices" button loads six sample vendor rows so you can explore the dashboard without needing real documents. Each click adds another six rows on top. A collapsible amber warning appears to remind you the data is fake and to refresh the page before loading real invoices.

**Export**
- One-click CSV export covering all parsed invoices. Opens as a downloadable file ready to import into Excel or accounting software.

**Privacy**
- Everything runs inside your browser. No files, no invoice data, and no financial information ever leaves your device or gets sent to a server. The OCR engine (Tesseract.js) runs entirely client-side.

## 🚀 Live Demo

[**Launch InvoiceParsimus**](https://exekyute.github.io/InvoiceParsimus/)

## 💡 How to Use

1. Open the live dashboard link above (or open `index.html` directly in your browser).
2. Drag and drop a PDF invoice or image file into the drop zone, or click the zone to browse for a file.
3. Wait a few seconds while the OCR engine scans the document locally.
4. The extracted data populates the table automatically. Any fields that could not be found will show as N/A.
5. Use the column filters, sort headers, and range toggles to explore your data.
6. Click **Export CSV** when you are ready to take the data elsewhere.

## ⚠️ Current Limitations

**Invoice layouts vary a lot.** The scanner uses pattern-matching to hunt for keywords like "Subtotal", "Amount Due", and "Invoice #". If your invoice puts these labels in unusual spots or leaves them out entirely, some fields may come back as N/A and need a quick manual fill-in.

**Stylized fonts can trip up OCR.** Tesseract works best on clean, standard text. Heavily branded headers or decorative fonts in logos may not scan cleanly.

**It is built to be private, not powerful.** The reason this app does not use a cloud AI to extract data is simple: doing that would require an API key sitting in the source code, which anyone could read and misuse. The current approach keeps your invoices and your credentials safe by never involving a server at all. The tradeoff is that the pattern-matching engine is more rigid than an AI would be.

## 🗺️ Future Roadmap

**Gemini AI Integration (session-only)**

A button will open a small pop-up where you can paste in your personal Gemini API key. Once entered, the key exists only in the browser's memory for the current session. The moment you close the tab or refresh the page, it is gone completely. It is never written to a file, never stored in the browser, and never transmitted anywhere except directly to the Gemini API to process your document text. This is intentional and is the core privacy guarantee of this feature.

Once the key is active, the app will run the OCR text through Gemini alongside the existing pattern-matching engine. The goal is for them to work together: the regex engine is fast and reliable for standard fields, and Gemini steps in to fill the gaps it misses (a vendor name in an unusual position, a PO number in an unexpected format, etc.). Neither replaces the other.

**Custom PO Number Format**

A settings button will open a dialogue box (similar to the Gemini token pop-up above) where you can tell the app how your organization formats PO numbers. For example, if every PO your company issues is exactly 10 digits long, you can enter "10" and the app will specifically scan for 10-digit sequences when looking for a PO number. This helps avoid false positives (like a phone number being mistaken for a PO) and will also be passed as context to Gemini once that integration is live.

## 💻 Tech Stack

| Tool | What it does |
|---|---|
| HTML5 + Vanilla JavaScript | All logic and structure, no framework needed |
| Tailwind CSS (CDN) | Styling and layout |
| PDF.js (CDN) | Reads PDF files in the browser |
| Tesseract.js (CDN) | Runs OCR locally to extract text from documents |
| Chart.js + datalabels plugin (CDN) | Powers the spend timeline and vendor distribution charts |
