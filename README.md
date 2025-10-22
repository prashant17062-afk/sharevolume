# Company Shares Outstanding Viewer

This is a single-file, responsive web application built with HTML, JavaScript, and Tailwind CSS. It allows users to view the maximum and minimum number of common stock shares outstanding for a given company, based on data fetched directly from the U.S. Securities and Exchange Commission (SEC) EDGAR API.

## Features

*   **Dynamic Data Fetching**: Retrieves `EntityCommonStockSharesOutstanding` data for a specified CIK from the SEC API.
*   **Data Filtering**: Filters data to include only fiscal years (FY) greater than 2020 and valid numeric values for shares.
*   **Max/Min Identification**: Clearly displays the maximum and minimum share outstanding values along with their corresponding fiscal years.
*   **Responsive Design**: Utilizes Tailwind CSS to ensure a visually appealing and adaptive layout across various devices.
*   **Client-Side Updates**: Updates the displayed information dynamically without page reloads when switching between CIKs via URL parameters.
*   **Loading and Error States**: Provides visual feedback during data fetching and displays an error message if data retrieval fails.

## How to Use

1.  **Open `index.html`**: Simply open the `index.html` file in your web browser. By default, it will display data for Ameren (CIK: `0001002910`).

2.  **Specify a Different Company (CIK)**: To view data for another company, append a `?CIK=<your-10-digit-cik>` parameter to the URL.
    *   **Example**: To view data for Apple Inc. (CIK: `0000320193`), open:
        `index.html?CIK=0000320193`
    *   The application will fetch and display the relevant data without reloading the entire page.

## Technical Details

*   **Frontend**: HTML, JavaScript, Tailwind CSS (via CDN).
*   **Data Source**: SEC EDGAR API (`https://data.sec.gov/api/xbrl/companyconcept/CIK<CIK>/dei/EntityCommonStockSharesOutstanding.json`).
*   **User-Agent**: A descriptive `User-Agent` is set in the `fetch` request as per SEC guidance.
*   **Filtering Logic**:
    *   `fy` (fiscal year) must be greater than "2020".
    *   `val` (value of shares) must be a numeric type.

## Project Structure

*   `index.html`: The main single-file web application containing all HTML, CSS (Tailwind CDN), and JavaScript.
*   `README.md`: This file, providing an overview and instructions.
*   `LICENSE`: The MIT License for the project.
*   `uid.txt`: An attached file provided with the project. Its specific use case is not defined within the application, but it is committed as-is.

## Development Notes

The application uses client-side JavaScript to make API calls. If you encounter CORS issues during local development with a different CIK, you might need to use a browser extension to disable CORS or run a simple local proxy server. However, direct `fetch` from SEC API generally works in modern browsers when accessed directly or from a web server.
