# NewsBot Intelligence System

**Student:** Luis Adrian  
**Course:** ITAI 2373  
**Format:** Individual project   
**Status:** Working prototype

## Project Overview

NewsBot combines natural language processing techniques to classify
English news articles, analyze sentiment, extract named entities,
and explore grammatical patterns.

The system predicts five categories:
business, entertainment, politics, sport, and technology.

## Dataset

BBC News Classification, recommended and approved by the professor.

Source:
https://www.kaggle.com/competitions/learn-ai-bbc/data

The training CSV contains 1,490 articles.
After removing 50 duplicate texts, 1,440 articles remained.

Download `BBC News Train.csv` from Kaggle and upload it to Google Colab.
A Kaggle account and acceptance of competition rules may be required.

The CSV columns are renamed in the notebook:
- ArticleId → article_id
- Text → content
- Category → category

## Tools and Techniques

- Python, pandas, and NumPy
- NLTK: tokenization, stopwords, lemmatization, POS tagging, and VADER
- spaCy with en_core_web_sm: dependency parsing and entity recognition
- Scikit-learn: TF-IDF, classification pipelines, and evaluation
- Matplotlib and Seaborn: visualizations

## How to Run

1. Open `NewsBot_Intelligence_System_Luis_Adrian.ipynb`
   in Google Colab.
2. Run the installation and import cells.
3. Upload `BBC News Train.csv` using Colab's Files panel.
4. Check that the CSV path in the loading cell matches its location.
5. Execute the remaining cells in order.
6. Review the outputs and run the synthetic article demonstrations.

If Colab restarts, rerun the setup and preceding cells.
The CSV may need to be uploaded again.

Before repeating the model-training cell, rerun the feature-preparation
cell to restore the original sentiment values.

## Classification Results

The data was split into 1,152 training articles and 288 test articles,
using a stratified 80/20 split with random_state=42.

TF-IDF and numerical scaling were fitted inside model pipelines.
Three-fold cross-validation used only the training set.

| Model | Test Accuracy | Mean CV Accuracy |
|---|---:|---:|
| Naive Bayes | 93.75% | 95.49% |
| Logistic Regression | 94.10% | 94.53% |
| SVM | 95.83% | 96.79% |

SVM was selected using training cross-validation.
It correctly classified 276 of the 288 test articles.

These results apply to this BBC split and do not establish performance
on current news or other sources.

## Main Findings

- Entertainment had the highest average VADER sentiment score.
- Politics had the lowest average score, which was still slightly positive.
- Business had the largest total number of money and percentage mentions.
- Entity recognition detected 40,803 mentions with 12,071 distinct texts.

Entity mentions may repeat, and distinct texts do not necessarily
represent distinct real-world entities.

## Limitations

- The classifier always chooses one of the five available categories.
- Synthetic examples demonstrate functionality, not measured accuracy.
- VADER can misinterpret article tone and does not identify specific emotions.
- Article sentiment does not establish media bias or sentiment toward an entity.
- Entity boundaries and labels can be incorrect.
- Lowercase source text can affect grammatical and entity analysis.
- Basic lemmatization can produce incorrect word forms.
- SVM predictions can differ from the class with the highest
  estimated probability.
- This system is a prototype requiring further validation.

## Individual Contribution

I worked individually with my professor's approval.
My work included adapting the notebook to BBC, exploring and cleaning
the data, running NLP analyses, comparing classifiers, and testing
the integrated prototype.

I used AI assistance for code explanations, debugging, and adapting
the starter notebook.

## Project Files

- `NewsBot_Intelligence_System_Luis_Adrian.ipynb`: notebook and outputs.
- `README.md`: project overview and execution instructions.

`NewsBot_Reflection_Luis_Adrian.pdf`: two-page individual reflection.

## Remaining Work

- Complete outstanding analysis and written interpretations.
- Review the reflection and format it to exactly two pages.
- Run the entire notebook in a fresh Colab session.

## References

- Course-provided NewsBot student notebook and project instructions.
- BBC News Classification dataset linked above.
- spaCy: https://spacy.io/
- NLTK: https://www.nltk.org/
- Scikit-learn: https://scikit-learn.org/
