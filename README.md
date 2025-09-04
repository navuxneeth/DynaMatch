# DynaMatch

A browser-based tool that takes numerical and categorical data (from a CSV/XLSX file or pasted text) and generates an interactive UI. Users can manipulate sliders and options to explore the relationships within the data, find the closest matching preset, and discover new data combinations through real-time interpolation.

*Screenshot:*


## Features

-   **Flexible Data Input**: Upload `.csv`, `.xlsx` files, or simply paste comma/tab-separated data.
-   **Dynamic UI Generation**: The tool automatically creates sliders for numerical data and option selectors for categorical data based on your input.
-   **Real-time Interpolation**: Adjust one trait, and all others update in real-time based on the relationships in the original dataset.
-   **Slider Locking**: Lock in specific values you like, and the tool will interpolate the remaining unlocked values around your choices.
-   **Preset Matching**: Always recommends the closest "real" data point from your original dataset based on your current settings.
-   **Fully Client-Side**: All processing happens in your browser. Your data is never uploaded to a server.
-   **Responsive Design**: Usable on both desktop and mobile devices.

## How to Use

1.  **Step 1: Provide Data**
    -   Use the **"Select File"** button to upload a `.csv` or `.xlsx` file from your computer.
    -   Alternatively, paste your data directly into the **"Or Paste Data"** text area.
    -   Click **"Process Data"**.

2.  **Step 2: Configure Columns**
    -   **Preset Name Column**: Select the column that contains the unique names for your data rows (e.g., `BreedName`, `Item ID`).
    -   **Data Column Types**: For every other column, classify it as:
        -   `Numerical Slider`: For continuous data like weight, score, or size.
        -   `Categorical Options`: For discrete data that fits into categories (e.g., Low, Medium, High). The tool expects this data to be numerical (e.g., 1-5).
        -   `Ignore Column`: To exclude a column from the tool.
    -   Click **"Generate Tool"**.

3.  **Step 3: Interact with the Tool**
    -   **Adjust Sliders**: Drag the sliders for numerical traits.
    -   **Select Options**: Click the buttons for categorical traits.
    -   **Observe Changes**: As you change one value, all other unlocked values will adjust automatically.
    -   **Lock Sliders**: Click the `LOCK SLIDERS: OFF` button to turn it on. Now, any slider or option you adjust will become "locked" and won't be changed by the interpolation logic, allowing you to fine-tune your results.
    -   **View Recommendation**: The "RECOMMENDED" section will always show you which entry from your original data is the closest match to your current settings.

## Data Format Requirements

For best results, your data should be structured as follows:

-   **Header Row**: The first row must contain the names of the columns (headers).
-   **Name Column**: The first column should be the unique identifier for each row.
-   **Data Columns**: Subsequent columns should contain the trait data. For "Categorical Options", it's best to use a numerical scale (e.g., 1 for "Very Low", 2 for "Low", ..., 5 for "Very High").
-   **Clean Data**: The tool includes a feature to handle missing or non-numeric data by replacing it with the column's average value, but providing clean, numerical data is recommended.

#### Example Data:

| BreedName      | EnergyLevel | Trainability | Shedding | Size |
| :------------- | :---------: | :----------: | :------: | :--: |
| Golden Retriever |      4      |       5      |     4    | 4.5  |
| Basset Hound   |      2      |       2      |     3    | 3.2  |
| Beagle         |      5      |       3      |     3    | 2.8  |
| Bulldog        |      2      |       3      |     3    | 3.0  |

## How to Run Locally

Since this is a self-contained HTML file with no server-side dependencies, you can run it directly:
1.  Download `index.html`.
2.  Open the file in any modern web browser.

## Acknowledgments

-   Built by Navaneeth Sankar K P.
-   Uses [PapaParse.js](https://www.papaparse.com/) for CSV parsing.
-   Uses [SheetJS (xlsx.js)](https://sheetjs.com/) for Excel file parsing.