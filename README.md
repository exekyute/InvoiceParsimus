# 🏛️ InvoiceParsimus

**A private, client-side invoice parsing and financial sorting tool.**

InvoiceParsimus is a lightweight, single-file web application designed to instantly extract key financial data from PDF invoices and raw text. Because it operates entirely within the browser, no financial data is ever uploaded to an external server.

## ✨ Features

* **PDF Extraction:** Leverages `pdfjs-dist` to read and extract text from digital PDF invoices directly in the browser.
* **Regex Processing Engine:** Automatically identifies and extracts critical data points: Date, Vendor Name, Subtotal, Tax (GST/HST/VAT), and Total Amount.
* **Monthly Sorting Matrix:** Automatically categorizes parsed invoices by month, providing a clean, chronological ledger.
* **Interactive Analytics:** Utilizes `Chart.js` to render dynamic visual breakdowns of monthly spend trends and vendor distribution.
* **One-Click Export:** Compiles all processed ledger data into a clean `.csv` file for easy import into accounting software or Excel.
* **Zero-Backend Architecture:** Everything runs locally in your browser tab. Reloading the page wipes the data, keeping your financials completely private.

## 🛠️ Tech Stack

* **HTML5 & Vanilla JavaScript:** Core logic and structure.
* **Tailwind CSS (via CDN):** For a responsive, dark-mode fintech UI.
* **PDF.js (via CDN):** For client-side document reading.
* **Chart.js (via CDN):** For interactive data visualization.

## 🚀 Live Demo

[**Launch InvoiceParsimus**](https://exekyute.github.io/InvoiceParsimus/)

## 💡 How to Use

1. Open the live dashboard.
2. Drag and drop a PDF invoice into the dropzone (or paste raw text).
3. The engine will instantly parse the document, extract the metrics, and populate your monthly ledger.
4. Review your dynamic charts, and click **Export** to download your sorted `.csv`.
