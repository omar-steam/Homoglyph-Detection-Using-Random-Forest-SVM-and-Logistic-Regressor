# Homoglyph-Detection-Using-Random-Forest-SVM-and-Logistic-Regressor
Homoglyphs are characters that appear visually similar but have different Unicode code points. They're commonly used in phishing attacks to create deceptive domain names or text that looks legitimate but isn't. For example, using Cyrillic 'о' (U+043E) instead of Latin 'o' (U+006F) in "password" → "passwоrd".

This project trains machine learning models to identify when text contains homoglyph substitutions, helping detect potential security threats.

## Features

- Automated homoglyph generation using the `confusables` library
- Character-level n-gram feature extraction (unigrams and bigrams)
- Multiple ML algorithms for comparison:
  - Logistic Regression
  - Support Vector Machine (SVM)
  - Random Forest
- Cross-validation for robust model evaluation
- Real-time detection of homoglyph attacks

## Installation

```bash
pip install confusables scikit-learn pandas numpy
```

## Usage

Run the script to train models and test detection:

```bash
python rfhologyph.py
```

The script will:
1. Generate a dataset of clean words and their homoglyph variants
2. Train multiple classification models
3. Evaluate performance using cross-validation
4. Test on sample inputs

### Example Output

```
secure -> Clean
sеcurе -> Homoglyph  # Contains Cyrillic characters
password -> Clean
pаsswоrd -> Homoglyph  # Contains Cyrillic 'а' and 'о'
```

## How It Works

1. Dataset Generation: Creates pairs of original words and their homoglyph variants using Unicode confusable characters
2. Feature Extraction: Uses character-level n-grams (1-2 characters) to capture subtle differences
3. Model Training: Trains multiple classifiers to distinguish between clean and homoglyph-modified text
4. Detection: Classifies new text as either clean (0) or containing homoglyphs (1)

## Applications

- Phishing detection in emails and websites
- Domain name security monitoring
- Brand protection against typosquatting
- Content moderation for deceptive text

## Extending the Project

- Add more diverse word lists (domains, brand names, common passwords)
- Implement additional feature extraction methods
- Add support for mixed-script detection
- Create a web API for real-time detection
- Expand to detect other Unicode-based attacks

## Dataset

The current implementation uses a small sample word list including common terms like "password", "secure", "facebook", etc. For production use, consider expanding with:
- Popular domain names
- Brand names
- Common passwords
- Technical terminology

## Performance

Models achieve high accuracy on the generated dataset. Performance may vary with different word types and homoglyph patterns in real-world scenarios.

## Contributing

Feel free to contribute by:
- Adding more comprehensive word lists
- Implementing additional ML algorithms
- Improving feature extraction methods
- Adding evaluation metrics

## License

MIT License
