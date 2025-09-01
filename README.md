# Covary-encoder
This repository hosts the obfuscated runtime modules for the Covary-encoder logic, powered by [TIPs-VF](https://github.com/mahvin92/TIPs-VF) and with first-level protection using [CodeEnigma](https://github.com/KrishnanSG/codeenigma).

## About
The Covary-encoder implements a proprietary sequence encoding logic using the Translator-Interpreter Pre-seeding for Variable-length Fragments (TIPs-VF). Covary-encoder is released as obfuscated runtime ONLY. Each release has a validity period (per quarter). After expiration, users must update to the latest runtime to continue using Covary and other Covary-encoder-dependent implementations, manually or programmatically.

## Encoder architecture
The Covary-encoder was built on TIPs-VF developed by [De los Santos, 2025](https://doi.org/10.1101/2025.02.15.637782) for deep learning applications in synthetic biology. TIPs-VF is a _k-mer_-derived, non-overlapping, and frequency-independent encoding scheme. It represents genetic sequences based on the relative proximity and directional alignment of k-mer attributes while incorporating sequence, length, and positional awareness. TIPs-VF has demonstrated enhanced performance in truncation and fragmentation analysis, sequence homology detection, motif assessment, and splice junction identification using variable-length sequences.

![TIPs-VF model](https://github.com/user-attachments/assets/c4cee570-48e9-4d5a-9ed5-e2ef9e87b100)

## Covary-encoder updates
Updates and improvements in Covary-encoder are released in a per quarter basis, unless critical security and bug issues are found that warrant unscheduled updates. Covary-encoder updates will also include significant improvements made to TIPs-VF and CodeEnigma, if available.

## Obfuscation frequency
As part of security and performance upgrades on Covary-encoder, obfuscation frequency will also occur in a per quarter basis, unless specified in an obfuscation report/release.

## Sample implementation (_in Covary_)
### Clone
 ```
# Clone Covary-encoder in Google Colab
!git clone https://github.com/mahvin92/Covary-encoder.git
%cd Covary-encoder
!git sparse-checkout init --cone
!git sparse-checkout set Active README.md
 ``` 
### Runtime reconstruction
 ```
# Reconstruct the runtime directory
%cd Active
os.mkdir("codeenigma_runtime")
!mv /content/Covary-encoder/Active/__init__.py /content/Covary-encoder/Active/codeenigma_runtime
 ```
### Run Covary-encoder
 ```
# Feed your fasta file, containing the sequences to the Covary-encoder directory
!mv /content/[your fasta-formatted input] /content/Covary-encoder/
%cd /content/Covary-encoder/
!pip install /content/Covary-encoder/Active/codeenigma_runtime-*.whl

# Prevents premature exit
import sys, builtins
builtins.exit = sys.exit

sys.path.append("/content/Covary-encoder/Active")
import Covary_encoder
 ```

## Reporting
Comments and suggestions to improve Covary-encoder are welcome. If you find any bug or problem, please open an [issue](https://github.com/mahvin92/Covary-encoder/issues/new).

## Acknowledgements
Covary-encoder is powered by [TIPs](https://tips.chordexbio.com/) and [ChordexBio](https://chordexbio.com/), made with Python, and tested using Google Colab ❤️
