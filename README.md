This module implements a FastAPI web application for stock screening using Donchian Channels with custom conditions for a private client.
It provides endpoints for running screening tasks, checking task status, and downloading results as .xlsx.

## Installation
To install the application, follow these steps:

1. **Clone the repository**:
    ```sh
    git clone https://github.com/chengus/JoshuaStockWebApp.git
    cd JoshuaStockWebApp
    ```

2. **Install the required dependencies**:
    ```sh
    pip install -r requirements.txt
    ```

3. **Run the application**:
    ```sh
    fastapi dev
    ```

This will start the FastAPI server, and you can access the application at `http://127.0.0.1:8000`.

## Modules and Libraries

- **FastAPI**: Web framework for building APIs.
- **yfinance**: Library for accessing Yahoo Finance data.
- **openpyxl**: Library for working with Excel files.
- **yagmail**: Library for sending emails.
- **aioschedule**: Library for scheduling tasks with asyncio.
- **pandas**: Library for data manipulation and analysis.
- **requests**: Library for making HTTP requests.
- **concurrent.futures**: Module for running tasks concurrently.
- **logging**: Module for logging messages.

## Global Variables

- **Errors**: Dictionary to store errors encountered during processing.
- **LONG**: Dictionary to store long position data.
- **SHORT**: Dictionary to store short position data.
- **parent_etf**: Dictionary to store parent ETF data.
- **tradable_etfs**: List to store tradable ETFs.
- **t20holdings**: List to store top 20 holdings.
- **headers**: Dictionary to store HTTP headers for requests.
- **default_tickers**: List of default tickers.
- **processedTickers**: List to store processed tickers.
- **DOWNLOAD_DIR**: Directory for storing downloaded files.
- **process_pool**: ProcessPoolExecutor for running tasks concurrently.
- **task_status**: Dictionary to store task status.

## Endpoints

- **GET /**: Returns the `index.html` file.
- **GET /favicon.ico**: Returns the `favicon.ico` file.
- **POST /run_screening**: Starts a screening task with the given tickers and optional email sending.
- **GET /task_status/{task_id}**: Returns the status of a screening task.
- **GET /download/{task_id}**: Returns the Excel file for a completed screening task.

## Functions

- **startup_event**: Initializes the application and starts the cleanup scheduler.
- **run_cleanup_scheduler**: Schedules and runs the cleanup task daily.
- **cleanup_old_folders**: Deletes old folders in the download directory.
- **register**: Starts a screening task and returns the task ID.
- **get_task_status**: Returns the status of a screening task.
- **download_excel**: Returns the Excel file for a completed screening task and schedules folder cleanup.
- **log_requests**: Middleware to log incoming requests.
- **run_screening_task**: Runs the screening task and updates the task status.
- **create_download_directory**: Creates the download directory if it doesn't exist.
- **run_screening**: Runs the stock screening process.
- **process_tickers**: Processes the given tickers.
- **Condition**: Checks the Donchian Channel conditions for a ticker.
- **find_holdings**: Finds the holdings for tradable ETFs.
- **get_etf_holdings**: Retrieves the holdings for an ETF.
- **export_to_excel**: Exports the screening results to an Excel file.
- **send_email**: Sends an email with the screening results.