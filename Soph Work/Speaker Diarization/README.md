DCW Task 2: Speaker Diarization

# Introduction, Task

Given a dataset containing several samples of audio files (.wav, .mp3), we are required to list the number of distinct speakers in the entire dataset, including their gender/noise information, and the duration to which the dataset plays. 

# Methodology

## 1. Manual Annotation

Particularly useful for smaller datasets, the manual annotation method involves listening to the audio files and noting down the speaker, and relevant attributes like gender and noise in each segment. We did manual annotation for the first dataset. This annotation involved running a python script "manual_annotation.ipynb" which plays the audio file one by one and asks the user to input the corresponding attributes. It then compiles all the entries into a JSON Line format and saves it as "manual_annotation.jsonl", and publishes a summary of the dataset.

The dataset was taken from the following resource. The dataset contains 708 samples. The results and the "manual_annotation.ipynb" script file can be found in the "Results/Dataset 1" folder.

It is highly recommended that the script be run in a VS environment in Windows OS. Tests on other environments have not been conducted. Google Collab does not support the audio playback feature through sounddevice, for which an alternative approach has been provided in the script.

>> https://cle.org.pk/software/ling_resources/phoneticallyrichurduspeechcorpus.htm
(c) 2017 Center for Language Engineering, Al-Khawarizmi Institute of Computer Science, University of Engineering and Technology, Lahore, Pakistan