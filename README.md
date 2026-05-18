# 🏛️ InvoiceParsimus

**A private, client-side OCR invoice parsing and financial sorting dashboard.**

InvoiceParsimus is a lightweight, single-file web application designed to extract key financial metrics from PDF invoices and raw images. Because it operates entirely within the browser using local machine vision, no financial data is ever uploaded to an external server, ensuring 100% privacy and security.

## ✨ Features

* **Machine Vision Integration:** Leverages `Tesseract.js` to run Optical Character Recognition (OCR) directly in the browser, allowing it to read standard PDFs, flat images (`.png`, `.jpeg`), and scanned receipts.
* **Smart Line-Scanning Engine:** Uses intelligent Regex to scan document lines and extract critical data points: Date (normalized to DD-MM-YYYY), Vendor Name, Subtotal, Tax (GST/HST/VAT), and Total Amount.
* **Monthly Sorting Matrix:** Automatically categorizes parsed invoices by month, providing a clean, chronological ledger.
* **Interactive Analytics:** Utilizes `Chart.js` to render dynamic visual breakdowns of monthly spend trends and vendor distribution.
* **One-Click Export:** Compiles all processed ledger data into a clean `.csv` file for easy import into accounting software or Excel.

## 🚀 Live Demo

[**Launch InvoiceParsimus**](https://exekyute.github.io/InvoiceParsimus/) 

## ⚠️ Current Scope & Limitations

As a strictly client-side application, InvoiceParsimus prioritizes privacy and hosting simplicity over heavy server-side AI processing. 

* **Invoice Formatting:** The line-scanning parser is explicitly tuned for standard corporate invoice layouts. It hunts for standard professional attributes (like "Amount Due", "Subtotal", and "Tax"). If an invoice places totals in highly unusual locations or omits clear labels, the engine may require a quick manual review.
* **Stylized Fonts:** The Tesseract OCR engine performs best on standard, clear text. Highly stylized corporate logos or heavily branded headers may occasionally obscure perfect vendor name extraction.
* **The Browser Architecture Choice:** I chose a 100% client-side setup because running this strictly as a static page keeps the app free to host and ensures user data never leaves their device. Utilizing cloud AI APIs would require exposing private API keys in the public frontend source code, so relying on localized OCR and smart text-matching was the most secure approach for this framework.

## 🗺️ Future Roadmap: Moving Beyond Regex

While Regex is incredibly fast and operates securely in the browser, it is structurally rigid. Future iterations of InvoiceParsimus aim to replace hardcoded text-matching with smarter parsing techniques to handle edge-case formatting:

* **In-Browser SLMs (Small Language Models):** Exploring libraries like `Transformers.js` or `WebLLM` to process OCR text contextually directly within the browser, maintaining the strict zero-server privacy policy.
* **Client-Side NLP:** Integrating lightweight Natural Language Processing engines (e.g., `Compromise.js`) to intelligently identify organizations and monetary values through grammar rather than strict formatting.
* **Serverless API Integration:** Evaluating a shift to a serverless architecture (like Vercel Edge Functions) to securely utilize LLM APIs (Anthropic, OpenAI) for foolproof structured data extraction without exposing API keys on the frontend.

## 🛠️ Tech Stack

* **HTML5 & Vanilla JavaScript:** Core logic and structure.
* **Tailwind CSS (via CDN):** For a responsive, dark-mode fintech UI.
* **PDF.js (via CDN):** For client-side document reading.
* **Tesseract.js (via CDN):** For client-side Optical Character Recognition.
* **Chart.js (via CDN):** For interactive data visualization.

## 💡 How to Use

1. Open the live dashboard.
2. Drag and drop a PDF or image into the dropzone.
3. Allow a few seconds for the local OCR engine to scan the document.
4. The engine will extract the metrics and populate your monthly ledger.
5. Review your dynamic charts, and click **Export** to download your sorted `.csv`.
