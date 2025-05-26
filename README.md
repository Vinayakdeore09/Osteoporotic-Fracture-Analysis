# Osteoporotic Fracture Analysis

This project focuses on the detection and classification of osteoporotic fractures using machine learning. A **Random Forest Classifier** is trained on clinical data to predict the bone health status of patients, categorizing them as **Normal**, **Osteopenia**, or **Osteoporotic** based on input features.

---

## Project Overview

* **Topic:** Osteoporotic Fracture Analysis
* **Goal:** Detect and classify osteoporosis-related fractures
* **Model:** Random Forest Classifier
* **Accuracy:** \~94%
* **Dataset:** Clinical dataset containing demographic and medical history features
* **Features Used:**

  * Age
  * Sex
  * Associated Medical Problems
  * History of Injury/Surgery
  * Drug History

---

## Dataset Preparation

* The dataset is read from `Dataset.csv`.
* Irrelevant columns like `SI.NO`, `DATE`, and `NAME` are dropped.
* Categorical features are mapped to numerical values for model compatibility:

  * `SEX`: Male=1, Female=0
  * `ASSO MEDICAL PROB`: Various medical conditions mapped to integers
  * `H/O INJURY/SURGERY`: History of surgeries/injuries mapped to integers
  * `DRUG HISTORY`: Drug intake mapped to integers

---

## Model Training

* Random Forest Classifier with 10 trees (`n_estimators=10`) and entropy criterion.
* Dataset is split into 70% training and 30% testing sets.
* The model achieves an accuracy of approximately 94%.

---

## Usage

### Prediction Function

The model predicts bone health status based on input features:

| Output Class | avg Score Range |
| ------------ | --------------- |
| Normal       | avg < 60        |
| Osteopenia   | 60 < avg < 100  |
| Osteoporotic | avg > 100       |

Example test input for prediction:

\`\`\`python

Age = 29

SEX = 1             # Male = 1, Female = 0

Prob = 3            # Associated Medical Problem mapped integer

INJURY = 2          # Injury/Surgery mapped integer

DRUG = 1            # Drug History mapped integer

test = \[\[Age, SEX, Prob, INJURY, DRUG]]

result = give\_pred(test)

print(result)

## Flask Web Application

A simple Flask app provides a web interface to input patient data and get predictions:

### URL routes:

/ or /Hello - Home page with form input

/result - Displays prediction results

Run the app locally:

python app.py

The app will be available at [http://127.0.0.1:5000/](http://127.0.0.1:5000/).

### Requirements

Python 3.x

pandas

numpy

scikit-learn

Flask

seaborn (for any exploratory data visualization, optional)

matplotlib (optional)

## File Structure

.

├── Dataset.csv

├── app.py                # Flask application script

├── OstoFracture.py       # Contains \`give\_pred\` prediction function

├── templates/

│   └── web.html          # HTML template for the web UI

├── README.md

└── requirements.txt      # (Optional) Python dependencies list

### Future Improvements

#### Increase the size and diversity of the dataset.

#### Hyperparameter tuning for better model performance.

#### Add more features such as bone density scan results.

#### Deploy the web app on cloud platforms.

#### Add user authentication and data storage.

## License

This project is open-source and available under the MIT License.

## Acknowledgments

Thanks to all contributors and data providers for making this project possible.

If you have any questions or want to contribute, feel free to open an issue or pull request.
