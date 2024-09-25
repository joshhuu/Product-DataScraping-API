# Product Data Scraper

## Overview
This project is a FastAPI-based web scraper designed to extract product information from web pages. The scraper attempts to retrieve product data by parsing the page's JSON-LD and meta tags.

## Features
 Fetch Product Information from JSON-LD: Extracts product details from structured JSON-LD data.
- Fetch Product Information from Meta Tags: If JSON-LD data is not available, the scraper falls back to extracting product details from Open Graph (`og:*`) and Twitter (`twitter:*`) meta tags.
- REST API Endpoint: The `/scrape` endpoint allows users to submit a URL and receive product data.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/product-scraper.git
   cd product-scraper
   

2. Set up a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   

3. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   

4. Run the application:
   ```bash
   uvicorn main:app --reload
   

## API Endpoints

### POST `/scrape`
- Description: Fetch product data from the given URL.
- Request: 
-Body: JSON object containing the `url` key.
  ```json
  {
    "url": "https://example.com/product-page"
  }
  ```
- Response: 
  - JSON object containing the product name, price, URL, image URL, and description.

#### Example Request
```bash
curl -X POST "http://127.0.0.1:8000/scrape" -H "Content-Type: application/json" -d '{"url": "https://example.com/product-page"}'


#### Example Response
```json
{
  "product_name": "Sample Product",
  "product_price": "29.99",
  "product_url": "https://example.com/product-page",
  "product_image_url": "https://example.com/images/product.jpg",
  "product_description": "A short description of the product."
}


## Dependencies
- `FastAPI`: Web framework for building APIs.
- `requests`: Library for making HTTP requests.
- `BeautifulSoup4`: Python library for parsing HTML and extracting data.
- `pydantic`: Data validation and parsing library used for request models.

Install dependencies via:
```bash
pip install fastapi requests beautifulsoup4 pydantic uvicorn


## Running Locally
Start the application using Uvicorn:
```bash
uvicorn main:app --reload
```
The API will be available at `http://127.0.0.1:8000`.

## License
This project is licensed under the MIT License.