# Weekly Project Progress Report

## Week Ending: 10-17-2023

### Week theme: Data collection and Preprocessing for the Translator Transformer

---

## 1. Overview

During this week we will be starting the second part of our final project: the translator model that can convert Spanish text to English text. This model is going to be built and trained from scrath by us.

---

## 2. Accomplishments

We were able to find the United Nations parallel corpus and convert part of this data into a pytorch vocabulary. This vocabulary in turn gave us the necessary indices for us to transform our training data (the UN parallel corpus) into a list of tensors for later use when making a DataLoader.

---
## 3. Challenges and Solutions

Any challenges encountered during the week and the solutions used to overcome them.

- Challenge 1: Loading huge datasets
  - Solution: We use small parts of the dataset while not losing much information.
- Challenge 2: RAM availability on Google Colab
  - Solution: We used Kaggle notebooks to mitigate this. We might shift to Dartmouth's RPC network.

---

## 4. Upcoming Tasks

A list of tasks and deliverables that are projected for the upcoming week.

- Train the translation model
- Validate and finetune it

---
## 5. Requests for Assistance

We might need assistance using Dartmouth's RPC network, but we don't require it as of now.
---

## 6. Additional Notes

There is no other information worth noting, but if it ever arises it will be shared with the Professor.

## 7. Google Colab link

Here is the [link to the Google Colab Notebook](https://colab.research.google.com/drive/1zQ8nwXlbIua2XEg9zxjAkoQnOgykd2EZ?usp=sharing)

—