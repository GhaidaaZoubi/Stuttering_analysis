# Stuttering Analysis

## Introduction
This study delves into stuttering behaviors across diverse speech contexts using data sourced from the UCLASS archives. Through meticulous audio analysis, we aimed to elucidate stuttering frequency and severity, specifically focusing on accurately classifying speech situations based on acoustic features. Utilizing statistical analysis and machine learning models, we identified significant differences in stuttering severity between conversational speech and reading, even when considering reading and monologue as a unified category. Our findings underscore the pivotal role of speech context in informing stuttering interventions.

## Table of Contents
- [Data Description](#data-description)
- [Methodology](#methodology)
- [Results](#results)
- [Installation and Usage](#installation-and-usage)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)
- [Authors and Acknowledgments](#authors-and-acknowledgments)
- [Contact Information](#contact-information)
- [References and Further Reading](#references-and-further-reading)

## Data Description
The study utilized data from the UCLASS archives, comprising recordings of speakers who stutter across diverse speech situations (reading, conversation, monologue) and conditions (normal speaking, altered listening). These recordings were obtained from controlled laboratory studies, offering background information about speakers and recording conditions for in-depth analysis of stuttering behaviors across contexts.

## Methodology
We segment each audio file by its length and then extract feature values using specialized algorithms tailored to each feature type:
1. **Pitch**: Measured using Praat, we calculate the average fundamental frequency (pitch) across each audio segment.
2. **Intensity**: Calculated as the root mean square (RMS) amplitude of the segment, providing a measure of its loudness.
3. **Disfluency Duration**: Quantified by detecting pauses in speech segments using the short-time Fourier transform (STFT) energy envelope, summing the duration of identified pauses.
4. **Spectral Feature Scalar (MFCCs)**: Extracted from the segment's power spectrogram using Mel-frequency cepstral coefficients (MFCCs), averaged across coefficients to capture spectral characteristics.

For each segment, these feature values are averaged to obtain segment-level scores, and the mean of these scores across all segments within each audio file provides the final feature score used for analysis and comparison across recordings.

### Audio Stuttering Severity Score Calculation
To generate a comprehensive measure, we used weighted sums of the scores from different features. Finally, we normalized the combined score to ensure consistency across recordings, facilitating fair comparisons and interpretation.

### Data Split
The dataset was split 70-30 for training and testing to impartially assess model performance. We applied SVM, Random Forest, KNN, and Logistic Regression, each trained and tested using this split and further evaluated through cross-validation techniques for comprehensive assessment. Additionally, we performed these methods on data that included clusters for comparative analysis.

## Results
Significant differences in stuttering severity were identified through ANOVA analysis (F=9.049, P=0.00014), with post hoc tests revealing a notable distinction between conversation and reading contexts (P=0.0372).

Machine learning techniques including SVM, Random Forests, KNN, and logistic regression were applied to the data initially yielding modest accuracy (0.3804-0.5652). However, consolidating reading and monologue into one category and conversation into another significantly improved model performance (0.619-0.75), highlighting distinct stuttering patterns between solitary and interactive speech situations.

The inclusion of cluster variables did not substantially enhance accuracy, indicating limited additional predictive value in this context.

These findings underscore the nuanced relationship between speech context and stuttering severity, suggesting potential therapeutic implications. Addressing communication dynamics and social interaction may positively influence stuttering outcomes. Despite limitations, notably the small dataset (304 observations), this study provides valuable insights.

## Installation and Usage
1. Open the link to UCLASS: [UCLASS](https://www.uclass.psychol.ucl.ac.uk/)
2. Work with Release One and Release Two.
3. The background information files are converted from MDB files to CSV files to make them easy to work with (the CSV files are in the repository).
4. For each release, download the WAV zip files.
5. By terminal, open the Jupyter notebook making sure that the relevant files (all CSV and zip files) are in the Jupyter environment.
6. Run the code from the beginning in the order of the report.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Authors 
Ghaida Zoubi , Donia Shebrawi
