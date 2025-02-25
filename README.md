# VulnCrypt

VulnCrypt is a machine learning-based framework for detecting vulnerabilities in C code. It leverages the Juliet Test Suite for training and employs an LSTM model to classify functions as "good" (secure) or "bad" (vulnerable). This project is inspired by **Project Achilles**, further extending its capabilities with additional features and improved performance.

## Features

- **Data Preprocessing**: Automated extraction and tokenization of functions from raw C files.
- **Model Training**: Customizable LSTM-based architecture for vulnerability classification.
- **Prediction**: Analyze new C code files to classify function safety.
- **Metrics Visualization**: Evaluate and visualize model accuracy, precision, recall, and F1-score.

## Directory Structure

```
VulnCrypt/
├── src/
│   ├── data_processing/
│   │   ├── build_vocab.py          # Build vocabulary from processed data
│   │   ├── data_preprocessing.py   # Extract and tokenize functions from raw C code
│   │   ├── encode_sequences.py     # Convert tokenized sequences to model-readable format
│   │   ├── extract_data.py         # Extract raw function data
│   │   ├── split_data.py           # Split data into training and validation sets
│   │   ├── tokenize_data.py        # Tokenize raw C code files
│   │   └── vocab.py                # Vocabulary helper functions
│   ├── model/
│   │   ├── evaluation.py           # Evaluate model performance
│   │   ├── model.py                # Define the LSTM model architecture
│   │   ├── predict.py              # Predict vulnerabilities in new C code
│   │   ├── some_code.c             # Example C file for testing predictions
│   │   ├── test.py                 # Unit tests for the framework
│   │   ├── train.py                # Train the LSTM model
│   │   └── visualize_metrics.py    # Plot confusion matrices and other metrics
├── tests/                          # Test cases for validating the framework
├── venv/                           # Virtual environment directory
├── .gitignore                      # Git ignore file
├── LICENSE                         # License file
├── README.md                       # Project documentation
├── cli.py                          # Command-line interface for VulnCrypt
└── requirements.txt                # Python dependencies
```

## Getting Started

### Prerequisites

- Python 3.8+
- Virtual environment (recommended)
- Juliet Test Suite (C test cases for vulnerability analysis)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/ame0101/VulnCrypt.git
   cd VulnCrypt
   ```

2. Create a virtual environment and activate it:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### Usage

#### Preprocess Data
Extract and tokenize functions from raw C code:
```bash
python src/data_processing/data_preprocessing.py
```

#### Split Data
Split the processed functions into training and validation sets:
```bash
python src/data_processing/split_data.py
```

#### Train the Model
Train the LSTM model using the preprocessed data:
```bash
python src/model/train.py
```

#### Predict Vulnerabilities
Analyze a new C file for potential vulnerabilities:
```bash
python src/model/predict.py <path_to_c_file>
```

#### Evaluate Model Performance
Run evaluation scripts to visualize confusion matrices and other metrics:
```bash
python src/model/visualize_metrics.py
```

## Example

To test predictions on an example file:
```bash
python src/model/predict.py src/model/some_code.c
```

## Progress and Next Steps
The confusion matrix shows strong classification performance, correctly identifying 6,083 "good" functions while minimizing false positives (only 17 misclassified). However, 1,370 "bad" functions were misclassified as "good," indicating room for improvement in detecting security vulnerabilities. To enhance accuracy, I have integrated SARD C code datasets into the training set, expanding the diversity of vulnerability patterns the model learns. This expansion aims to reduce false negatives and improve generalization across real-world insecure code structures.

<img width="465" alt="Screenshot 2024-12-18 at 1 58 48 PM" src="https://github.com/user-attachments/assets/bf774bf8-c9aa-4f44-8117-28b359b7455a" />


To further improve accuracy, I plan to fine-tune the model using data augmentation techniques and additional handcrafted features that better capture vulnerability patterns. Additionally, integrating a confidence-based threshold for uncertain classifications will help reduce misclassifications and prioritize high-risk code for manual review.

This project is crucial for automating vulnerability detection in C code, helping developers and security researchers identify insecure patterns early, reducing the risk of exploitable security flaws in software.


## Contribution

Contributions are welcome! Feel free to fork this repository, create a feature branch, and submit pull requests. Please ensure your code adheres to the project structure and passes all tests.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Acknowledgment

This project draws inspiration from **Project Achilles**, a pioneering effort in leveraging machine learning for vulnerability detection.
