# COSC 094 project week 6
### Overview of the week
This weeks marks the start of our model building process, which continues on till next week.

### Week 6: Model setup
We load the data we had pickled before (to save us a lot time). We then define a custom positional encoder which encodes comparative position within our sentences. Then, we set up our Transformer's training loop, which will be trained over the next week.

We set up an ```nn.Module``` class for our positional encoding algorithm.

We used an adapter to convert input tokens to transformer ingestable embeddings.

Once we were setup with processing the tokens for our transformer, we created the model itself. We neede to create a mask to ensure that our model ignores padding tokens and to also ensure our model does not look into future words when making a prediction for the current word's meaning. We used matrices to this end, with the padding mask matrices taking values of True and False depending on whether a token is a padding index or not. On the other hand, we prevented our model from looking into future words by creating a a triangular matrix so that in each row we can take one more word than in the last row. Then, we initialized the transformer model on random parameters to then set up the training loop for our model.

## 3. Challenges and Solutions

Any challenges encountered during the week and the solutions used to overcome them.

- Challenge 1: Training on huge datasets
  - Solution: We use batching to dissect the dataset into small chunks.
- Challenge 2: The trained features could not figure out positions
  - Solution: We use a positional encoder to solve the problem.

---

## 4. Upcoming Tasks

A list of tasks and deliverables that are projected for the upcoming week.

- Run the training loop

---
## 5. Requests for Assistance

We might need assistance using Dartmouth's RPC network, but we don't require it as of now.