# Leveraging-Rule-Based-Systems-for-Financial-Regulation-Document-Filtering

## Project Overview

This project develops an intelligent document filtering system for financial regulations using rule-based approaches. It aims to automatically identify and categorize relevant financial regulatory documents from a large corpus of diverse texts.

## Installation and Setup

### Codes and Resources Used

- **Editor Used:** Google Colab
- **Python Version:** Python 3

### Python Packages Used

- **General Purpose:** collections
- **Data Manipulation:** pandas, numpy
- **Data Visualization:** matplotlib, seaborn
- **Machine Learning:** scikit-learn

To set up the project environment:

1. Ensure you have Python 3 installed on your system.
2. Clone this repository:
   ```
   git clone https://github.com/your-username/financial-regulation-document-filtering.git
   ```
3. Navigate to the project directory:
   ```
   cd financial-regulation-document-filtering
   ```
4. Install the required packages:
   ```
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```

## Data

### Source Data

The project uses two main datasets:

1. **relevance_data.csv**: Contains information about document relevance.
2. **regulations.csv**: Contains the full text and metadata of regulatory documents.

### Data Acquisition

The data is loaded from CSV files stored in Google Drive. To replicate this:

1. Upload your `relevance_data.csv` and `regulations.csv` files to your Google Drive.
2. Update the file paths in the code to match your Google Drive structure.

### Data Preprocessing

Preprocessing steps include:

1. Merging of the relevance and regulations datasets based on DocumentID.
2. Handling of duplicate entries.
3. Balancing of the dataset to address class imbalance.
4. Creation of derived features like regulator scores and document type scores.

## System Summary

Our document filtering system uses two main approaches:

1. **Simple Method:** Uses keyword matching and basic scoring to classify documents.
2. **Robust Method:** Incorporates multiple factors including regulator credibility, document type, language, and content relevance to provide a more nuanced classification.

The system works by:
- Analyzing document content for relevant keywords
- Considering the credibility of the document source (regulator)
- Evaluating the document type and language
- Combining these factors to produce a relevance score
- Classifying documents as relevant if their score exceeds a defined threshold

## Metrics

We chose the following metrics to evaluate our system:

- Accuracy: Measures overall correctness of classifications
- Precision: Indicates the proportion of true relevant documents among those classified as relevant
- Recall: Measures the proportion of truly relevant documents that were correctly identified
- F1 Score: Harmonic mean of precision and recall, providing a balanced measure of the model's performance

For the Simple Method:
- Accuracy: 0.1001
- Precision: 0.0992
- Recall: 0.9991
- F1 Score: 0.1804

These metrics were chosen because they provide a comprehensive view of the system's performance, balancing its ability to correctly identify relevant documents (recall) with its ability to avoid false positives (precision).

The Robust Method uses a scoring system, with documents scoring above 50 considered relevant.
- Accuracy: 0.9058
- Precision: 0.8864
- Recall: 0.0207
- F1 Score: 0.0404
- True Positive: 17767
- True Negative: 39
- False Positive: 5
- False Negative: 1847 

The distribution of scores for relevant documents:
- Mean: 54.06
- Median: 53.95
- Mode: 54.58

The second approach proves to be very accurate compare to the first simple approach

## Limitations

Known limitations of our system include:

1. Language Dependency: The system may perform better on English documents due to keyword selection.
2. Regulator Bias: The system may be biased towards well-known regulators, potentially missing important documents from lesser-known sources.
3. Keyword Reliance: Heavy reliance on predefined keywords may lead to missed relevant documents that use different terminology.
4. Lack of Context Understanding: The rule-based system doesn't understand the deeper context or implications of the text.

To mitigate these:
- Expand keyword lists to include multiple languages and synonyms
- Regularly update the regulator credibility scores
- Implement periodic human review to catch edge cases and update rules
- Consider incorporating more advanced NLP techniques in future iterations

## Human-in-the-Loop

Humans play crucial roles in our system:

1. Initial Setup: Experts define relevant keywords, set initial regulator credibility scores, and determine document type importance.
2. Threshold Setting: Humans decide on the relevance score threshold based on the desired balance between precision and recall.
3. Performance Monitoring: Regular human review of system performance, especially for edge cases or misclassified documents.
4. System Updates: Based on monitoring, humans update keywords, scoring rules, and other system parameters.
5. Final Verification: For critical applications, humans may perform a final review of documents classified as relevant by the system.

This human involvement ensures the system remains accurate, up-to-date, and aligned with current regulatory landscapes and organizational needs.
