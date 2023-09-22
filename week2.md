# Weekly Project Progress Report

## Week Ending: 09/24/2023

### Week theme: Tacotron2-based spectrogram generation pipeline

---

## 1. Overview of the week

This week, we continue work on our tex-to-speech model, for which we created a phoneme-based text encoding last week. In this week's submission, we will generate an audio spectrogram from the generated phoneme encodings, which will later be used to actually generate the final audio output, which, due to the nature of the spectrograms we use (mel spectrograms), will be well-suited for encoding human speech.

---

## 2. Accomplishments

### 2.1. Tacotron2-based spectogram generation pipeline
After preprocessing the text graphemes, our program needs to figure out the sound frequencies necessary to generate the audio spectrogram that correspond to the language we inputted.

The type of spectrogram we want is a Mel spectrogram, which is a non-linear spectrogram which transforms pitch such as pitch changes feel linear to the human ear. This allows us to create a much more natural sounding audio output which would mimic human voice.

To do this, we use the pre-trained Tacotron2 model (which directly converts encoded characters to mel-spectrograms) to make an inference based on the preppedText tensor and the durations for each phoneme. For testing purposes we also use the matplotlib library to generate a spectogram based on the inferences from the Tacotron2 model:
```python
with torch.inference_mode():
    tac2 = bundle.get_tacotron2()
    inference = tac2.infer(preppedText, durations)
    melSpectro = inference[0]


import matplotlib.pyplot as plt
plt.imshow(melSpectro[0])
```
This creates a mel-spectrogram of the encoded words, ready for use for the purpose of audio generation.

This is an intermediate step in the process that starts with encoding text, and will subsequently end with the generation of the final audio output.

---

## 3. Challenges and Solutions

Here are the challenges encountered during the week and the solutions used to overcome them.
* Selecting which tool to use for spectogram generation.
	* After some consideration we realized that using the Tacotron2 model would be the best option in this case, since we had already initialized a Tacotron2 pipeline for the word preprocessing, and this model was also the one recommended by Pytorch.

---

## 4. Upcoming Tasks
This is a list of tasks and deliverables that are projected for the upcoming week:
* Converting the spectrogram to audio.
* Chosing and comparing of the different options we have for audio creation/waveform generation.
* Writing the weekly Markdown report.
---
## 5. Requests for Assistance
We do not seem to need any further support at this point for our project.

---

## 6. Additional Notes

There is no other information worth noting, but if it ever arises it will be shared with the Professor.

## 7. Google Colab link
Here is the [link to the Google Colab Notebook](https://colab.research.google.com/drive/1zQ8nwXlbIua2XEg9zxjAkoQnOgykd2EZ?usp=sharing)
