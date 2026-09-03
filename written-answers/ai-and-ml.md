<!-- TOC START -->
**Table of Contents** — 11 subtopics · 43 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Artificial Intelligence & Expert Systems](#artificial-intelligence--expert-systems-8) | 8 |
| 2 | [Deep Learning & Neural Networks (ANN, CNN, RNN)](#deep-learning--neural-networks-ann-cnn-rnn-8) | 8 |
| 3 | [Machine Learning Paradigms (Supervised vs Unsupervised)](#machine-learning-paradigms-supervised-vs-unsupervised-6) | 6 |
| 4 | [Model Evaluation & Datasets](#model-evaluation--datasets-5) | 5 |
| 5 | [Supervised Learning (Decision Trees)](#supervised-learning-decision-trees-4) | 4 |
| 6 | [Generative AI & Explainable AI (XAI)](#generative-ai--explainable-ai-xai-4) | 4 |
| 7 | [Advanced Machine Learning & Deep Learning (RL, DL, Federated Learning)](#advanced-machine-learning--deep-learning-rl-dl-federated-learning-3) | 3 |
| 8 | [Search Algorithms (Informed vs Uninformed Search)](#search-algorithms-informed-vs-uninformed-search-2) | 2 |
| 9 | [Overfitting, Underfitting & Model Generalization](#overfitting-underfitting--model-generalization-1) | 1 |
| 10 | [Association Rule Learning (Market Basket Analysis)](#association-rule-learning-market-basket-analysis-1) | 1 |
| 11 | [Clustering & Unsupervised Learning (K-Means, Hierarchical)](#clustering--unsupervised-learning-k-means-hierarchical-1) | 1 |

<!-- TOC END -->

---

## Artificial Intelligence & Expert Systems (8)

1. **What is Artificial Intelligence?** *[Mongla Port Authority Assistant Programmer 2023 compact it 573 (ET: N/A)]*

   Answer: Artificial Intelligence (AI) is the branch of computer science that builds machines able to do tasks that normally need human intelligence — learning, reasoning, understanding language and taking decisions.

   - An AI system takes input from sensors, processes it with an algorithm or a trained model, and produces an action or an answer.
   - Main branches: machine learning, natural language processing (NLP), computer vision, robotics, expert systems.
   - Two approaches: symbolic AI uses rules written by people; machine learning finds the rules itself from data.

   Types by capability
   - Narrow AI (ANI) — does one fixed task, like a spam filter or face unlock. All AI today is of this type.
   - General AI (AGI) — can do any intellectual task a human can. Still research work.
   - Super AI — ability beyond humans. Only a theory now.

   - Uses: search engine ranking, chatbots, fraud detection in banks, medical image diagnosis, self-driving cars.

2. **An artificial intelligence is an agent is an entity that continuously revious its enviornment.....** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 449 (ET: BUET)]*

3. **Write PEAS for (a) Auto taxi (b) Automatic clinical test.** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 457 (ET: BUET)]*

   Answer: PEAS is the standard way to describe the task environment of a rational agent. It stands for Performance measure, Environment, Actuators and Sensors.

   | PEAS | (a) Auto taxi | (b) Automatic clinical test |
   |---|---|---|
   | Performance measure | Safe trip, fast, legal, comfortable ride, minimum fuel, maximum profit | Correct diagnosis, healthy patient, low test cost, fast report |
   | Environment | Roads, traffic, pedestrians, traffic signals, weather, passengers | Patient, blood/urine sample, hospital lab, doctor, hospital database |
   | Actuators | Steering, accelerator, brake, gear, indicator, horn, display screen | Test report display, alert to doctor, sample handling arm, printer |
   | Sensors | Camera, LIDAR, GPS, speedometer, odometer, engine sensor, microphone | Blood analyser, temperature sensor, keyboard input of symptoms, patient history |

   - Performance measure says what "success" means for the agent.
   - Environment is the world the agent works in.
   - Actuators are the parts it acts with; sensors are the parts it perceives with.

4. **Intelligence can not be measured only by intelligence test because it is related to other subjects. (True or False)** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)]*

   Answer: True.

   - An IQ test checks only a few skills such as logic, pattern finding and memory. Intelligence also covers creativity, emotional skill, language and practical problem solving, so one test cannot measure all of it.

5. **Machine learning is a subset of cloud computing that can be built AI-Based. (True or False).** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)], [BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

   Answer: False.

   - Machine learning is a subset of Artificial Intelligence, not of cloud computing.
   - Correct order: AI > Machine Learning > Deep Learning. Cloud computing is only a platform used to train and run ML models; it does not contain ML.

6. **What is the father of AI?** *[BARC Data Entry Officer 10.09.2022 compact it 703 (ET: N/A)]*

   Answer: John McCarthy is called the Father of Artificial Intelligence.

   - He coined the term "Artificial Intelligence" and organised the Dartmouth Conference of 1956, which started AI as a subject. He also created the LISP programming language.

7. **(i) ‘Knowledge’ কী? Human Knowledge কে Computer এ প্রকাশ করার একটি flow diagram দেখান।** *[BPSC Assistant Network Engineer 2020 compact it 952 (ET: N/A)]*

   Answer: Knowledge is processed information together with the rules and relations that let a system reason and take a decision. Data is raw, information is data with meaning, and knowledge is information a system can act on.

   Types of knowledge
   - Declarative — facts, "what is true" (Dhaka is the capital of Bangladesh).
   - Procedural — "how to do" a task (steps to withdraw money).
   - Heuristic — rule of thumb from experience.
   - Meta knowledge — knowledge about knowledge.

   Putting human knowledge into a computer is called knowledge representation. It is done with IF-THEN rules, semantic networks, frames, ontologies or predicate logic.

   ```mermaid
   flowchart TD
       A[Human Expert Knowledge] --> B[Knowledge Acquisition]
       B --> C[Knowledge Representation<br/>rules, frames, logic]
       C --> D[(Knowledge Base)]
       D --> E[Inference Engine]
       U[User Query] --> E
       E --> F[Decision / Answer]
   ```

   - Knowledge acquisition collects facts and rules from the expert or from documents.
   - Knowledge representation converts them into a machine-readable form.
   - The knowledge base stores them; the inference engine applies the rules to a user query and produces the answer.

8. **Who is Largely credited for breaking the German Enigma codes that provided a foundation for artificial intelligence?** *[Sadharan Bima Corporation Programmer/ AP/AME 2020 compact it 1002 (ET: DU)]*

   Answer: Alan Turing.

   - He broke the German Enigma cipher at Bletchley Park during World War II. His work on the Turing machine and the Turing Test became a foundation of computer science and AI.

## Deep Learning & Neural Networks (ANN, CNN, RNN) (8)

1. **(c) What is activation function in Deep Neural Network? What is the usability of this?** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*

   Answer: An activation function is a small mathematical function placed at the output of every neuron. It takes the weighted sum of the inputs and decides how strongly that neuron will fire.

   - For a neuron: `output = f(w1x1 + w2x2 + ... + b)`, where `f` is the activation function.

   Usability
   - Adds non-linearity. Without it the whole network, however deep, collapses into one linear equation and cannot learn curved patterns.
   - Keeps the output inside a usable range, so values do not blow up layer after layer.
   - Must be differentiable, because backpropagation needs its derivative to update the weights.
   - Decides which neurons stay active, which helps the network pick useful features.

   Common ones
   - Sigmoid — squeezes output to 0-1. Used in binary classification output.
   - Tanh — output -1 to +1, zero-centred.
   - ReLU — `f(x) = max(0, x)`. Fast, the default for hidden layers.
   - Softmax — turns outputs into probabilities that sum to 1. Used for multi-class output.

2. **What does the axon of neural network do?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

   Answer: The axon is the output line of a neuron. It carries the signal produced by the neuron away to the next neurons.

   - In a biological neuron, dendrites receive signals, the cell body sums them, and the axon transmits the result to other neurons through synapses.
   - In an artificial neural network, the axon matches the output connection of a node — it passes the activation value, multiplied by the connection weight, to the neurons of the next layer.

3. **Write difference between machine learning and deep learning.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 681 (ET: N/A)]*

   Answer: Deep learning is a subset of machine learning that uses multi-layer neural networks.

   | Point | Machine Learning | Deep Learning |
   |---|---|---|
   | Feature extraction | Done by hand — a human picks the features | Learned automatically by the network |
   | Data needed | Works well on small to medium data | Needs very large data |
   | Hardware | Runs on a normal CPU | Usually needs a GPU/TPU |
   | Structure | Algorithms like decision tree, SVM, KNN | Neural networks with many hidden layers |
   | Training time | Short (minutes to hours) | Long (hours to days) |
   | Interpretability | Easier to explain the result | Mostly a black box |
   | Typical use | Loan default prediction, spam filter | Image recognition, speech, machine translation |

4. **What is Deep learning?** *[BARC Data Entry Officer 10.09.2022 compact it 703 (ET: N/A)]*

   Answer: Deep learning is a branch of machine learning that uses artificial neural networks with many hidden layers to learn patterns straight from raw data.

   - "Deep" means the network has several hidden layers stacked one after another.
   - Each layer learns a higher-level feature: early layers find edges, middle layers find shapes, later layers find whole objects.
   - It does its own feature extraction, so no manual feature engineering is needed.
   - It needs large datasets and heavy computing power (GPU).
   - Main types: CNN for images, RNN and LSTM for sequences and text, Transformer for language.
   - Uses: face recognition, speech to text, machine translation, self-driving cars, medical image analysis.

5. **What is Artificial Neural Network (ANN)? Difference between deep learning technique and Traditional machine learning technique.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 856 (ET: N/A)]*

   Answer: An Artificial Neural Network (ANN) is a computing model built from layers of connected nodes called neurons, copying the way the human brain processes signals.

   - Structure: input layer → one or more hidden layers → output layer.
   - Every connection carries a weight. A neuron sums its weighted inputs, adds a bias, applies an activation function and passes the result on.
   - It learns by backpropagation — compare output with the correct answer, then adjust weights to reduce the error.

   Deep learning vs traditional machine learning

   | Point | Traditional ML | Deep Learning |
   |---|---|---|
   | Features | Selected by a human expert | Learned by the model itself |
   | Data size | Good result on limited data | Needs a very large dataset |
   | Layers | Shallow model, no or one hidden layer | Many hidden layers |
   | Compute | CPU is enough | GPU needed |
   | Explainability | Result can be traced | Hard to explain |

6. **Write LSTM gates name in AI.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 858 (ET: N/A)]*

   Answer: LSTM (Long Short-Term Memory) has three gates.

   - Forget gate — decides what part of the old cell state to throw away.
   - Input gate — decides what new information to store in the cell state.
   - Output gate — decides what part of the cell state to send out as the hidden state.

   - All three use a sigmoid layer, which gives a value between 0 (block fully) and 1 (pass fully). These gates let LSTM hold information for long sequences and solve the vanishing gradient problem of a plain RNN.

7. **Draw the single layer of ANN.** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 880 (ET: BUET)]*

   Answer: A single layer ANN (a perceptron) has only an input layer and an output layer — no hidden layer.

   ```mermaid
   flowchart LR
       X1[Input x1] -->|w1| S((Sum + bias))
       X2[Input x2] -->|w2| S
       X3[Input x3] -->|w3| S
       S --> A[Activation f]
       A --> Y[Output y]
   ```

   - Each input `x` is multiplied by its weight `w`, and all products are added with a bias `b`.
   - Net input: `net = w1x1 + w2x2 + w3x3 + b`
   - Output: `y = f(net)`, where `f` is a step or sigmoid activation function.
   - Weights are updated during training so the output moves closer to the target value.
   - A single layer can only separate linearly separable data, so it cannot solve the XOR problem.

8. **What is artificial Neural Network (ANN)? Based on ANN, describe input & hidden layer, weight and activation function.** *[ICT Ministry Assistant Programmer 2017 compact it 1237-1238 (ET: N/A)]*

   Answer: An Artificial Neural Network is a model made of layers of connected neurons that learns a mapping from input to output by adjusting the weights of its connections.

   ```mermaid
   flowchart LR
       I1[Input layer] --> H1[Hidden layer 1]
       H1 --> H2[Hidden layer 2]
       H2 --> O[Output layer]
   ```

   (a) Input layer
   - Takes the raw features and passes them into the network. It does no calculation.
   - Number of nodes = number of input features. For a 28x28 image, 784 nodes.

   (b) Hidden layer
   - Sits between input and output and does the actual processing.
   - Each hidden neuron takes a weighted sum of the previous layer, applies an activation function and passes it forward.
   - More hidden layers let the network learn more complex patterns; a network with many of them is called a deep network.

   (c) Weight
   - A number on each connection that shows how important that input is.
   - Net input of a neuron: `net = Σ(wi × xi) + b`, where `b` is the bias.
   - Training means changing these weights by backpropagation and gradient descent until the error is small.

   (d) Activation function
   - Decides the output of a neuron from its net input and adds non-linearity.
   - Common choices: ReLU in hidden layers, sigmoid for binary output, softmax for multi-class output.
   - Without it, the whole network would behave like a single linear equation.

## Machine Learning Paradigms (Supervised vs Unsupervised) (6)

1. **(a) Describe the following terms:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*
 * **(i) Supervised learning**
 * **(ii) Unsupervised learning**
 * **(iii) Reinforcement learning**

   Answer:

   (i) Supervised learning
   - The model is trained on labelled data — every input already carries its correct output.
   - It learns the mapping `input → output` and then predicts the label for new, unseen data.
   - Two kinds: classification (output is a class, e.g. spam / not spam) and regression (output is a number, e.g. house price).
   - Algorithms: linear regression, logistic regression, decision tree, SVM, KNN, Naive Bayes.

   (ii) Unsupervised learning
   - The data has no labels. The model finds hidden structure on its own.
   - Main tasks: clustering (group similar items) and association (find items that occur together).
   - Algorithms: K-Means, hierarchical clustering, DBSCAN, PCA, Apriori.
   - Example: grouping bank customers into segments by spending behaviour.

   (iii) Reinforcement learning
   - An agent learns by acting in an environment and receiving a reward or a penalty for each action.
   - There is no labelled dataset; the agent improves by trial and error to maximise total reward.
   - Parts: agent, environment, state, action, reward, policy.
   - Algorithms: Q-learning, SARSA, Deep Q-Network. Example: game playing, robot walking, self-driving car.

2. **a) Define the term "Data Mining". Explain supervised and unsupervised classification with suitable example.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*

   Answer: Data mining is the process of finding useful patterns, rules and relationships hidden inside a large dataset, so that the result can support a business decision.

   - Steps: data cleaning → integration → selection → transformation → mining → pattern evaluation → knowledge presentation.
   - Common tasks: classification, clustering, association rule mining, regression, outlier detection.

   Supervised classification
   - Training data is labelled — each record already has its class.
   - The model learns the boundary between the classes and then labels new records.
   - Example: a bank has old loan records marked "defaulter" and "non-defaulter". A decision tree is trained on them and then predicts whether a new applicant will default.

   Unsupervised classification (clustering)
   - Data has no class labels. The algorithm groups records by similarity.
   - The analyst looks at the groups afterwards and decides what each one means.
   - Example: K-Means groups bank customers into three clusters by balance and transaction count, and the bank later names them high, medium and low value customers.

3. **Briefly explain supervised learning, unsupervised learning & reinforcement learning.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1341 (ET: N/A)]*

   Answer:

   - Supervised learning — learns from labelled data. Input and correct output are both given, and the model learns to predict the output for new input. Used for classification and regression. Example: predicting whether an email is spam.
   - Unsupervised learning — learns from unlabelled data. The model finds hidden groups or patterns by itself. Used for clustering and association. Example: grouping customers by buying habit.
   - Reinforcement learning — an agent learns by doing. Each action gives a reward or a penalty, and the agent changes its policy to collect the most reward over time. Example: a robot learning to walk, or a program learning to play chess.

4. **(b) What is the difference between supervised and unsupervised learning? Explain with examples.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)], [SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)], [DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

   Answer:

   | Point | Supervised learning | Unsupervised learning |
   |---|---|---|
   | Input data | Labelled — correct output is given | Unlabelled — no output given |
   | Goal | Predict the output for new data | Find hidden structure in the data |
   | Tasks | Classification, regression | Clustering, association, dimension reduction |
   | Algorithms | Decision tree, SVM, KNN, linear regression | K-Means, DBSCAN, PCA, Apriori |
   | Accuracy check | Easy — compare prediction with the true label | Hard — no true label to compare with |
   | Human effort | High, labelling costs time and money | Low, raw data is used directly |

   Examples
   - Supervised: a dataset of 10,000 emails already marked spam or not spam. The model learns from them and classifies a new email.
   - Unsupervised: a dataset of 10,000 customers with no labels. K-Means splits them into groups of similar spending behaviour, and the bank decides later what each group means.

5. **Given some features of diabetic patient dataset with some labeled data. From this it can be predict whether this patient is diabetic or not. Is this supervised learning or unsupervised learning problem. Explain in one sentence.** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 433 (ET: BUET)]*

   Answer: It is a supervised learning problem — the dataset already carries the correct label (diabetic / not diabetic), so the model learns from those labelled examples to predict the class of a new patient.

   - More exactly it is binary classification, since the output has only two possible classes.

6. **What do you mean by machine learning? Name three machine learning application in our daily life?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 680 (ET: N/A)]*

   Answer: Machine learning is a branch of Artificial Intelligence in which a computer learns patterns from data and improves its performance with experience, instead of being programmed with fixed rules for every case.

   - The program is given data, it builds a model from that data, and the model then makes predictions on new data.
   - Types: supervised, unsupervised and reinforcement learning.

   Three daily-life applications
   - Email spam filtering — Gmail classifies an incoming mail as spam or inbox.
   - Product and video recommendation — Daraz, YouTube and Netflix suggest items from past behaviour.
   - Bank fraud detection — a card transaction that does not match the customer's usual pattern is flagged and blocked.

## Model Evaluation & Datasets (5)

1. **Write down the Role of Validation set in ML.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1448 (ET: N/A)]*

   Answer: The validation set is the part of the data kept aside to tune the model and to check how it performs on data it did not train on, before the final test.

   - Hyperparameter tuning — choose learning rate, number of layers, tree depth, value of K, and so on.
   - Model selection — compare several models and keep the one that scores best on validation.
   - Detects overfitting — if training accuracy keeps rising while validation accuracy falls, the model is memorising the training data.
   - Early stopping — training is stopped at the epoch where validation error is lowest.
   - Keeps the test set clean, so the final test score stays an honest estimate of real-world performance.
   - Usual split: 70% train, 15% validation, 15% test. When data is small, k-fold cross-validation is used instead.

2. **(b) Given following values:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*
 * **True Positive \text{(TP)} = 560**
 * **True Negative \text{(TN)} = 330**
 * **False Positive \text{(FP)} = 60**
 * **False Negative \text{(FN)} = 50**
**Calculate the following: (i) Accuracy (ii) Precision (iii) Recall (iv) F1 Score**

   Answer:

   Given: TP = 560, TN = 330, FP = 60, FN = 50
   Total samples = 560 + 330 + 60 + 50 = 1000

   (i) Accuracy
   - Formula: `Accuracy = (TP + TN) / (TP + TN + FP + FN)`
   - `= (560 + 330) / 1000 = 890 / 1000 = 0.89`
   - Accuracy = 0.89 = 89%

   (ii) Precision
   - Formula: `Precision = TP / (TP + FP)`
   - `= 560 / (560 + 60) = 560 / 620 = 0.9032`
   - Precision = 0.9032 = 90.32%

   (iii) Recall
   - Formula: `Recall = TP / (TP + FN)`
   - `= 560 / (560 + 50) = 560 / 610 = 0.9180`
   - Recall = 0.9180 = 91.80%

   (iv) F1 Score
   - Formula: `F1 = 2 × (Precision × Recall) / (Precision + Recall)`
   - `= 2 × (0.9032 × 0.9180) / (0.9032 + 0.9180)`
   - `= 2 × 0.8292 / 1.8212 = 1.6584 / 1.8212 = 0.9106`
   - F1 Score = 0.9106 = 91.06%

   Final answer
   - Accuracy = 89%, Precision = 90.32%, Recall = 91.80%, F1 Score = 91.06%

3. **b) How can we validate and check reliability of a machine learning model?** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*

   Answer: A model is validated by testing it on data it has never seen, and by checking that the score stays stable across different splits of the data.

   (a) Data splitting
   - Hold-out method — split into train, validation and test sets (about 70:15:15).
   - K-fold cross-validation — split the data into k parts, train on k-1 and test on the remaining one, repeat k times and take the average score. This removes luck from a single split.
   - Stratified k-fold — keeps the class ratio same in every fold, needed for imbalanced data.

   (b) Evaluation metrics
   - Classification: accuracy, precision, recall, F1 score, confusion matrix, ROC-AUC.
   - Regression: MAE, MSE, RMSE, R-squared.
   - For imbalanced data do not trust accuracy alone; use precision, recall and F1.

   (c) Reliability checks
   - Compare training and validation error — a big gap means overfitting, both high means underfitting.
   - Plot a learning curve to see whether more data would help.
   - Test on a fresh dataset from a different time period to check that the model still holds.
   - Watch for data leakage, where test information reaches the training set.
   - After deployment, monitor for data drift and retrain when accuracy falls.

4. **You are a designing a machine learning model for a binary classification problem. The model has three features: f1, f2, f3. Derive the objective and loss function for this problem.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 746 (ET: N/A)]*

   Answer: For binary classification with three features, the standard model is logistic regression.

   Step 1 - linear combination of the features
   - `z = w1·f1 + w2·f2 + w3·f3 + b`
   - Here `w1, w2, w3` are weights and `b` is the bias.

   Step 2 - convert z into a probability with the sigmoid function
   - `ŷ = σ(z) = 1 / (1 + e^(-z))`
   - `ŷ` is the predicted probability that the sample belongs to class 1. Output is 1 if `ŷ ≥ 0.5`, else 0.

   Step 3 - loss function for one sample (binary cross-entropy / log loss)
   - `L(y, ŷ) = -[ y·log(ŷ) + (1 - y)·log(1 - ŷ) ]`
   - If `y = 1` the loss is `-log(ŷ)`; if `y = 0` it is `-log(1 - ŷ)`. A confident wrong answer is punished heavily.

   Step 4 - cost function over all m samples
   - `J(w, b) = -(1/m) · Σ [ yi·log(ŷi) + (1 - yi)·log(1 - ŷi) ]`, for i = 1 to m

   Step 5 - the objective
   - Objective: find the weights and bias that make the cost smallest.
   - `min J(w, b)` over `w1, w2, w3, b`
   - With L2 regularization: `J(w, b) + (λ / 2m) · Σ wj²`, which keeps the weights small and reduces overfitting.

   Step 6 - how the minimum is reached
   - Gradient descent updates each weight: `wj := wj - α · ∂J/∂wj`
   - The gradient works out to `∂J/∂wj = (1/m) · Σ (ŷi - yi)·fji`, and `α` is the learning rate.

5. **Write down the difference between test set and validation set.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033 (ET: BUET)]*

   Answer:

   | Point | Validation set | Test set |
   |---|---|---|
   | Purpose | Tune hyperparameters and compare models | Give the final, unbiased performance score |
   | When used | Repeatedly, during training | Once only, after training is finished |
   | Effect on model | Indirect — its result changes the settings we choose | None — the model is never changed from it |
   | Seen by developer | Yes, many times | Should be kept untouched until the end |
   | Risk | Repeated use can overfit the model to this set | Stays a fair estimate as long as it is used once |
   | Typical share | About 15% of the data | About 15% of the data |

   - Both sets are kept out of training, but they answer different questions: validation asks "which settings are best?", test asks "how good is the finished model?".

## Supervised Learning (Decision Trees) (4)

1. **What is Machine Learning? Mention some real-life applications.** *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer: Machine learning is a field of Artificial Intelligence where a computer learns rules from data and improves with experience, instead of being given a fixed rule for every case.

   - A learning algorithm is fed training data, it builds a model, and the model predicts results for new data.
   - Three types: supervised (labelled data), unsupervised (unlabelled data) and reinforcement (learning from reward).

   Real-life applications
   - Banking — credit scoring, loan default prediction, card fraud detection, AML alerts.
   - Email and messaging — spam filtering, auto-reply suggestion.
   - E-commerce — product recommendation on Daraz or Amazon, demand forecasting.
   - Healthcare — disease prediction, cancer detection from X-ray and MRI images.
   - Speech and language — voice assistants, speech to text, Google Translate.
   - Security — face recognition, fingerprint matching, intrusion detection.
   - Transport — route and traffic prediction, self-driving cars.

2. **Decisiontree model in Machine Learning.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1448 (ET: N/A)]*

   Answer: A decision tree is a supervised learning model shaped like a tree, where each internal node tests one feature, each branch is the result of that test, and each leaf gives the final class or value.

   - Root node — the whole dataset, split first on the most useful feature.
   - Internal node — a test on a feature, e.g. "Income > 50,000?".
   - Branch — the outcome of the test (yes / no).
   - Leaf node — the predicted class or number.

   How it is built
   - At every node the algorithm picks the feature that separates the classes best.
   - Splitting measures: Information Gain and Entropy (ID3, C4.5), or Gini Index (CART).
   - `Entropy = -Σ pi·log2(pi)`, and `Information Gain = Entropy(parent) - weighted Entropy(children)`.
   - Splitting stops when the node is pure, when a depth limit is reached, or when too few samples remain.

   Advantages and drawbacks
   - Easy to read and explain, needs no feature scaling, handles both numeric and categorical data.
   - Overfits easily on deep trees; it is controlled by pruning, or by using Random Forest.

3. **What is machine learning? Differentiate among supervised learning vs unsupervised learning vs reinforcement learning.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 339 (ET: BIBM)]*

   Answer: Machine learning is the branch of AI in which a system learns patterns from data and improves its performance on a task without being explicitly programmed for every rule.

   | Point | Supervised | Unsupervised | Reinforcement |
   |---|---|---|---|
   | Data | Labelled input-output pairs | Unlabelled data only | No dataset; agent explores an environment |
   | Feedback | Correct answer given for each sample | No feedback at all | Reward or penalty after each action |
   | Goal | Predict the label of new data | Find hidden groups or structure | Choose actions that maximise total reward |
   | Main tasks | Classification, regression | Clustering, association, PCA | Policy learning, control |
   | Algorithms | Decision tree, SVM, KNN, logistic regression | K-Means, DBSCAN, Apriori | Q-learning, SARSA, Deep Q-Network |
   | Example | Predicting loan default from past records | Segmenting bank customers by behaviour | A robot learning to walk, game playing |

4. **(ক) Decision Tree কী? উদাহরণসহ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 605 (ET: N/A)]*

   Answer: A decision tree is a supervised learning model that makes a decision by asking a series of questions about the features, one at a time, until it reaches a leaf that holds the answer.

   - Root node — the starting question, chosen on the most informative feature.
   - Internal node — a test on one feature.
   - Branch — one possible answer to that test.
   - Leaf node — the final class or predicted value.

   Example — a bank deciding whether to approve a loan:

   ```mermaid
   flowchart TD
       A{Income > 50,000?} -->|No| B[Reject]
       A -->|Yes| C{Credit history good?}
       C -->|No| D[Reject]
       C -->|Yes| E{Existing loan?}
       E -->|Yes| F[Approve with limit]
       E -->|No| G[Approve]
   ```

   - The tree first checks income, then credit history, then any existing loan.
   - An applicant with income 80,000, good credit history and no existing loan follows the right-hand path and reaches "Approve".
   - The feature at each node is chosen by Information Gain or Gini Index, so the most useful question is always asked first.

## Generative AI & Explainable AI (XAI) (4)

1. **Imagine a government agency is developing an AI-based citizen service chatbot that can automatically generate responses, summarize documents, and provide policy information to citizens. Explain how Generative AI can be used to power such a system, and how Explainable AI (XAI) techniques can ensure that its responses are transparent, reliable, and accountable.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1428 (ET: E-Zone)]*

   Answer:

   (a) How Generative AI powers the chatbot
   - A Large Language Model (LLM) trained on text can write a fresh reply for each citizen question instead of picking from fixed templates.
   - Response generation — the model understands the question in Bangla or English and answers in natural language.
   - Document summarization — long circulars, gazettes and policy papers are compressed into short points.
   - RAG (Retrieval Augmented Generation) — before answering, the system searches the agency's own approved documents and passes them to the model, so the answer stays inside official policy and hallucination drops.
   - Fine-tuning on the agency's past queries teaches it the right tone and the local terms.
   - Multi-turn memory lets a citizen ask follow-up questions in the same conversation.

   (b) How XAI keeps it transparent and accountable
   - Source citation — every answer shows which circular or clause it came from, so the citizen can verify it.
   - Attention or attribution methods (LIME, SHAP) show which input words pushed the model towards its answer.
   - Confidence score — a low-confidence answer is passed to a human officer instead of being sent out.
   - Audit log — question, retrieved documents, generated answer and model version are all stored for later review.
   - Human-in-the-loop for sensitive matters such as tax, legal or financial advice.
   - Bias and fairness testing before release, plus a feedback button so wrong answers are reported and corrected.

2. **b) Briefly discuss "Generative Artificial Intelligence (GAI)" & "Large Language Models (LLMs)".** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1346 (ET: N/A)]*

   Answer:

   Generative AI (GAI)
   - AI that creates new content — text, image, audio, video or code — instead of only classifying or predicting.
   - It learns the pattern and distribution of the training data, then produces new samples that follow the same pattern.
   - Main model families: GAN (Generative Adversarial Network), VAE (Variational Autoencoder), Diffusion models, Transformers.
   - Examples: ChatGPT for text, DALL-E and Midjourney for images, GitHub Copilot for code.

   Large Language Models (LLMs)
   - A type of generative AI built for language, trained on a very large text corpus with billions of parameters.
   - Built on the Transformer architecture, which uses a self-attention mechanism to weigh the importance of every word against the others.
   - Trained by next-token prediction — guess the next word again and again over huge text.
   - Abilities: answering, summarizing, translating, writing code, reasoning over text.
   - Examples: GPT, Claude, Gemini, LLaMA.
   - Limitations: can hallucinate false facts, carries bias from training data, has a knowledge cut-off date, and training costs are very high.

3. **LLM stands for __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: Large Language Model.

4. **What is ChatGPT? Write down the Pros and cons of ChatGPT.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 521 (ET: MIST)]*

   Answer: ChatGPT is a conversational AI chatbot made by OpenAI. It is built on the GPT (Generative Pre-trained Transformer) large language model and answers questions in natural language.

   - It is pre-trained on a very large text corpus, then refined with RLHF (Reinforcement Learning from Human Feedback) so the replies stay helpful and safe.
   - It keeps the context of a conversation, so follow-up questions work.

   Pros
   - Instant answers, available all day, in many languages.
   - Helps with writing, summarizing, translation, coding and debugging.
   - Explains a hard topic in simple words, useful for learning.
   - Cuts cost and time in customer support and routine drafting work.

   Cons
   - Can hallucinate — states wrong facts with full confidence.
   - Knowledge has a cut-off date, so recent events may be missing.
   - Carries bias present in the training data.
   - Privacy risk if users paste confidential or personal data.
   - Encourages over-dependence and can be misused for plagiarism or exam cheating.
   - Does not truly understand meaning; it predicts likely text.

## Advanced Machine Learning & Deep Learning (RL, DL, Federated Learning) (3)

1. **Explain the concepts of Reinforcement Learning (RL), Deep Learning (DL), and Federated Learning (FL) in the context of Machine Learning. Briefly describe how each approach differs in its learning mechanism, data usage, and real-world applications.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1427 (ET: E-Zone)]*

   Answer:

   Reinforcement Learning (RL)
   - An agent learns by acting inside an environment and getting a reward or penalty for every action.
   - Learning mechanism: trial and error. The agent updates its policy to maximise total future reward.
   - Data usage: no fixed dataset; experience is generated by the agent itself while interacting.
   - Applications: game playing (AlphaGo), robot control, dynamic pricing, traffic signal control, algorithmic trading.

   Deep Learning (DL)
   - A subset of ML that uses neural networks with many hidden layers.
   - Learning mechanism: forward pass, then backpropagation with gradient descent to reduce the loss.
   - Data usage: needs a very large labelled dataset kept in one place, and GPU power.
   - Applications: image recognition, speech to text, machine translation, medical imaging, cheque and signature verification.

   Federated Learning (FL)
   - Many devices train a shared model without sending their raw data to a central server.
   - Learning mechanism: the server sends the model to each device, each device trains on its local data and returns only the weight updates, and the server averages them into a new global model.
   - Data usage: data never leaves the device, so privacy is preserved.
   - Applications: mobile keyboard next-word prediction, hospital data collaboration, bank fraud models across branches without sharing customer records.

   Key difference in one line
   - RL learns from reward, DL learns from large centralised labelled data, FL learns from distributed data while keeping it private.

2. **Explain reinforcement learning in the field of Machine Learning?** *[BTCL Assistant Manager (Technical) 2023 compact it 593 (ET: BUET)]*

   Answer: Reinforcement learning is a type of machine learning where an agent learns which action to take by interacting with an environment and receiving a reward for good actions and a penalty for bad ones.

   Main elements
   - Agent — the learner or decision maker.
   - Environment — the world the agent acts in.
   - State (S) — the current situation of the environment.
   - Action (A) — a move the agent can make.
   - Reward (R) — the feedback score returned after an action.
   - Policy (π) — the rule that maps a state to an action.

   ```mermaid
   flowchart LR
       AG[Agent] -->|Action At| EN[Environment]
       EN -->|State St+1| AG
       EN -->|Reward Rt+1| AG
   ```

   - The agent observes the state, takes an action, gets a reward and the next state, then updates its policy.
   - Goal: maximise the total reward over time, not just the next reward.
   - Exploration vs exploitation — it must try new actions sometimes, and use the known best action at other times.
   - Algorithms: Q-learning, SARSA, Deep Q-Network, Policy Gradient.
   - Examples: chess and Go programs, robot walking, self-driving cars, recommendation systems.

3. **Weak and strong learner ensemble learning in Machine learning.** *[GTCL Assistant Engineer (CSE) 2022 compact it 686 (ET: BUET)]*

   Answer: Ensemble learning combines several models so that the group gives a better result than any single model alone.

   Weak learner
   - A model that performs only slightly better than random guessing (a bit above 50% on a balanced binary problem).
   - Usually simple and fast, for example a decision stump — a tree with only one split.
   - Has high bias but low variance.

   Strong learner
   - A model that gives high accuracy and generalises well on new data.
   - Ensemble methods build a strong learner by combining many weak learners.

   Main ensemble techniques
   - Bagging — train many models in parallel on random samples of the data (bootstrap) and take a majority vote. Reduces variance. Example: Random Forest.
   - Boosting — train models one after another, where each new model focuses on the mistakes of the previous one. Reduces bias. Example: AdaBoost, Gradient Boosting, XGBoost.
   - Stacking — train several different models and use another model (meta learner) to combine their outputs.

   - Why it works: individual weak learners make different errors, and combining them cancels out much of that error.

## Search Algorithms (Informed vs Uninformed Search) (2)

1. **Write down the difference between informed and uninformed search algorithm.** *[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

   Answer: Uninformed search explores the state space blindly, while informed search uses extra knowledge (a heuristic) to move towards the goal faster.

   | Point | Uninformed (Blind) Search | Informed (Heuristic) Search |
   |---|---|---|
   | Domain knowledge | None beyond the problem definition | Uses a heuristic function `h(n)` |
   | Direction | Explores in a fixed pattern | Explores towards the goal |
   | Efficiency | Slow, expands many nodes | Faster, expands fewer nodes |
   | Time and space cost | High | Comparatively low |
   | Optimality | BFS and UCS give an optimal path | A* is optimal only if `h(n)` is admissible |
   | Examples | BFS, DFS, Uniform Cost Search, Depth Limited, Iterative Deepening | Greedy Best First Search, A*, AO* |

   - In A*, `f(n) = g(n) + h(n)`, where `g(n)` is the cost already spent and `h(n)` is the estimated cost still to go.
   - Example: finding a route from Dhaka to Chittagong. BFS checks every road blindly; A* uses straight-line distance as `h(n)` and heads south-east from the start.

2. **How $\alpha$-$\beta$ pruning is better than minimax search in game planning?** *[ICT Ministry Assistant Programmer 2017 compact it 1243 (ET: N/A)]*

   Answer: Alpha-beta pruning is minimax with a cut-off rule. It gives the same answer as minimax but skips branches that cannot change the result.

   How it works
   - Alpha (α) — the best value the MAX player is sure of so far.
   - Beta (β) — the best value the MIN player is sure of so far.
   - When `α ≥ β` at a node, the rest of that branch is pruned, because neither player would ever choose it.

   Why it is better
   - Minimax must visit every node of the game tree; alpha-beta skips large parts of it.
   - Time complexity falls from `O(b^d)` to `O(b^(d/2))` in the best case, where `b` is the branching factor and `d` the depth.
   - That effectively doubles the search depth for the same time, so the engine sees further ahead and plays stronger.
   - Uses less memory, since fewer nodes are stored.
   - The final move chosen is exactly the same as plain minimax — no accuracy is lost.

   - Its gain depends on move ordering. If the best move is examined first, pruning is maximum; with the worst ordering it degrades to plain minimax.

## Overfitting, Underfitting & Model Generalization (1)

1. **In machine learning. What will happen, when a machine is highly trained up a slight trained up?** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 395 (ET: BUET)]*

   Answer: Training a model too much causes overfitting, and training it too little causes underfitting. Both give poor results on new data.

   Highly trained (overfitting)
   - The model memorises the training data, including its noise and outliers.
   - Training accuracy is very high but test accuracy is low — a large gap between the two.
   - The model has high variance and low bias, and fails to generalise.
   - Remedies: stop training early, use more training data, simplify the model, apply regularization (L1/L2), dropout in neural networks, pruning in decision trees, and cross-validation.

   Slightly trained (underfitting)
   - The model has not learned the pattern at all.
   - Both training accuracy and test accuracy are low.
   - It has high bias and low variance — the model is too simple for the data.
   - Remedies: train longer, use a more complex model, add better features, reduce regularization.

   - The aim is the balance point in the middle, called a good fit, where training error and validation error are both low and close to each other. This trade-off is known as the bias-variance trade-off.

## Association Rule Learning (Market Basket Analysis) (1)

1. **Which Machine Learning Algorithm is suitable for the case of Market - Basket Analysis? Explain the steps involved.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1364 (ET: BUET)]*

   Answer: The Apriori algorithm is used for market basket analysis. It is an unsupervised association rule mining algorithm that finds which items are bought together. FP-Growth is a faster alternative for large datasets.

   Three measures used
   - Support — how often the itemset appears: `Support(A) = (transactions containing A) / (total transactions)`
   - Confidence — how often B is bought when A is bought: `Confidence(A→B) = Support(A ∪ B) / Support(A)`
   - Lift — how much stronger the rule is than chance: `Lift(A→B) = Confidence(A→B) / Support(B)`. Lift > 1 means a real positive relation.

   Steps of the Apriori algorithm
   - Step 1 — set a minimum support and a minimum confidence threshold.
   - Step 2 — scan the transaction database and count the support of every single item (1-itemsets).
   - Step 3 — drop the items whose support is below the minimum; the rest are frequent 1-itemsets.
   - Step 4 — join the frequent 1-itemsets to form candidate 2-itemsets, count their support and drop the weak ones.
   - Step 5 — repeat the join-and-prune step for 3-itemsets, 4-itemsets and so on, until no new frequent itemset is found.
   - Step 6 — from each frequent itemset, generate association rules and keep only the rules that meet the minimum confidence.
   - Step 7 — rank the surviving rules by lift and use the strong ones for business decisions.

   - Apriori property used in pruning: if an itemset is not frequent, none of its supersets can be frequent. This cuts the search space heavily.
   - Example: a rule `{Bread, Butter} → {Milk}` with support 8%, confidence 70% and lift 1.6 tells the shop to place milk near bread and butter, or to offer a combo discount.

## Clustering & Unsupervised Learning (K-Means, Hierarchical) (1)

1. **Consider the five points: P1 (0.07, 0.83), P2 (0.85, 0.14), P3 (0.66, 0.89), P4 (0.49, 0.64), and P5 (0.80, 0.46). Group first two points considering single-linkage hierarchical clustering technique.** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 473 (ET: N/A)]*

   Answer: In single-linkage agglomerative clustering, every point starts as its own cluster and the two closest points are merged first. So we compute the Euclidean distance between every pair and pick the smallest.

   Formula: `d(A, B) = √[(x2 - x1)² + (y2 - y1)²]`

   Step 1 - distance matrix

   | Pair | (dx)² + (dy)² | Distance |
   |---|---|---|
   | P1-P2 | (0.78)² + (0.69)² = 1.0845 | 1.0414 |
   | P1-P3 | (0.59)² + (0.06)² = 0.3517 | 0.5930 |
   | P1-P4 | (0.42)² + (0.19)² = 0.2125 | 0.4610 |
   | P1-P5 | (0.73)² + (0.37)² = 0.6698 | 0.8184 |
   | P2-P3 | (0.19)² + (0.75)² = 0.5986 | 0.7737 |
   | P2-P4 | (0.36)² + (0.50)² = 0.3796 | 0.6161 |
   | P2-P5 | (0.05)² + (0.32)² = 0.1049 | 0.3239 |
   | P3-P4 | (0.17)² + (0.25)² = 0.0914 | 0.3023 |
   | P3-P5 | (0.14)² + (0.43)² = 0.2045 | 0.4522 |
   | P4-P5 | (0.31)² + (0.18)² = 0.1285 | 0.3585 |

   Step 2 - sample calculation for the smallest pair
   - `d(P3, P4) = √[(0.66 - 0.49)² + (0.89 - 0.64)²]`
   - `= √[(0.17)² + (0.25)²] = √[0.0289 + 0.0625] = √0.0914`
   - `= 0.3023`

   Step 3 - pick the minimum
   - Smallest distance in the matrix is 0.3023, between P3 and P4.
   - Next smallest is P2-P5 at 0.3239, so it is not the first merge.

   Final answer
   - The first two points grouped are P3 (0.66, 0.89) and P4 (0.49, 0.64), merging at distance 0.3023.
   - The new cluster is {P3, P4}. In the next round, single-linkage uses the shortest distance from any member of this cluster to the remaining points.
