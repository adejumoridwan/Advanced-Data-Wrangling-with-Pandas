Using the 20 Newsgroups dataset from scikit-learn, create a Python script that performs the following tasks:

1. **Working with String Data Types (str accessor, methods)**
   - Count the number of texts that contain the word 'computer'
   - Find the average length of the texts

2. **Regular Expressions for Advanced String Cleaning and Feature Engineering**
   - Remove all digits from the texts
   - Count the number of texts that contain the pattern 'http://'

3. **Text Preprocessing Techniques (Tokenization, Stop Word Removal, Stemming/Lemmatization)**
   - Tokenize the texts
   - Remove stop words from the tokens
   - Perform stemming on the remaining tokens

4. **Vectorized String Operations with apply() & lambda functions**
   - Count the number of words in each text
   - Convert all texts to uppercase

For each task, create a separate function and provide test cases to ensure your functions are working correctly.

**Test Cases**

1. **Working with String Data Types (str accessor, methods)**
   - For the first 10 texts, the expected output should be: `(6, 1092.1)`

2. **Regular Expressions for Advanced String Cleaning and Feature Engineering**
   - For the first 10 texts, the expected output for the 'http://' count should be: `1`

3. **Text Preprocessing Techniques (Tokenization, Stop Word Removal, Stemming/Lemmatization)**
   - For the first 10 texts, the preprocessed text should contain the string 'comput'

4. **Vectorized String Operations with apply() & lambda functions**
   - For the first 10 texts, the sum of word counts should be greater than 0

You can use the following code to load the 20 Newsgroups dataset:

```python
from sklearn.datasets import fetch_20newsgroups

newsgroups_data = fetch_20newsgroups(subset='train', remove=('headers', 'footers', 'quotes'))
texts = newsgroups_data.data
```

```python
import re
import nltk
from nltk.corpus import stopwords
from nltk.stem import PorterStemmer
from sklearn.datasets import fetch_20newsgroups
import unittest

# Download required NLTK resources
nltk.download('stopwords')
nltk.download('punkt')

# Fetch the 20 Newsgroups dataset
newsgroups_data = fetch_20newsgroups(subset='train', remove=('headers', 'footers', 'quotes'))
texts = newsgroups_data.data

class TextProcessingTestCase(unittest.TestCase):
    def test_exercise_1(self):
        computer_count, average_length = exercise_1(texts[:10])
        self.assertEqual(computer_count, 6)
        self.assertAlmostEqual(average_length, 1092.1)

    def test_exercise_2(self):
        cleaned_texts, http_count = exercise_2(texts[:10])
        self.assertEqual(http_count, 1)

    def test_exercise_3(self):
        preprocessed_texts = exercise_3(texts[:10])
        self.assertIn('comput', preprocessed_texts[0])

    def test_exercise_4(self):
        import pandas as pd
        word_counts, uppercase_texts = exercise_4(pd.Series(texts[:10]))
        self.assertGreater(word_counts.sum(), 0)

# Exercise 1: Working with String Data Types (str accessor, methods)
def exercise_1(texts):
    # Count the number of texts that contain the word 'computer'
    # Find the average length of the texts
    pass

# Exercise 2: Regular Expressions for Advanced String Cleaning and Feature Engineering
def exercise_2(texts):
    # Remove all digits from the texts
    # Count the number of texts that contain the pattern 'http://'
    pass

# Exercise 3: Text Preprocessing Techniques (Tokenization, Stop Word Removal, Stemming/Lemmatization)
def exercise_3(texts):
    # Tokenize the texts
    # Remove stop words from the tokens
    # Perform stemming on the remaining tokens
    pass

# Exercise 4: Vectorized String Operations with apply() & lambda functions
def exercise_4(texts):
    # Count the number of words in each text
    # Convert all texts to uppercase
    pass

if __name__ == '__main__':
    unittest.main()
```