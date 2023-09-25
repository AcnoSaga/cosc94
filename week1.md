# Weekly Project Progress Report

## Week Ending: 09-17-2023

### Project Name: COSC 094

---

## 1. Overview of the week
* Topics Covered: Overview of the overall project, Text preprocessing and encoding for TTS model.
* Github repository setup, including the README.md for the project.

---

## 2. Accomplishments

Tasks and milestones that have been accomplished over the week:

### 2.1. Github Repository Setup
We were able to setup the project's [Github repository](https://github.com/carlosguealv/cosc-094). This task helped us gain experience when it comes to creating a repository from the ground up and adding multiple collaborators to it.

### 2.2. README.md creation and first draft of the README document
We created a README.md file on the Github repository, to be certain that anyone who stumbles upon the project can understand both its purpose, the way it was created, and how to use it.

In the README.md file we wrote documentation to give an introduction to the project, and to express what the features of this project are.

Furthermore, we wrote a disclaimer that let viewers know that the README.md document is a work in progress, since we will be working on this project during the following weeks, which will hopefully help us give more insight into our project and the way it was made.

### 2.3. Text processing
Since the model can not process natural language directly, we need to convert it into something more understandable for the model.

We do this by encoding the text into discrete symbols under a phenome-based scheme.

Please note that we are using the Tacotron2 pretrained model to develop the text-to-speech system, and thus our preprocessing will correspond to the requirements of this model.

Firstly, we need the [`DeepPhonemizer`](https://github.com/as-ideas/DeepPhonemizer) library to be installed py pip3 using:
```bash
pip3 install deep-phonemizer
```

The `DeepPhonemizer` is our tool of choice to convert graphemes (letters in a written language) in English to phonemes (basic division of sound which is represented by graphemes).

Now, for encoding our text to a symbolic representation, we could use a phoneme-based encoding scheme.


To this end, we use a `torchaudio.pipelines` Bundle: [`TACOTRON2_WAVERNN_PHONE_LJSPEECH`](https://pytorch.org/audio/stable/generated/torchaudio.pipelines.TACOTRON2_WAVERNN_PHONE_LJSPEECH.html#torchaudio.pipelines.TACOTRON2_WAVERNN_PHONE_LJSPEECH), trained on the [LJSpeech dataset](https://keithito.com/LJ-Speech-Dataset/) using the [WaveRNN](https://github.com/fatchord/WaveRNN) vocoder.

```python
with torch.inference_mode():
    bundle = torchaudio.pipelines.TACOTRON2_WAVERNN_PHONE_LJSPEECH
    processor = bundle.get_text_processor()

    preppedText, durations = processor("We are making a new text to speech system")
```

This prepares the text for usage in our speech synthesis model.

This concludes our text preprocessing.

---
## 3. Challenges and Solutions

- Challenge 1: Selection of encoding scheme
  - Solution: We went with a phenome-based encoding as we realized it encapulated more data about actual sppech component than a basic character-based encoding.
- Challenge 2: Selection of vocoder
  - Solution: We did not have a particular bias for or against `Griffin-Lim` or `WaveRNN` but we were able to find better resources for `WaveRNN` online and thus decided to use that.
---
## 4. Upcoming Tasks

This is a list of tasks and deliverables that are projected for the upcoming week:

- Developing the Tacotron2 spectrogram generation pipeline.
- Writing the weekly Markdown report.
- Expand on the current README.md document, adding more information as to what we have been doing.
---
## 5. Requests for Assistance

We do not seem to need any further support at this point for our project.

---

## 6. Additional Notes

We hope for the best as the weeks progress, and hope we'll be able to complete the project without delays.

### [Link for Collab Notebook](https://colab.research.google.com/drive/1HMPFAtRou1qToG1qfFgrEsfe4_S4qIAB?usp=sharing)