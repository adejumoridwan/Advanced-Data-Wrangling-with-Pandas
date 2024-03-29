n this practice test, you'll be working with the "tips" dataset from the Seaborn library. This dataset contains information about tips given to waiters/waitresses at a restaurant. The dataset has the following columns:

- `total_bill`: the total bill amount
- `tip`: the tip amount
- `sex`: the gender of the person (Male or Female)
- `smoker`: whether the person is a smoker or not (Yes or No)
- `day`: the day of the week
- `time`: the time of day (Dinner or Lunch)
- `size`: the size of the party

Your task is to write a Python function called `process_data` that performs the following operations:

1. Load the "tips" dataset from the Seaborn library
2. Convert the `day` column to a categorical data type
3. Calculate the percentage of the total bill that was given as a tip
4. Add a new column `tip_percentage` to the DataFrame with the calculated tip percentages
5. Filter the DataFrame to include only records where the tip percentage is greater than 15%
6. Group the filtered DataFrame by `day` and `time`, and calculate the mean `tip_percentage` for each group
7. Return a new DataFrame containing the `day`, `time`, and their corresponding mean `tip_percentage` values

Here's the test suite you need to pass:

```python
import pandas as pd
import seaborn as sns
import unittest

class TestDataManipulation(unittest.TestCase):
    def setUp(self):
        self.tips_data = sns.load_dataset('tips')

    def test_process_data(self):
        # Load expected data
        expected_data = pd.DataFrame({
            'day': ['Sun', 'Sun', 'Sat', 'Sat', 'Thur', 'Thur'],
            'time': ['Dinner', 'Lunch', 'Dinner', 'Lunch', 'Dinner', 'Lunch'],
            'mean_tip_percentage': [19.72, 16.67, 19.18, 16.91, 18.59, 16.75]
        })

        # Call the student's function
        result = process_data()

        # Check if the resulting DataFrame matches the expected data
        self.assertTrue(result.equals(expected_data))

    def test_tip_percentage(self):
        # Calculate expected tip percentages
        expected_tip_percentages = [tip / total_bill * 100 for total_bill, tip in zip(self.tips_data['total_bill'], self.tips_data['tip'])]

        # Call the student's function
        result = process_data()

        # Check if the 'tip_percentage' column matches the expected values
        self.assertListEqual(result['tip_percentage'].tolist(), expected_tip_percentages)

if __name__ == '__main__':
    unittest.main()
```

This test suite defines two test cases:

1. `test_process_data`: This test case checks if the resulting DataFrame from the `process_data` function matches the expected data, which includes the `day`, `time`, and their corresponding mean `tip_percentage` values for records where the tip percentage is greater than 15%.

2. `test_tip_percentage`: This test case checks if the `tip_percentage` column in the resulting DataFrame correctly calculates the percentage of the total bill that was given as a tip, based on the original "tips" dataset.

To pass this practice test, you need to write the `process_data` function that performs the required operations on the "tips" dataset from the Seaborn library and returns the correct output. The test suite will automatically run and validate your function against the provided test cases.

Note: Make sure to import the necessary libraries (pandas and seaborn) in your code, and handle any potential errors or edge cases.