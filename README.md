# Image Scraper using Python Flask

## Overview
This project is a web-based application that allows users to search, scrape, and download images from Google. The application is built using Python Flask and integrates MongoDB for storing image data. It simplifies the process of collecting images for various use cases, such as research or design projects.

## Features
- User-friendly web interface for searching images.
- Scrapes and downloads images from Google search results.
- Stores image data in a MongoDB database.
- Organizes downloaded images in a local directory.

## Prerequisites
- Python 3.6 or higher
- MongoDB instance (local or cloud)

## Installation

1. Clone the repository:
    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```

2. Install the required Python libraries:
    ```bash
    pip install -r requirements.txt
    ```

3. Create a directory to store images (if not created automatically):
    ```bash
    mkdir images
    ```

4. Set up MongoDB:
    - If using a local MongoDB instance, ensure it is running.
    - If using MongoDB Atlas, replace the connection string in the code with your credentials.

## Usage

1. Run the Flask application:
    ```bash
    python app.py
    ```

2. Open a web browser and navigate to:
    ```
    http://localhost:8000
    ```

3. Enter a search query in the text box and submit to scrape images.

4. Downloaded images will be saved in the `images` directory, and metadata will be stored in MongoDB.

## Code Details

### Main Components

1. **Flask Routes**:
    - `/` : Renders the homepage with a search form.
    - `/review` : Handles the search request, scrapes images, and stores data.

2. **Image Scraping**:
    - Uses `requests` and `BeautifulSoup` to fetch and parse Google search results.
    - Downloads images using their `src` attributes.

3. **MongoDB Integration**:
    - Connects to MongoDB using `pymongo`.
    - Stores image metadata, including index and binary data.

4. **Logging**:
    - Logs events and errors in `scrapper.log`.

### Dependencies

- `Flask`: For building the web application.
- `requests`: For HTTP requests.
- `BeautifulSoup`: For parsing HTML content.
- `pymongo`: For MongoDB integration.
- `os`: For handling file system operations.

## Directory Structure
```
project-directory/
├── app.py               # Main Flask application
├── templates/
│   ├── index.html       # HTML template for the homepage
├── images/              # Directory to store downloaded images
├── scrapper.log         # Log file for tracking events and errors
└── README.md            # Project documentation
```

## Known Issues
- The Google search scraping might fail if the structure of the search results page changes.
- Limited to public and non-copyrighted images.
- Potential for blocking if Google detects scraping behavior.