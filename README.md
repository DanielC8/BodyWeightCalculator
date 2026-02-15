# Body Weight Calculator

## Body Fat Percentage Estimator Using Jackson-Pollock Skinfold Method

A command-line Python tool that estimates body fat percentage from skinfold and circumference measurements. It uses the Jackson-Pollock regression equations to calculate body density, then converts to body fat percentage via the Siri equation.

## Features

- **Gender-Specific Formulas**: Separate measurement sets and equations for men and women.
- **Input Validation**: Rejects non-numeric, negative, and malformed inputs.
- **No External Dependencies**: Runs on the Python standard library alone.

## Project Structure

```
main.py  - All application logic: input collection, validation, and body fat calculation.
```

## How It Works

1. **Gender Selection**: Prompts the user for gender (M or F).
2. **Measurement Collection**: Requests the required skinfold and circumference measurements based on gender.
3. **Body Density Calculation**: Applies the Jackson-Pollock equation to compute body density.
4. **Body Fat Conversion**: Converts body density to body fat percentage using the Siri equation: `(495 / body_density) - 450`.
5. **Output**: Prints the estimated body fat percentage rounded to 2 decimal places.

## Required Measurements

**Men** (6 measurements):
- Chest Skinfold (mm)
- Abdomen Skinfold (mm)
- Thigh Skinfold (mm)
- Age (Year)
- Waist Circumference (m)
- Forearm Circumference (m)

**Women** (5 measurements):
- Triceps Skinfold (mm)
- Thigh Skinfold (mm)
- Suprailiac Skinfold (mm)
- Age (Year)
- Gluteal Circumference (cm)

## Usage

Run the script:

```bash
python main.py
```

Follow the prompts to enter your gender and measurements. The program will output your estimated body fat percentage.

### Example

```
Please enter your gender (F or M): M

Please enter the measurement for your Chest Skinfold (mm): 15

Please enter the measurement for your Abdomen Skinfold (mm): 20

Please enter the measurement for your Thigh Skinfold (mm): 12

Please enter your age (Year): 30

Please enter the measurement for your Waist Circumference (m): 0.85

Please enter the measurement for your Forearm Circumference (m): 0.28

Your body fat percentage is 14.52%
```

## Functions

### `isfloat(num)`
Validates whether a string can be interpreted as a non-negative float. Handles edge cases like standalone periods and leading decimal points.

### `push(stack, value)`
Prepends a value to a list, used to build the measurement list during input collection.

## Formulas

**Male Body Density (Jackson-Pollock):**
```
BD = 1.0990750 - 0.0008209(S) + 0.0000026(S^2) - 0.0002017(A) - 0.005675(W) + 0.018586(F)
```
Where S = sum of skinfolds, A = age, W = waist circumference, F = forearm circumference.

**Female Body Density (Jackson-Pollock):**
```
BD = 1.1470292 - 0.0009376(S) + 0.0000030(S^2) - 0.0001156(A) - 0.0005839(G)
```
Where S = sum of skinfolds, A = age, G = gluteal circumference.

**Body Fat Percentage (Siri Equation):**
```
BF% = (495 / BD) - 450
```

## Requirements

- Python >= 3.10
