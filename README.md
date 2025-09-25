# Transaction Fraud Detector

A client-side web tool for identifying potentially fraudulent or anomalous transactions in a dataset. This application runs entirely in your browser, ensuring your data remains private. It uses simplified versions of common statistical and forensic accounting techniques to flag suspicious entries.

 <!-- It's recommended to add a screenshot of your application here -->

## Features

*   **Multiple Data Input Methods:**
    *   Paste data directly as a JSON array.
    *   Drag and drop an Excel file (`.xlsx`, `.xls`) for automatic conversion to JSON.
*   **Configurable Analysis:** Specify which column in your dataset contains the transaction amounts to be analyzed.
*   **Client-Side Processing:** All analysis is performed in the browser. No data is ever sent to a server.
*   **Multi-Faceted Analysis:** Suspicious entries are flagged based on three distinct methods:
    1.  **Benford's Law:** Checks the frequency distribution of the first digit of transaction amounts against the expected logarithmic distribution. Significant deviations can indicate fabricated numbers.
    2.  **Statistical Outliers (Z-Score):** Identifies transactions that are statistically unusual (too high or too low) compared to the rest of the data.
    3.  **Clustering Outliers:** A simplified heuristic to find isolated, high-value transactions that don't have other similar-value transactions nearby.
*   **Interactive Visualization:** A bar chart compares your data's first-digit frequency against the Benford's Law distribution, providing a clear visual reference for anomalies.

## How to Use

1.  **Open the Application:** Simply open the `index.html` file in any modern web browser (e.g., Chrome, Firefox, Edge).
    * Open Google Chrome
    * Press `CTRL + O`
    * A window opens
    * Navigate to your destination folder and click on your `.html` file
2.  **Provide Your Data:**
    *   **Option A: Drag and Drop an Excel File**
        *   Drag your Excel file and drop it onto the designated drop zone. The tool will read the first sheet and convert its contents into the JSON text area.
    *   **Option B: Paste JSON Data**
        *   Copy your transaction data, formatted as a JSON array of objects, and paste it into the text area.

3.  **Configure the Column:**
    *   In the "Column to scan" input field, enter the name of the key in your JSON objects that holds the numerical transaction values (e.g., `amount`, `value`, `price`). The default is `amount`.

4.  **Run Analysis:**
    *   Click the **Run Analysis** button.

5.  **Review Results:**
    *   The results section will appear, displaying the Benford's Law chart and a list of any transactions that were flagged as suspicious, along with the reason(s) why.

## Data Format

The tool expects data to be an array of JSON objects. Each object represents a transaction and must contain a numerical field to be analyzed.

**Example (`mock_data.json`):**
```json
[
  {"id": 101, "amount": 120.50},
  {"id": 102, "amount": 2345.00},
  {"id": 103, "amount": 9999.00},
  {"id": 104, "amount": 1.23},
  {"id": 105, "amount": 543.21}
]
```

## Technologies Used

*   **HTML5, CSS3, JavaScript**
*   **SheetJS/xlsx:** For parsing and reading Excel files in the browser.

---

***Disclaimer:** This is a demonstration tool and not a production-grade fraud detection system. The analytical methods are simplified and should be used for educational or illustrative purposes. Always consult with a professional for financial auditing.*