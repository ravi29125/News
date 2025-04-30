
# 📰 News Summarizer with Text-to-Speech (TTS)

This Jupyter notebook fetches the latest news articles using the [NewsAPI](https://newsapi.org/), summarizes the top article using a fine-tuned BART transformer model, and reads the summary aloud using a text-to-speech engine.

## 📌 Features

- Fetches news articles for a specific keyword and date.
- Extracts and summarizes the most popular article using Hugging Face's BART model.
- Speaks the summary aloud using `pyttsx3`.

## 🚀 Requirements

Make sure the following Python packages are installed:

```bash
pip install requests transformers pyttsx3
```

Also, make sure to have:

- A valid [NewsAPI](https://newsapi.org/) key.
- A pre-trained or fine-tuned BART model saved locally under the name `bart_model`.

## 🔧 Usage

1. **Import Dependencies**
   - Modules like `requests`, `transformers`, and `pyttsx3` are imported for HTTP requests, model inference, and speech synthesis.

2. **Set Up API Request**
   - You define a `key` for NewsAPI and build a URL to fetch news on a specific topic and date.

3. **Fetch & Parse News**
   - The response is parsed, and the top article's title and content are extracted.

4. **Summarize with BART**
   - The content is summarized using a preloaded BART model and tokenizer from Hugging Face Transformers.

5. **Play Summary with TTS**
   - The final summary is read aloud using `pyttsx3`.

## 🧠 Model

- The BART model must be available locally in a directory named `bart_model`. If not already available, you can download a pretrained summarization model:

```python
from transformers import BartForConditionalGeneration, BartTokenizer

model = BartForConditionalGeneration.from_pretrained("facebook/bart-large-cnn")
tokenizer = BartTokenizer.from_pretrained("facebook/bart-large-cnn")

model.save_pretrained("bart_model")
tokenizer.save_pretrained("bart_model")
```

## 📎 Example Output

```
📰 News Article:
Google, Apple, and Snap aren’t happy about Meta’s poorly-redacted slides...

Summary:
Google, Apple, and Snap aren’t happy about Meta’s poorly-redacted slides. An Apple attorney called the inadvertent disclosures from Meta's antitrust trial egregious.
```

## ⚠️ Notes

- If no articles are found, the script exits gracefully.
- Ensure `pyttsx3` is properly configured to use a system-compatible speech engine (like `sapi5` on Windows or `espeak` on Linux).

## 📄 License

This project is provided for educational and experimental purposes.
