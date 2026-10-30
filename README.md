# Student Performance Analysis and Prediction using Machine Learning

A Python-based machine learning project that explores student academic-behaviour data, visualizes patterns, and trains classification models to predict a student's performance category.

The project uses the supplied `AI-Data.csv` dataset. It creates a correlation heatmap and several class-distribution charts, trains five classification algorithms, prints model evaluation reports, and optionally predicts a performance category for a set of user-entered values.

## Project contents

```text
Studentperformance_analysis/
├── AI-Data.csv          # Student dataset
├── Project.py           # Data analysis, model training, and prediction script
├── requirements.txt     # Python package dependencies
├── README.md            # Project documentation
└── .gitignore           # Git ignore rules (hidden file)
```

## Technologies used

- Python
- Pandas and NumPy for data handling
- Matplotlib and Seaborn for visualizations
- Scikit-learn for preprocessing, classification, and model evaluation

## Dataset

`AI-Data.csv` contains 480 student records and 17 columns. The target column is `Class`, with three performance categories:

- `L` – Low
- `M` – Medium
- `H` – High

The script initially uses the dataset to display a correlation heatmap and class-distribution charts. For model training, it removes several columns and uses these four input features:

| Model input | Meaning |
|---|---|
| `raisedhands` | Number of times the student raised their hand |
| `VisITedResources` | Number of times the student visited learning resources |
| `Discussion` | Number of student discussions |
| `StudentAbsenceDays` | Student absence category (`Under-7` or `Above-7`) |

The model predicts the `Class` category.

## Machine learning models

The script trains and evaluates these five classifiers:

1. Decision Tree Classifier
2. Random Forest Classifier
3. Perceptron
4. Logistic Regression
5. Multi-layer Perceptron (MLP) Classifier

For each model, the program prints a classification report and an accuracy value. The dataset is shuffled before a roughly 70/30 train-test split. Results can vary between runs because the shuffle and model initialization are not fixed with a random seed.

## Requirements

- Windows, macOS, or Linux
- Python 3
- `pip`

Python 3.10 or newer is a practical choice. The project dependencies are listed in `requirements.txt`.

## Setup and installation

### 1. Download or clone the repository

If you use Git:

```bash
git clone https://github.com/jaiadityav/Studentperformance_analysis.git
cd Studentperformance_analysis
```

Alternatively, download the repository as a ZIP from GitHub and extract it.

### 2. Open a terminal in the project folder

Make sure `Project.py`, `AI-Data.csv`, and `requirements.txt` are in the current folder. The script reads the CSV using the relative path `AI-Data.csv`, so it should be launched from this folder.

### 3. Create and activate a virtual environment (recommended)

**Windows CMD:**

```cmd
py -m venv .venv
.venv\Scripts\activate
```

**macOS / Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 4. Install the dependencies

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

On Windows, `py -m pip install -r requirements.txt` can be used if the `python` command is not available.

## Run the project

Run this command from the folder containing `Project.py` and `AI-Data.csv`:

```bash
python Project.py
```

On Windows, you can also run:

```cmd
py Project.py
```

## How to use the program

1. The program loads `AI-Data.csv` and displays a correlation heatmap. Close the plot window to continue.
2. A text menu appears with graph options:

   | Choice | Visualization |
   |---|---|
   | 1 | Marks class count |
   | 2 | Marks class by semester |
   | 3 | Marks class by gender |
   | 4 | Marks class by nationality |
   | 5 | Marks class by grade |
   | 6 | Marks class by section |
   | 7 | Marks class by topic |
   | 8 | Marks class by stage |
   | 9 | Marks class by absence days |
   | 10 | Stop displaying graphs and continue to model training |

3. Enter a number from `1` to `9` to display the corresponding chart. Close each chart window to return to the menu.
4. Enter `10` when you have finished exploring the charts. This exits the graph menu; it does **not** stop the whole program.
5. The program trains the five classifiers and prints their classification reports and accuracy values.
6. At the prompt `Do you want to test specific input (y or n):`, enter `y` to try a sample prediction or `n` to finish.
7. When testing an input, the program asks for several student details. The current implementation actually passes only the four model features below to the classifiers: raised hands, visited resources, discussions, and absence category. The other prompted details are currently not used in the prediction.

For the prediction inputs, enter the requested absence category as `Under-7` or `Above-7`. Use numeric values for raised hands, visited resources, and discussions.

## Important implementation notes

This repository contains the original project script. Review these limitations before interpreting its prediction results:

- **Class-label display mapping needs correction:** Scikit-learn's `LabelEncoder` encodes the target labels alphabetically as `H = 0`, `L = 1`, and `M = 2`. The current script converts predictions back using `0 = H`, `1 = M`, and `2 = L`, which swaps the displayed `L` and `M` labels. Correct the reverse mapping in `Project.py` before relying on the displayed prediction categories.
- **Logistic Regression accuracy display needs correction:** The current script prints the Perceptron accuracy variable for the Logistic Regression line. Replace `round(accP, 3)` with `round(accL, 3)` in that print statement.
- The script prompts for demographic and other information that is not included in the four-feature prediction array. Those prompts do not currently affect the model output.
- Model scores may change from run to run because the data shuffle and classifiers do not use fixed random seeds.
- This is an educational demonstration, not a validated tool for making high-stakes decisions about students.

## Troubleshooting

**`FileNotFoundError: AI-Data.csv`**

Run the program from the directory that contains both `Project.py` and `AI-Data.csv`. Check that the dataset filename is exactly `AI-Data.csv`.

**`ModuleNotFoundError`**

Activate the virtual environment and install dependencies again:

```bash
python -m pip install -r requirements.txt
```

**A plot window appears and the program seems paused**

This is expected. Close the Matplotlib plot window to return to the program.

**`python` is not recognized on Windows**

Try `py Project.py` and `py -m pip install -r requirements.txt` instead.

## Possible future improvements

- Fix the class-label and Logistic Regression accuracy display issues.
- Remove unused prompts or include the additional fields in a consistently preprocessed model pipeline.
- Use a stratified train-test split and fixed random seeds for repeatable evaluation.
- Add input validation and clearer prediction output.
- Save trained models and provide a graphical user interface or web application.

## License

No license file was included with the supplied project files. Add a license only after confirming the project owner's intended terms for reuse and distribution.
