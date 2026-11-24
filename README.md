Support Ticket Classification
An end-to-end Python project that classifies customer support tickets into categories and assigns priority levels.
Features
Text cleaning and tokenization (spaCy when installed; regex fallback)
Ticket category classification with TF-IDF + Logistic Regression
Priority tagging (High / Medium / Low) using transparent keyword and urgency rules
Evaluation metrics and confusion matrix report
Streamlit interface for single-ticket and CSV batch classification
Sample dataset for demonstration
Project structure
```text
support_ticket_classification/
├── app.py
├── train.py
├── evaluate.py
├── requirements.txt
├── README.md
├── data/
│   └── sample_tickets.csv
├── models/                 # trained model files are saved here
├── reports/                # evaluation report is saved here
├── notebooks/
│   └── support_ticket_classification.ipynb
└── src/
    ├── __init__.py
    ├── preprocessing.py
    ├── priority.py
    └── classifier.py
```
Setup
Python 3.10+ recommended.
```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

pip install -r requirements.txt
python train.py
python evaluate.py
streamlit run app.py
```
Optional spaCy language model:
```bash
python -m spacy download en_core_web_sm
```
The project continues to work without spaCy by using a regex-based tokenizer.
Dataset
`data/sample_tickets.csv` is a small, illustrative dataset created for this project. It is suitable for testing the workflow, not for claiming production-grade accuracy. Replace it with a larger, representative, properly labelled support-ticket dataset before deployment.
Required columns:
`ticket_text`: the customer's message
`category`: one of `Billing`, `Technical`, `Account`, `Shipping`, `Refund`
`priority`: one of `High`, `Medium`, `Low`
How it works
Preprocess ticket text (lowercase, remove noise, tokenize).
Train a TF-IDF + Logistic Regression category model.
Predict a category and confidence score for a new ticket.
Assign priority using explainable urgency and impact rules.
Evaluate category predictions using accuracy, precision, recall, F1-score and a confusion matrix.
Priority rules are a transparent baseline. Review them with support staff and tune them to the organisation's SLA policy.
Important
Do not upload personal, financial, password, or other sensitive customer information to an unapproved environment. Review predictions before acting on them.
