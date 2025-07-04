# Microbiome Sample Origin Predictor

## Overview

The **Microbiome Sample Origin Predictor** is a web-based tool designed for health practitioners to predict the body site origin (Mouth, Nasal, Skin, or Stool) of microbiome samples based on sequencing characteristics. It supports two input methods: manual entry of 27 sequencing features or automatic feature extraction from uploaded FastQ files. The tool leverages a neural network model built with TensorFlow.js to provide accurate predictions with confidence scores and detailed probability visualizations.

---

## Features

- **Manual Input**: Enter 27 sequencing features, including read statistics, GC content, quality metrics, nucleotide composition, and k-mer frequencies.
- **FastQ File Upload**: Upload `.fastq`, `.fq`, or `.txt` files for automatic feature extraction and prediction.
- **Interactive UI**: User-friendly interface with tooltips, real-time input validation, and smooth animations.
- **Prediction Results**: Displays predicted body site, confidence score, probability bars for each site, and detailed location descriptions.
- **Sample Data**: Includes a "Load Sample Data" button for testing with predefined values.
- **Responsive Design**: Optimized for desktop and mobile devices with adaptive layouts.
- **Notifications**: Provides success and error notifications for user actions.

---

## Installation

No installation is required. This is a **web-based application**.

Simply open the `index.html` file in a modern web browser (e.g., Chrome, Firefox, Edge) to run the application locally.

---

## Prerequisites

- A modern web browser with JavaScript enabled.
- Internet access to load external dependencies:
  - TensorFlow.js
  - Font Awesome
  - Google Fonts
- A TensorFlow.js model file (`model.json`) and its associated weight files, placed in a `tfjs/` directory relative to `index.html`.

---

## Setup

1. **Clone or download** this repository to your local machine.
2. Ensure the TensorFlow.js model files (`model.json` and weight files) are in the `tfjs/` directory.
3. Open `index.html` in your web browser.

---

## Usage

### **Manual Input**

- Navigate to the input section and fill in the 27 sequencing features:
  - Example: Number of Reads, Average GC Content, Quality Scores, etc.
- Hover over the `?` icons to see tooltips for each feature.
- Click **Predict Location** to generate a prediction.

### **FastQ File Upload**

- Click **Upload FastQ File** to open the upload modal.
- Drag and drop or browse to select a `.fastq`, `.fq`, or `.txt` file.
- The system will extract features automatically.
- Click **Predict from FastQ** to get the predicted result.

### **Sample Data**

- Click **Load Sample Data** to autofill the form with predefined values.

### **Results**

- The app displays:
  - Predicted body site
  - Confidence score
  - Probability bars for each body site
  - Description in the "About This Location" section

### **Reset**

- Click **Reset Form** to clear inputs and results.

---

## File Structure

```

microbiome-predictor/
├── index.html          # Main HTML file with UI and logic
├── tfjs/               # Directory for TensorFlow\.js model files
│   ├── model.json      # Neural network model architecture
│   └── ...             # Model weight files
└── README.md           # This documentation file

```

---

## Dependencies

- **TensorFlow.js** (v3.18.0): For client-side machine learning predictions (via CDN)
- **Font Awesome** (v6.0.0-beta3): For icons (via CDN)
- **Google Fonts**: Roboto and Open Sans for typography (via CDN)

---

## Model Details

### **Input Features (27 Total)**

- **Read Statistics**:
  - Number of Reads
  - Average Read Length
  - Read Length Deviation
- **GC Content**:
  - Average GC Content
  - GC Content Deviation
- **Quality Metrics**:
  - Average Quality Score
  - Quality Score Deviation
- **Nucleotide Composition**:
  - Proportions of A, T, G, C
- **K-mer Frequencies**:
  - Frequencies of 16 dinucleotide pairs (AA, AT, AG, AC, TA, TT, TG, TC, GA, GT, GG, GC, CA, CT, CG, CC)

### **Output**

- Probability scores for four body sites:
  - Mouth
  - Nasal
  - Skin
  - Stool

### **Standardization**

- Input features are standardized using **predefined mean and standard deviation** values before prediction.

### **Model Type**

- A neural network trained on thousands of microbiome samples
- Implemented in **TensorFlow.js** for browser-based prediction

---

## Limitations

- **Research Use Only**: Not intended for clinical decision-making.
- **File Size**: Large FastQ files may slow down browser performance.
- **Model Dependency**: Requires a valid TensorFlow.js model in `tfjs/` folder.
- **Browser Compatibility**: Best viewed on modern browsers with WebGL enabled.

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| **Model Loading Error** | Make sure the `model.json` and weight files are present in `tfjs/` |
| **Invalid FastQ File** | Check the file format and ensure it’s a valid `.fastq`, `.fq`, or `.txt` |
| **Prediction Errors** | Ensure all fields are filled with valid numbers (e.g., proportions between 0 and 1) |
| **Performance Issues** | Try using smaller FastQ files or use sample data for testing |

---

## Contributing

Contributions are welcome!  
Submit issues or pull requests for:
- Bug fixes
- New features
- Documentation improvements

---

## License

This project is licensed under the **MIT License**.  
See the [LICENSE](LICENSE) file for more details.

---

## Disclaimer

This tool is provided for **research purposes only**.  
Always consult qualified medical professionals for any clinical applications.
