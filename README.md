# News-Reels-Software
Consuming the news from traditional to new ways of socially acceptable reels form 
import time
import schedule
import requests
from bs4 import BeautifulSoup
from datetime import datetime

# Function to fetch and display news
def fetch_news():
    url = 'https://news.ycombinator.com/'  # Example news site
    response = requests.get(url)
    soup = BeautifulSoup(response.text, 'html.parser')
    headlines = soup.find_all('a', class_='storylink')

    print(f"News Update at {datetime.now()}:")
    for i, headline in enumerate(headlines[:10], 1):
        print(f"{i}. {headline.text}")

# Schedule the news fetching function
schedule.every().day.at("09:00").do(fetch_news)
schedule.every().day.at("12:00").do(fetch_news)
schedule.every().day.at("18:00").do(fetch_news)

print("Sreela News Scheduler Started. Press Ctrl+C to exit.")

# Run the scheduled tasks
while True:
    schedule.run_pending()
    time.sleep(1)
# Sreela - Scheduled News Delivery System

Sreela is a Python-based scheduled news delivery system that fetches and displays the latest headlines from a specified news website at scheduled times. This eliminates the hassle of manually checking online news sites, providing you with timely news updates directly in your terminal.

## Features

- **Scheduled News Fetching**: Automatically fetches news at specified times.
- **Customizable**: Easily change the news source and schedule times.
- **Lightweight**: Minimal dependencies and easy to set up.

## Installation

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/yourusername/sreela.git
    cd sreela
    ```

2. **Install Dependencies**:
    Sreela requires `requests` and `beautifulsoup4` for fetching and parsing news.
    Install them using pip:
    ```bash
    pip install requests beautifulsoup4
    ```

## Usage

1. **Run the Script**:
    ```bash
    python sreela.py
    ```

2. The script will fetch news headlines at 9:00 AM, 12:00 PM, and 6:00 PM every day. You can customize these times in the `sreela.py` file.

## Customization

- **Change News Source**:
    Modify the `url` variable in the `fetch_news` function to change the news source.
    ```python
    url = 'https://news.ycombinator.com/'  # Example news site
    ```

- **Change Schedule Times**:
    Update the `schedule.every().day.at("HH:MM").do(fetch_news)` lines to your desired times.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Happy news reading with Sreela!
