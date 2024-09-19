# Analysis_Sentiment
A Python project that scrapes online articles and analyzes their sentiment using newspaper3k and TextBlob.

```markdown
# Article Sentiment Analysis

This Python project demonstrates how to scrape an online article and perform basic sentiment analysis on the text using libraries like `newspaper3k` and `TextBlob`. The project fetches an article from a given URL, extracts its content, and then analyzes the sentiment of the text.

## Installation

Before running this project, ensure you have Python installed. You also need to install the following libraries:

```bash
pip install nltk textblob newspaper3k
```

### Additional Setup
- You may need to download additional NLTK resources by uncommenting and running:
```python
nltk.download('punkt')
```

## Usage

1. Clone this repository or copy the code to your local machine.
2. Run the script to download and analyze an article.
3. Modify the `url` variable in the script to analyze different articles.

### Running the script

You can either analyze an article from a URL or from a local text file:

1. **From an article URL:**
```python
url = 'https://blog.reedsy.com/short-story/0y7dum/'
article = Article(url)  # Initialize article object
article.download()       # Download the article
article.parse()          # Parse the article to extract text
article.nlp()            # Perform natural language processing
text = article.text      # Extract text content

# Sentiment analysis
blob = TextBlob(text)
sentiments = blob.sentiment.polarity  # Sentiment score: -1 = bad, 1 = good
print(f"Sentiment polarity: {sentiments}")
```

2. **From a local text file:**
```python
with open('text.txt', 'r') as f:
    text = f.read()

blob = TextBlob(text)
sentiments = blob.sentiment.polarity
print(f"Sentiment polarity: {sentiments}")
```

## Libraries Used

- **Newspaper3k**: This library is used for scraping articles from the web. It provides a simple API to download, parse, and extract text from an article.
- **TextBlob**: A powerful library for text processing, TextBlob allows for sentiment analysis, part-of-speech tagging, and other natural language processing (NLP) tasks.
- **NLTK**: A foundational library for NLP tasks in Python, used here primarily for tokenization with `punkt`.

## How It Works

1. **Article Scraping**: 
   The `newspaper3k` library is used to download and extract text from a given article URL. It parses metadata such as the title, author, and publication date, while also providing access to the article's main body of text.
   
2. **Sentiment Analysis**:
   Once the text is extracted, the `TextBlob` library analyzes its sentiment. The `polarity` value ranges from `-1` (very negative sentiment) to `1` (very positive sentiment). This simple sentiment score can help gauge the overall tone of the article.

## Data Source

- The project uses publicly available articles from websites like [Reedsy](https://blog.reedsy.com). You can analyze any article by replacing the URL in the script with another valid article link.
