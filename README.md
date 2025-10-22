# BlackRock Shares Outstanding Viewer

This single-page responsive web application, built with HTML and Tailwind CSS, allows users to view the maximum and minimum common stock shares outstanding for a given company, based on data fetched from the SEC EDGAR API.

## Features

- **Dynamic Data Display**: Fetches and displays entity name, maximum, and minimum common stock shares outstanding, along with their respective fiscal years.
- **Responsive Design**: Utilizes Tailwind CSS for a mobile-first, responsive user interface.
- **Live Updates**: Data is fetched and updated on the page without a full reload, supporting dynamic CIK changes via URL parameters.
- **SEC API Integration**: Retrieves `EntityCommonStockSharesOutstanding` data directly from the SEC's XBRL company concept endpoint.
- **User-Agent Compliance**: Configures a descriptive `User-Agent` header for SEC API requests as per guidance.

## How to Use

Simply open `index.html` in your web browser.

### Default View

Upon opening, the application will default to displaying data for **BlackRock (CIK 0001364742)**.

### View Other Companies

You can specify a different company's CIK (Central Index Key) by adding a `CIK` query parameter to the URL. For example:

`index.html?CIK=0001018724`

(Replace `0001018724` with any other 10-digit CIK you wish to query).

## Technical Details

- **HTML**: Provides the structure of the web page.
- **Tailwind CSS**: A utility-first CSS framework for styling and responsiveness.
- **JavaScript**: Handles data fetching, processing, and dynamic DOM updates.
- **SEC EDGAR API**: The primary data source.
- **Proxy**: For client-side requests to the SEC API, a proxy (like `api.allorigins.win` used in this example, or a custom-built proxy like AIPipe) is necessary to circumvent Cross-Origin Resource Sharing (CORS) restrictions. In a production environment, a more robust and secure proxy solution would be implemented.

## Data Filtering

The application filters the `EntityCommonStockSharesOutstanding` data to include only entries where:
- The fiscal year (`fy`) is greater than `2020`.
- The share value (`val`) is a valid numeric figure.

From this filtered set, the highest and lowest share values are identified and displayed.

## Attachments

This project refers to a `uid.txt` file, which contains a unique project identifier. Its content is embedded directly into the `index.html` for display purposes.