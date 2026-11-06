Real-Time Web Bot Detection Using User Behavior Graph Analysis
A machine-learning based web bot detection project that identifies automated website sessions by analyzing both user browsing behavior and page-navigation graphs. The project combines behavioral features with graph-based features and uses classification models to distinguish human users from bots.
Project Overview
Traditional bot detection can rely on individual request patterns. This project goes a step further by examining:
- Behavioral patterns: number of requests, session duration, request rate, time intervals between requests, page diversity, action diversity, and page repetition.
- Navigation graph patterns: pages are represented as graph nodes and transitions between consecutive pages are represented as directed, weighted edges.
- Feature fusion: behavioral and graph features are combined into one session-level feature dataset for machine-learning classification.
The notebook also includes model comparison, error analysis, feature-importance analysis, a real-time detection simulation, and a Streamlit dashboard.
Key Features
- Generates a sample website activity dataset containing 2,000 sessions.
- Simulates human and bot browsing sessions (the notebook uses a 60% human / 40% bot label distribution).
- Extracts session-level behavioral features.
- Builds directed user-navigation graphs using NetworkX.
- Extracts graph statistics and transition-related features.
- Combines behavioral and graph features through feature fusion.
- Trains and compares multiple machine-learning classifiers.
- Evaluates models using Accuracy, Precision, Recall, F1-score, and ROC-AUC.
- Produces model-comparison plots, confusion matrices, and feature-importance analysis.
- Demonstrates real-time and multi-session bot-detection simulations.
- Creates a Streamlit dashboard for exploring web sessions and bot predictions.
Technologies Used
Technology	Purpose
Python	Main programming language
Pandas, NumPy	Data handling and numerical operations
Scikit-learn	Model training and evaluation
XGBoost	Gradient-boosting classifier
NetworkX	User-navigation graph creation and analysis
Matplotlib, Seaborn	Data visualization
Streamlit	Interactive dashboard
Google Colab / Jupyter Notebook	Development and execution environment


Machine Learning Models
The notebook compares the following classifiers:
1. Logistic Regression
2. Decision Tree
3. Random Forest
4. Support Vector Machine (SVM)
5. XGBoost
The real-time detection demonstration uses a Random Forest classifier.
Workflow
Website Activity Data
        |
        v
Data Preparation and Cleaning
        |
        +-----------------------------+
        |                             |
        v                             v
Behavioral Feature Extraction   Navigation Graph Creation
        |                             |
        v                             v
Behavioral Features             Graph Feature Extraction
        |                             |
        +--------------+--------------+
                       |
                       v
                 Feature Fusion
                       |
                       v
              Machine Learning Models
                       |
                       v
             Model Evaluation and Analysis
                       |
                       v
          Real-Time Detection Demonstration
                       |
                       v
              Streamlit Dashboard
Dataset
The notebook generates a sample dataset programmatically; it does not download a real-world website traffic dataset.

The simulated website contains pages such as:
- Home
- Products
- Product A, Product B, Product C
- Search
- Cart
- Checkout
- Login
- About
- Contact
The simulated activity records include a session ID, timestamp, page, action, and Human/Bot label. Actions include view, click, scroll, and search.

Important: The dataset is synthetic and its labels are assigned by the simulation logic. Results from this dataset should be treated as experimental results, not as proof of performance on real production traffic.
Feature Extraction
Behavioral features
Examples of the session-level behavioral features include:
- Request count
- Session duration
- Requests per second and per minute
- Average, standard deviation, minimum, and maximum request interval
- Number of unique pages
- Number of unique actions
- Page repetition ratio
Graph features
Each session is represented as a directed graph:
- Nodes: website pages visited during the session.
- Edges: transitions from one page to the next.
- Edge weights: number of times a transition occurs.
The notebook derives graph characteristics such as node and edge counts, graph density, self-loops, degree statistics, connected-component statistics, transition repetition, edge-weight statistics, transition entropy, and page-diversity measures.
Model Evaluation
Models are evaluated using:
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion matrix
- Classification report
The notebook saves model comparison results and generates visualizations for the evaluation metrics.
Evaluation note: The model-training section in the notebook deliberately applies a controlled 10% prediction-flip step to the reported class predictions to simulate imperfect predictions. Therefore, the reported Accuracy, Precision, Recall, and F1-score are adjusted simulation metrics, not the classifiers' untouched predictions. ROC-AUC is calculated from model probabilities with probability smoothing. Clearly disclose this when presenting or comparing results. For a standard evaluation, remove the artificial prediction adjustment and evaluate predictions directly.

Project Structure
A suggested GitHub repository structure is:
web-bot-detection/
│
├── README.md
├── graph_and_web_analyticsipynb.ipynb
├── web_bot_behavior_dataset.csv       # Generated by the notebook
├── behavior_features.csv              # Generated by the notebook
├── graph_features.csv                 # Generated by the notebook
├── final_fused_features.csv            # Generated by the notebook
├── model_results.csv                   # Generated by the notebook
├── app.py                              # Streamlit app (if saved separately)
└── *.png                               # Generated evaluation plots
Only add generated CSV files, plots, or app.py to GitHub if you have actually saved them in your repository. The notebook creates some of these outputs during execution.
How to Run
Option 1: Run using Google Colab
1. Download or clone this repository.
2. Open the .ipynb notebook in Google Colab.
3. Run the cells in order, from top to bottom.
4. The notebook installs the required Python libraries.
5. It generates the sample web activity dataset and extracts behavioral and graph features.
6. It trains and evaluates the machine-learning models.
7. Continue through the real-time simulation and Streamlit dashboard sections.
The notebook includes Google Colab-specific code for downloading generated files and exposing the Streamlit dashboard.
Option 2: Run locally
Create and activate a Python virtual environment, then install the dependencies:
python -m venv venv
Windows:
venv\Scripts\activate
macOS / Linux:
source venv/bin/activate
Install the packages:
pip install pandas numpy scikit-learn networkx matplotlib seaborn xgboost streamlit
Launch Jupyter:
pip install notebook
jupyter notebook
Open the notebook and run its cells in order. Note that some cells use Google Colab-specific modules (google.colab) and will need to be skipped or adapted when running locally.
Outputs
Depending on which notebook cells are executed, the project generates files such as:
- web_bot_behavior_dataset.csv
- behavior_features.csv
- graph_features.csv
- final_fused_features.csv
- model_results.csv
- Training and testing feature/label CSV files
- Metric-comparison plots
- Confusion-matrix visualizations
- Feature-importance visualizations
Future Improvements
- Validate the approach using real, anonymized web-server or application traffic.
- Evaluate on a separate external dataset and compare against established bot-detection baselines.
- Remove simulation-only prediction adjustments for standard model evaluation.
- Add cross-validation, hyperparameter tuning, and class-imbalance analysis.
- Test detection on previously unseen sessions and monitor false-positive rates.
- Deploy the dashboard with a production-ready data ingestion pipeline.
Disclaimer
This is an academic / experimental project based on simulated web activity. It is intended for learning and demonstration. It should not be considered a production-ready security system without validation on representative real-world traffic.
