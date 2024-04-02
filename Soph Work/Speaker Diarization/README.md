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

## 2. Speaker Diarization using Machine Learning

For larger datasets, manual annotation is not feasible. In such cases, we can use machine learning models to perform speaker diarization. Speaker diarization is the process of partitioning an input audio stream into homogeneous segments according to the speaker identity. First we used the audio features in, like banding according to the frequncies, to segment out the audio files. Then we used the K-means clustering algorithm to cluster the audio files into different speakers. 

A more roboust approach, used in the second and third dataset in this task, is using a pretrained model from Pyannote.

>> https://github.com/pyannote/pyannote-audio
Copyright (c) 2020 CNRS

We create a pipeline using the pretrained model to perform speaker diarization on the dataset. The results and the script file can be found in the "Results/Dataset 2" and "Results/Dataset 3" folders. The diarization script, "speaker_diarization.ipynb", first merges all the audio files into one, then segments the audio into different speakers, and finally prompts representative samples from the corpus to the user for manual annotation of gender and noise nuances. This is done in order to increase the accuracy of the results. 

The second dataset was taken from the following resource. The dataset chosen was Urdu language "Common Voice Delta Segment 17.0" which contained a total of 68 samples. 

* Please note that the diarization script "speaker_diarization.ipynb" has actually segmented the merged audio into a total of 89 segments, whereas it correctly identifies the total 7 speakers (all Male voice as identified). 
* The "speaker_diarization.jsonl" also provides the file name of the respective file that it clustered with a particular ascent of a speaker. Please note that no cross verification has been done, and occassional errors may be present.
* It is recommended that the script "speaker_diarization.ipynb" be run in a Python 3 environment in Google Colab with GPU acceleration (T4) enabled. The script may take a long time to run on a CPU. Additionally, several version mismatch errors were noticed when running the script in a local environment (tested on a Windows machine). The script was tested to work fine in Google Colab.

>> https://commonvoice.mozilla.org/en/datasets 
2024 Content available under a Creative Commons license.

The third dataset was taken from the following resource. It contains 400 utterances of four basic emotions: Angry, Happy, Neutral, and Emotion. There are 38 speakers (27 male and 11 female).

* Please note that the diarization script "speaker_diarization.ipynb" has actually segmented the merged audio into a total of 571 segments, whereas it incorrectly identifies the total 14 speakers. We anticipate that the model may possibly struggled differentiating between the different emotions, and may have missed different speaker ascents for different emotions. 
* A further manual annotation of the dataset is recommended to increase the accuracy of the results. A more robust possible solution also includes using the script seperately for each emotion and then combining the results (This was not done due in these results).
* Although the entire dataset was uploaded on a GPU T4 Google Collab instance, we also anticipate that the Colab environment might has incorrectly merged partial of the data, leading to malfunctioned results. A analysis of the dataset is recommended (The total duration seems to be incorrect, please see "summary.json").

>> https://www.kaggle.com/datasets/bitlord/urdu-language-speech-dataset 
(c) Wasif Baloch (Owner), Kaggle