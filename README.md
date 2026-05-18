# 🏛️ InvoiceParsimus

**A private, client-side OCR invoice parsing and financial sorting dashboard.**

InvoiceParsimus is a lightweight, single-file web application designed to extract key financial metrics from PDF invoices and raw images. Because it operates entirely within the browser using local machine vision, no financial data is ever uploaded to an external server, ensuring 100% privacy and security.

## ✨ Features

* **Machine Vision Integration:** Leverages `Tesseract.js` to run Optical Character Recognition (OCR) directly in the browser, allowing it to read standard PDFs, flat images (`.png`, `.jpeg`), and scanned receipts.
* **Smart Line-Scanning Engine:** Uses intelligent Regex to scan document lines and extract critical data points: Date (normalized to DD-MM-YYYY), Vendor Name, Subtotal, Tax (GST/HST/VAT), and Total Amount.
* **Monthly Sorting Matrix:** Automatically categorizes parsed invoices by month, providing a clean, chronological ledger.
* **Interactive Analytics:** Utilizes `Chart.js` to render dynamic visual breakdowns of monthly spend trends and vendor distribution.
* **One-Click Export:** Compiles all processed ledger data into a clean `.csv` file for easy import into accounting software or Excel.

## ⚠️ Current Scope & Limitations

As a strictly client-side application, InvoiceParsimus prioritizes privacy over heavy server-side AI processing. Because of this architecture, users should be aware of the following:

* **Stylized Fonts:** The Tesseract OCR engine performs best on standard, highly legible text. Highly stylized, heavily branded, or handwritten invoices may result in garbled text extraction.
* **Non-Standard Layouts:** The Regex engine expects standard invoice layouts. If a document places totals in highly unusual locations or omits clear labels (like "Tax" or "Total"), the parser may fail to extract the exact amounts.
* **Manual Review:** This tool is designed to drastically speed up data entry, but it is not infallible. Always briefly verify the extracted ledger amounts against your original document before exporting the final CSV. 

## 🛠️ Tech Stack

* **HTML5 & Vanilla JavaScript:** Core logic and structure.
* **Tailwind CSS (via CDN):** For a responsive, dark-mode fintech UI.
* **PDF.js (via CDN):** For client-side document reading.
* **Tesseract.js (via CDN):** For client-side Optical Character Recognition.
* **Chart.js (via CDN):** For interactive data visualization.

## 🚀 Live Demo

[**Launch InvoiceParsimus**](https://exekyute.github.io/InvoiceParsimus/)

## 💡 How to Use

1. Open the live dashboard.
2. Drag and drop a PDF or image into the dropzone.
3. Allow a few seconds for the local OCR engine to scan the document.
4. The engine will extract the metrics and populate your monthly ledger.
5. Review your dynamic charts, and click **Export** to download your sorted `.csv`.
