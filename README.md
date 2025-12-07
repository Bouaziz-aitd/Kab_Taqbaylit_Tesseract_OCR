# Kabyle (Taqbaylit) Tesseract OCR Model
By Bouaziz Ait Driss

## Overview
Tesseract OCR model for Taqbaylit Kabyle language with support for 
special characters (ɣ, ɛ, ḍ, ṭ, ḥ, ṛ, ṣ, ẓ, ǧ, č).

## Starting Training Details
- Base model: eng (English)
- Training data: ~5,000 files
- Wordlist: 5,000+ Kabyle words
- Iteration count: ~10,000

## Starting Performance
Performance using python dedicated script test_cer.py
- Character Error Rate (CER): 30.56%
- Word Error Rate (WER): 72.94%
- Tested on average quality scanned documents

## Fine Tuning Training details
- Base model: kab (kabyle)
- Training data: 5,554 files
- Wordlist: 29,840 Kabyle words
- Iteration count: ~26,000

## Optimal Performance from Fine Tuning
Tesseract ended at checkpoint with  
BCER: 2.9% at iteration #26000

Performance using python dedicated script test_cer.py
- Character Error Rate (CER): 5.08%
- Word Error Rate (WER): 15.28%
- Tested on average quality scanned documents

## Installation
```bash
# Copy to Tesseract tessdata directory
sudo cp kab.traineddata /usr/share/tesseract-ocr/4.00/tessdata/
# Or for local user
cp kab.traineddata ~/.local/share/tessdata/
```
## Usage
```bash
tesseract input.png output -l kab
```
Note that the use in conda environment pytesseract is calling the model from conda environment (tessdatada) 
where Tesseract is installed and not from the Tesseract installed under windows.

## Data Quality Guidelines
- **Good quality scans** (300+ DPI, clear text): ~98% accuracy
- **Average quality scans** (150-300 DPI): ~84% word accuracy
- **Poor quality scans** (<150 DPI, skewed, faded): May require manual review

## Preprocessing Recommendations
- Deskew images
- Normalize lighting
- Use document or grayscale
- Minimum 150 DPI resolution

## License
[Apache 2.0]

## Citation
If you use this model, please cite:
[Bouaziz Ait Driss. (2025). *[Kabyle (Taqbaylit) Tesseract OCR model]* [OCR-model]. https://github.com/Bouaziz-aitd/Kab_Taqbaylit_Tesseract_OCR]

## Known Limitations
- Numbers: Limited training data
- May miss some old less used characters such as "Г" equivalent to "ɣ" and "ţ" equivalent to "tt"
- Performance degrades with poor scan quality
- Best results on printed text (not handwritten)

## Acknowledgments
- Based on Tesseract OCR
- Trained using Tesstrain 
- Trained over WSL on Windows 11
```
