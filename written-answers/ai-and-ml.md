<!-- TOC START -->
**Table of Contents** — 11 subtopics · 41 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Artificial Intelligence & Expert Systems](#artificial-intelligence--expert-systems-8) | 8 |
| 2 | [Deep Learning & Neural Networks (ANN, CNN, RNN)](#deep-learning--neural-networks-ann-cnn-rnn-7) | 7 |
| 3 | [Machine Learning Paradigms (Supervised vs Unsupervised)](#machine-learning-paradigms-supervised-vs-unsupervised-6) | 6 |
| 4 | [Model Evaluation & Datasets](#model-evaluation--datasets-5) | 5 |
| 5 | [Supervised Learning (Decision Trees)](#supervised-learning-decision-trees-4) | 4 |
| 6 | [Generative AI & Explainable AI (XAI)](#generative-ai--explainable-ai-xai-4) | 4 |
| 7 | [Advanced Machine Learning & Deep Learning (RL, DL, Federated Learning)](#advanced-machine-learning--deep-learning-rl-dl-federated-learning-3) | 3 |
| 8 | [Search Algorithms (Informed vs Uninformed Search)](#search-algorithms-informed-vs-uninformed-search-1) | 1 |
| 9 | [Overfitting, Underfitting & Model Generalization](#overfitting-underfitting--model-generalization-1) | 1 |
| 10 | [Association Rule Learning (Market Basket Analysis)](#association-rule-learning-market-basket-analysis-1) | 1 |
| 11 | [Clustering & Unsupervised Learning (K-Means, Hierarchical)](#clustering--unsupervised-learning-k-means-hierarchical-1) | 1 |

<!-- TOC END -->

---

## Artificial Intelligence & Expert Systems (8)

1. **What is Artificial Intelligence?** *[Mongla Port Authority Assistant Programmer 2023 compact it 573 (ET: N/A)]*

   Answer: Artificial Intelligence (AI) is the branch of computer science that builds machines and software able to perform tasks that normally need human intelligence, such as learning, reasoning, problem solving, understanding language and taking decisions.

   Main characteristics:
   - Learning: the system improves its performance from data or experience instead of being programmed for every case.
   - Reasoning: it applies rules and logic on stored knowledge to reach a conclusion.
   - Perception: it takes input from the environment through images, speech or sensors.
   - Decision making: it selects the action that best achieves a defined goal.

   Types of AI:
   - Narrow AI (weak AI): built for one specific task, such as spam filtering, chatbots or face recognition. All AI in practical use today is of this type.
   - General AI (strong AI): would handle any intellectual task a human can do. It is still theoretical.
   - Super AI: a hypothetical stage where machine intelligence exceeds human intelligence.

   Major branches:
   - Machine Learning and Deep Learning
   - Natural Language Processing
   - Computer Vision
   - Robotics
   - Expert Systems

   Applications in the banking and government sector:
   - Fraud detection in card and mobile transactions
   - Credit scoring and risk assessment
   - Chatbots for customer service
   - Cheque and document reading through OCR
   - Cyber attack detection from network traffic patterns

2. **An artificial intelligence is an agent is an entity that continuously revious its enviornment.....** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 449 (ET: BUET)]*

3. **Write PEAS for (a) Auto taxi (b) Automatic clinical test.** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 457 (ET: BUET)]*

   Answer: PEAS stands for Performance measure, Environment, Actuators and Sensors. It is the standard way to describe the task environment of a rational agent before designing it.

   (a) Automated taxi
   - Performance measure: safe driving, reaching the destination, minimum trip time and fuel, obeying traffic law, passenger comfort, maximum profit.
   - Environment: roads, other vehicles, pedestrians, traffic signals, road signs, weather, passengers.
   - Actuators: steering, accelerator, brake, gear, indicator, horn, display and speaker for the passenger.
   - Sensors: camera, GPS, speedometer, odometer, radar or LIDAR, engine sensors, accelerometer, microphone.

   (b) Automatic clinical test system
   - Performance measure: correct diagnosis, accurate test result, minimum cost, minimum patient discomfort, fast reporting.
   - Environment: patient, hospital or laboratory, sample, medical staff, existing patient records.
   - Actuators: display of the result, printed report, questions asked to the patient, referral or treatment suggestion.
   - Sensors: keyboard entry of symptoms, laboratory test readings, imaging devices, patient history database.

4. **Intelligence can not be measured only by intelligence test because it is related to other subjects. (True or False)** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)]*

   Answer: True. An IQ test measures only some abilities such as logic and pattern recognition, while intelligence also covers creativity, emotional intelligence, practical skill and social judgement, so a single test cannot measure it completely.

5. **Machine learning is a subset of cloud computing that can be built AI-Based. (True or False).** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)], [BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

   Answer: False. Machine Learning is a subset of Artificial Intelligence, not of cloud computing. Cloud computing only supplies the storage and processing power on which ML models may be trained and deployed.

6. **What is the father of AI?** *[BARC Data Entry Officer 10.09.2022 compact it 703 (ET: N/A)]*

   Answer: John McCarthy is known as the father of Artificial Intelligence. He coined the term "Artificial Intelligence" and organised the Dartmouth Conference of 1956, where AI was established as a field of study.

7. **(i) ‘Knowledge’ কী? Human Knowledge কে Computer এ প্রকাশ করার একটি flow diagram দেখান।** *[BPSC Assistant Network Engineer 2020 compact it 952 (ET: N/A)]*

   Answer: Knowledge is processed and organised information together with the rules and experience needed to use it for reasoning and decision making. In AI, knowledge is the facts and relations that an intelligent system stores and applies to solve a problem.

   Knowledge Representation is the technique of expressing human knowledge in a form a computer can store and process, such as propositional and predicate logic, semantic networks, frames, production rules and ontologies.

   ```mermaid
   graph TD
       A[Human Knowledge: facts, rules, experience] --> B[Knowledge Acquisition]
       B --> C[Knowledge Representation<br/>logic, rules, frames, semantic net]
       C --> D[(Knowledge Base)]
       D --> E[Inference Engine]
       E --> F[Conclusion / Decision]
       F --> G[User Interface]
   ```

   - Knowledge is first collected from experts, documents or data during knowledge acquisition.
   - It is then encoded in a formal representation that a machine can read.
   - The encoded knowledge is stored in the knowledge base.
   - The inference engine applies reasoning rules on the knowledge base to derive new facts.
   - The result is returned to the user through the interface, which is the basic structure of an expert system.

8. **Who is Largely credited for breaking the German Enigma codes that provided a foundation for artificial intelligence?** *[Sadharan Bima Corporation Programmer/ AP/AME 2020 compact it 1002 (ET: DU)]*

   Answer: Alan Turing. He led the work at Bletchley Park that broke the German Enigma cipher during the Second World War, and later proposed the Turing Test, which became a foundation of artificial intelligence.

## Deep Learning & Neural Networks (ANN, CNN, RNN) (7)

1. **(c) What is activation function in Deep Neural Network? What is the usability of this?** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*

   Answer: An activation function is a mathematical function applied to the weighted sum of inputs at a neuron, which decides the output that the neuron passes to the next layer.

   Usability:
   - It introduces non-linearity. Without it, however many layers are stacked, the whole network collapses into a single linear equation and cannot learn complex patterns.
   - It keeps the output within a controlled range, which makes training stable.
   - It decides whether a neuron should be activated for a given input, so the network can select useful features.
   - It allows gradients to flow during backpropagation, which is how the weights get updated.

   Common activation functions:
   - Sigmoid: output between 0 and 1, used in binary classification output layers, but suffers from vanishing gradient.
   - Tanh: output between -1 and 1, zero centred, so it converges faster than sigmoid.
   - ReLU: outputs the input if positive, otherwise zero. It is the most used function in hidden layers because it is simple and avoids vanishing gradient.
   - Leaky ReLU: allows a small negative slope, which solves the dying ReLU problem.
   - Softmax: converts outputs into probabilities that sum to 1, used in the output layer of multi-class classification.

2. **What does the axon of neural network do?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

   Answer: The axon carries the output signal of a neuron and transmits it to the next neurons. In an artificial neural network it corresponds to the output connection that passes the activated value, multiplied by the connection weight, to the neurons of the next layer.

3. **Write difference between machine learning and deep learning.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 681 (ET: N/A)]*

   Answer:

   | Point | Machine Learning | Deep Learning |
   |---|---|---|
   | Relation | A subset of AI | A subset of Machine Learning |
   | Feature extraction | Features are selected manually by the engineer | Features are learned automatically by the network |
   | Data requirement | Works well on small or medium datasets | Needs very large datasets |
   | Hardware | Runs on an ordinary CPU | Usually needs GPU or TPU |
   | Training time | Short, minutes to hours | Long, hours to days |
   | Structure | Algorithms such as decision tree, SVM, KNN | Multi-layer neural networks (ANN, CNN, RNN) |
   | Interpretability | Easier to explain the decision | Behaves like a black box |
   | Example | Spam filter using Naive Bayes | Face recognition using CNN |

4. **What is Deep learning?** *[BARC Data Entry Officer 10.09.2022 compact it 703 (ET: N/A)]*

   Answer: Deep Learning is a subset of Machine Learning that uses artificial neural networks with many hidden layers to learn patterns directly from raw data.

   - The word "deep" refers to the large number of hidden layers between input and output.
   - Each layer extracts a higher level feature, for example edges, then shapes, then a full face.
   - It removes the need for manual feature engineering, but requires large data and heavy computation.
   - Common uses: image recognition, speech recognition, machine translation and self-driving cars.

5. **What is Artificial Neural Network (ANN)? Difference between deep learning technique and Traditional machine learning technique.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 856 (ET: N/A)]*

   Answer: An Artificial Neural Network is a computing model inspired by the human brain, built from connected units called neurons that are arranged in an input layer, one or more hidden layers and an output layer. Each connection carries a weight, each neuron applies an activation function, and the weights are adjusted by backpropagation so that the network learns the mapping from input to output.

   | Point | Traditional Machine Learning | Deep Learning |
   |---|---|---|
   | Feature extraction | Done manually by a domain expert | Learned automatically inside the network |
   | Data volume | Performs well on limited data | Needs a very large dataset |
   | Computation | Light, CPU is enough | Heavy, GPU is normally required |
   | Accuracy on complex data | Saturates early | Keeps improving as data grows |
   | Explainability | Relatively transparent | Mostly a black box |

6. **Write LSTM gates name in AI.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 858 (ET: N/A)]*

   Answer: An LSTM (Long Short Term Memory) cell has three gates:
   - Forget gate: decides which information from the previous cell state should be dropped.
   - Input gate: decides which new information should be stored in the cell state.
   - Output gate: decides which part of the cell state should be given as the output of the cell.

7. **Draw the single layer of ANN.** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 880 (ET: BUET)]*

   Answer: A single layer ANN (also called a perceptron) has only an input layer connected directly to an output layer, with no hidden layer in between.

   ```mermaid
   graph LR
       X1["Input x1"] -->|w1| S["Summation<br/>net = w1x1 + w2x2 + w3x3 + b"]
       X2["Input x2"] -->|w2| S
       X3["Input x3"] -->|w3| S
       B["Bias b"] --> S
       S --> F["Activation Function"]
       F --> Y["Output y"]
   ```

   - Each input is multiplied by its own weight and all products are added together with the bias.
   - The sum is passed through an activation function such as step or sigmoid.
   - The activation output is the final output of the network.
   - A single layer network can only separate linearly separable data, so it cannot solve the XOR problem.

## Machine Learning Paradigms (Supervised vs Unsupervised) (6)

1. **(a) Describe the following terms:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*
 * **(i) Supervised learning**
 * **(ii) Unsupervised learning**
 * **(iii) Reinforcement learning**

   Answer:

   (i) Supervised learning
   - The model is trained on labelled data, where every input already has the correct output.
   - The algorithm learns the mapping from input to output and then predicts the label of unseen data.
   - Two types: classification (output is a category) and regression (output is a number).
   - Examples: spam detection, credit approval, house price prediction.

   (ii) Unsupervised learning
   - The model is trained on unlabelled data, so no correct answer is supplied.
   - The algorithm finds hidden structure, groups or patterns by itself.
   - Two common types: clustering (K-Means, hierarchical) and association (market basket analysis).
   - Examples: customer segmentation, anomaly detection in transactions.

   (iii) Reinforcement learning
   - An agent learns by interacting with an environment, taking actions and receiving a reward or penalty.
   - No labelled dataset is given; the agent learns a policy that maximises long term reward through trial and error.
   - Key elements: agent, environment, state, action, reward.
   - Examples: game playing, robot navigation, automatic trading systems.

2. **a) Define the term "Data Mining". Explain supervised and unsupervised classification with suitable example.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*

   Answer: Data Mining is the process of discovering useful patterns, relationships and knowledge from a large volume of data by using statistics, machine learning and database techniques. It is a key step of the KDD (Knowledge Discovery in Databases) process.

   Supervised classification:
   - Training data is labelled, so each record already carries its class.
   - The model learns the boundary between classes and assigns a class to new records.
   - Example: a bank has past loan records marked as "defaulter" or "non-defaulter". A decision tree trained on these can classify a new applicant.

   Unsupervised classification (clustering):
   - Data has no label, so the algorithm groups records only by similarity.
   - The number and meaning of groups are discovered from the data itself.
   - Example: a bank runs K-Means on customer transaction data and gets natural groups such as high value customers, regular customers and dormant customers, without anyone labelling them first.

3. **Briefly explain supervised learning, unsupervised learning & reinforcement learning.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1341 (ET: N/A)]*

   Answer:
   - Supervised learning: learns from labelled data where the correct output is known, and predicts the output for new input. Used in classification and regression, for example spam filtering and price prediction.
   - Unsupervised learning: learns from unlabelled data and finds hidden groups or patterns by itself. Used in clustering and association, for example customer segmentation.
   - Reinforcement learning: an agent learns by acting in an environment and receiving reward or penalty, improving its policy over time. Used in robotics, game playing and automated control.

4. **(b) What is the difference between supervised and unsupervised learning? Explain with examples.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)], [SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)], [DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

   Answer:

   | Point | Supervised Learning | Unsupervised Learning |
   |---|---|---|
   | Training data | Labelled, correct output given | Unlabelled, no output given |
   | Goal | Predict the output for new input | Find hidden structure in the data |
   | Guidance | Learns under supervision of known answers | Learns without any supervision |
   | Main types | Classification, Regression | Clustering, Association |
   | Algorithms | Decision Tree, SVM, KNN, Linear Regression | K-Means, Hierarchical clustering, Apriori |
   | Accuracy check | Easy, compare prediction with the true label | Difficult, no ground truth to compare |
   | Example | Detecting whether an email is spam, using past emails already marked spam or not spam | Grouping bank customers into segments by spending behaviour, where no group was defined beforehand |

5. **Given some features of diabetic patient dataset with some labeled data. From this it can be predict whether this patient is diabetic or not. Is this supervised learning or unsupervised learning problem. Explain in one sentence.** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 433 (ET: BUET)]*

   Answer: It is a supervised learning problem, specifically binary classification, because the dataset already carries labels showing which patients are diabetic and which are not, and the model learns from those labels to classify a new patient.

6. **What do you mean by machine learning? Name three machine learning application in our daily life?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 680 (ET: N/A)]*

   Answer: Machine Learning is a branch of Artificial Intelligence in which a computer learns patterns from data and improves its performance on a task with experience, instead of being explicitly programmed with fixed rules for every case.

   Three daily life applications:
   - Email spam filtering, which classifies an incoming mail as spam or not from past mail patterns.
   - Product or video recommendation on e-commerce and streaming sites, based on the behaviour of similar users.
   - Fraud detection in card and mobile banking transactions, where an unusual transaction pattern raises an alert.

## Model Evaluation & Datasets (5)

1. **Write down the Role of Validation set in ML.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1448 (ET: N/A)]*

   Answer: The validation set is a part of the data kept aside from training, used to tune the model and check its performance before the final test.

   - It is used to select hyperparameters such as learning rate, tree depth or number of hidden layers.
   - It detects overfitting early, because training accuracy keeps rising while validation accuracy starts falling.
   - It is used for model selection when several candidate models are compared.
   - It is used for early stopping, where training is halted once validation error stops improving.
   - It keeps the test set untouched, so the final reported accuracy stays unbiased.

2. **(b) Given following values:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*
 * **True Positive \text{(TP)} = 560**
 * **True Negative \text{(TN)} = 330**
 * **False Positive \text{(FP)} = 60**
 * **False Negative \text{(FN)} = 50**
**Calculate the following: (i) Accuracy (ii) Precision (iii) Recall (iv) F1 Score**

   Answer:

   Given: TP = 560, TN = 330, FP = 60, FN = 50, total = 560 + 330 + 60 + 50 = 1000

   (i) Accuracy
   - Formula: Accuracy = (TP + TN) / (TP + TN + FP + FN)
   - = (560 + 330) / 1000
   - = 890 / 1000
   - = 0.89 or 89%

   (ii) Precision
   - Formula: Precision = TP / (TP + FP)
   - = 560 / (560 + 60)
   - = 560 / 620
   - = 0.9032 or 90.32%

   (iii) Recall
   - Formula: Recall = TP / (TP + FN)
   - = 560 / (560 + 50)
   - = 560 / 610
   - = 0.9180 or 91.80%

   (iv) F1 Score
   - Formula: F1 = 2 × (Precision × Recall) / (Precision + Recall)
   - = 2 × (0.9032 × 0.9180) / (0.9032 + 0.9180)
   - = 2 × 0.8291 / 1.8212
   - = 1.6582 / 1.8212
   - = 0.9105 or 91.05%

   Final answer: Accuracy = 89%, Precision = 90.32%, Recall = 91.80%, F1 Score = 91.05%

3. **b) How can we validate and check reliability of a machine learning model?** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*

   Answer: A model is validated by testing it on data it has never seen during training, and by measuring the right metrics for the problem.

   Validation methods:
   - Train-validation-test split, commonly 70:15:15, where the test set is used only once at the end.
   - K-fold cross validation, where the data is divided into k parts and the model is trained k times, each time using a different part as validation. The average score is reported.
   - Stratified k-fold, which keeps the class ratio the same in every fold, needed for imbalanced data.
   - Hold-out validation on a completely separate dataset collected later.

   Reliability checks:
   - Compare training and validation error. A large gap means overfitting, and both being high means underfitting.
   - Use the correct metric: accuracy for balanced data, but precision, recall, F1 and ROC-AUC for imbalanced data such as fraud detection.
   - Check the confusion matrix to see which class is being confused.
   - Test on fresh production data periodically, because data drift reduces accuracy over time.
   - Check stability by running with different random seeds and different data splits.

4. **You are a designing a machine learning model for a binary classification problem. The model has three features: f1, f2, f3. Derive the objective and loss function for this problem.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 746 (ET: N/A)]*

   Answer:

   Model: for binary classification with three features, logistic regression is used.
   - Linear part: z = w1·f1 + w2·f2 + w3·f3 + b
   - Prediction: ŷ = σ(z) = 1 / (1 + e^(−z)), which gives a probability between 0 and 1.
   - Decision: class 1 if ŷ ≥ 0.5, otherwise class 0.

   Loss function (binary cross entropy) for a single sample:
   - L = −[ y·log(ŷ) + (1 − y)·log(1 − ŷ) ]
   - If the true label y = 1, the loss becomes −log(ŷ), so the loss is small only when ŷ is close to 1.
   - If y = 0, the loss becomes −log(1 − ŷ), so the loss is small only when ŷ is close to 0.

   Objective function over the whole dataset of n samples:
   - J(w, b) = −(1/n) × Σ [ yi·log(ŷi) + (1 − yi)·log(1 − ŷi) ]
   - With L2 regularisation: J(w, b) = −(1/n) × Σ [ ... ] + (λ/2n) × Σ wj²

   Objective: minimise J(w, b) with respect to w1, w2, w3 and b, normally by gradient descent, where each weight is updated as wj = wj − α·(∂J/∂wj).

5. **Write down the difference between test set and validation set.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033 (ET: BUET)]*

   Answer:

   | Point | Validation Set | Test Set |
   |---|---|---|
   | Purpose | Tune hyperparameters and select the model | Give the final unbiased performance estimate |
   | Used during | The training and tuning phase | Only once, after everything is fixed |
   | Frequency of use | Many times | A single time |
   | Effect on the model | Indirectly influences the model, since choices are made from it | No influence at all |
   | Risk | Repeated use can leak information and cause overfitting to it | Stays clean, so the reported score is trustworthy |

## Supervised Learning (Decision Trees) (4)

1. **What is Machine Learning? Mention some real-life applications.** *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer: Machine Learning is a branch of Artificial Intelligence in which a system learns patterns from data and improves its performance on a task with experience, instead of following rules written by a programmer for every case.

   Basic working steps:
   - Collect and clean the data.
   - Select features and split the data into training, validation and test sets.
   - Train a model so that its error on the training data becomes minimum.
   - Validate, tune and finally test the model on unseen data.

   Real life applications:
   - Fraud detection in card and mobile banking transactions.
   - Credit scoring, where a bank predicts whether an applicant will repay a loan.
   - Email spam filtering.
   - Product and video recommendation on e-commerce and streaming platforms.
   - Face recognition and fingerprint matching in national ID and attendance systems.
   - Speech recognition in voice assistants and automatic call routing.
   - Medical diagnosis from X-ray and pathology images.
   - Demand and price forecasting in retail and agriculture.

2. **Decisiontree model in Machine Learning.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1448 (ET: N/A)]*

   Answer: A Decision Tree is a supervised learning model shaped like a tree, where each internal node tests one feature, each branch is the outcome of that test, and each leaf gives the final class or value.

   ```mermaid
   graph TD
       A{Income >= 50000?} -->|Yes| B{Credit history good?}
       A -->|No| C[Reject loan]
       B -->|Yes| D[Approve loan]
       B -->|No| E[Reject loan]
   ```

   - Splitting criteria: Information Gain or Gini Index for classification, and variance reduction for regression.
   - Working: the feature that separates the classes best is chosen at the root, and the process repeats on each branch until a stopping condition is reached.
   - Advantages: easy to understand and explain, needs little data preparation, handles both numeric and categorical data.
   - Disadvantages: a deep tree easily overfits, and a small change in data can change the whole tree. Pruning, or an ensemble such as Random Forest, is used to control this.

3. **What is machine learning? Differentiate among supervised learning vs unsupervised learning vs reinforcement learning.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 339 (ET: BIBM)]*

   Answer: Machine Learning is the field of Artificial Intelligence where a computer learns from data and improves with experience, without being explicitly programmed for each rule.

   | Point | Supervised | Unsupervised | Reinforcement |
   |---|---|---|---|
   | Input data | Labelled | Unlabelled | No dataset, an environment |
   | Learns from | Known correct output | Hidden structure in data | Reward and penalty |
   | Goal | Predict output for new input | Find groups or patterns | Maximise long term reward |
   | Feedback | Direct, from the label | None | Delayed, through reward |
   | Main types | Classification, Regression | Clustering, Association | Value based, Policy based |
   | Algorithms | Decision Tree, SVM, KNN | K-Means, Apriori | Q-Learning, SARSA |
   | Example | Loan default prediction | Customer segmentation | Robot learning to walk |

4. **(ক) Decision Tree কী? উদাহরণসহ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 605 (ET: N/A)]*

   Answer: A Decision Tree is a supervised machine learning model that makes a decision by asking a series of questions on the features. It has a tree structure where the root node is the first test, internal nodes are further tests, branches are the answers, and leaf nodes carry the final decision.

   Example: deciding whether to play cricket based on the weather.

   ```mermaid
   graph TD
       R{Outlook?} -->|Sunny| H{Humidity?}
       R -->|Overcast| P1[Play]
       R -->|Rainy| W{Windy?}
       H -->|High| N1[Do not play]
       H -->|Normal| P2[Play]
       W -->|True| N2[Do not play]
       W -->|False| P3[Play]
   ```

   - Root node: Outlook is chosen first because it separates the classes best, measured by Information Gain.
   - If Outlook is Overcast, the answer is always Play, so it becomes a leaf immediately.
   - If Outlook is Sunny, Humidity is tested next; if Rainy, Wind is tested.
   - Reading a path from root to leaf gives a readable rule, such as "if Outlook is Sunny and Humidity is High, then do not play".
   - This readability is why decision trees are widely used where the decision must be explained, for example in loan approval.

## Generative AI & Explainable AI (XAI) (4)

1. **Imagine a government agency is developing an AI-based citizen service chatbot that can automatically generate responses, summarize documents, and provide policy information to citizens. Explain how Generative AI can be used to power such a system, and how Explainable AI (XAI) techniques can ensure that its responses are transparent, reliable, and accountable.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1428 (ET: E-Zone)]*

   Answer:

   Role of Generative AI in the chatbot:
   - A Large Language Model understands the citizen's question written in natural Bangla or English and generates a human-like reply instead of returning a fixed template.
   - Retrieval Augmented Generation (RAG) is used, where the model first searches the agency's own circulars, acts and forms, then writes the answer from those retrieved documents. This keeps the reply tied to official policy and reduces hallucination.
   - Document summarisation lets a citizen get a short summary of a long gazette or policy paper.
   - Multilingual support allows the same system to serve Bangla and English users.
   - Form filling assistance guides the citizen step by step to complete an application.

   Role of Explainable AI:
   - Source citation: every reply shows which circular or section it came from, so the citizen can verify it.
   - Confidence score: when confidence is low the system says so and transfers the case to a human officer.
   - Feature attribution methods such as LIME and SHAP show which input words most influenced the output, which helps developers audit the behaviour.
   - Attention or highlight display shows which part of the retrieved document was used.
   - Decision logging keeps a record of every query and reply, so an audit can be done later and responsibility can be fixed.
   - Human in the loop review is kept for sensitive matters such as legal or financial advice.

   Together, Generative AI gives the service quality and Explainable AI gives the accountability that a government service must have.

2. **b) Briefly discuss "Generative Artificial Intelligence (GAI)" & "Large Language Models (LLMs)".** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1346 (ET: N/A)]*

   Answer:

   Generative AI:
   - It is the class of AI that creates new content such as text, image, audio, video or code, instead of only classifying or predicting.
   - It learns the underlying distribution of the training data and then samples new data from it.
   - Main techniques: GAN (Generative Adversarial Network), VAE (Variational Autoencoder), Diffusion models and Transformer based language models.
   - Examples: ChatGPT for text, DALL-E and Midjourney for images, GitHub Copilot for code.

   Large Language Models:
   - An LLM is a very large neural network, built on the Transformer architecture, trained on a huge amount of text to predict the next token.
   - It has billions of parameters and learns grammar, facts and reasoning patterns from the training text.
   - Capabilities: question answering, summarisation, translation, code generation and conversation.
   - Limitations: it can hallucinate confident but wrong facts, it has a knowledge cutoff date, it may carry bias from training data, and training and running it is expensive.

3. **LLM stands for __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: Large Language Model.

4. **What is ChatGPT? Write down the Pros and cons of ChatGPT.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 521 (ET: MIST)]*

   Answer: ChatGPT is a conversational AI system developed by OpenAI, built on a Large Language Model of the GPT family. It takes a question in natural language and generates a human-like reply, and it can hold a multi-turn conversation by remembering earlier messages in the same session.

   Pros:
   - Answers questions in natural language and explains difficult topics simply.
   - Available all day, gives an instant reply, and can serve many users at once.
   - Helps in drafting letters, reports, summaries and code, which saves working time.
   - Supports many languages including Bangla.
   - Useful for learning, as it can give examples and step by step explanations.

   Cons:
   - It can hallucinate, that is give a wrong answer with full confidence.
   - Its knowledge has a cutoff date, so very recent events may be missing.
   - It may reflect bias present in the training data.
   - Data privacy risk if confidential official information is typed into it.
   - Over dependence can weaken the user's own analytical and writing skill.
   - It does not truly understand meaning; it predicts the most likely next word.

## Advanced Machine Learning & Deep Learning (RL, DL, Federated Learning) (3)

1. **Explain the concepts of Reinforcement Learning (RL), Deep Learning (DL), and Federated Learning (FL) in the context of Machine Learning. Briefly describe how each approach differs in its learning mechanism, data usage, and real-world applications.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1427 (ET: E-Zone)]*

   Answer:

   Reinforcement Learning:
   - Learning mechanism: an agent takes an action in an environment, receives a reward or penalty, and updates its policy to maximise the total future reward.
   - Data usage: no labelled dataset. The agent generates its own experience by trial and error.
   - Applications: robot navigation, game playing, traffic signal control, automated trading, dynamic pricing.

   Deep Learning:
   - Learning mechanism: a multi-layer neural network learns features automatically, and weights are adjusted by backpropagation to reduce the loss.
   - Data usage: needs a very large labelled dataset and heavy computation, normally GPU.
   - Applications: image and face recognition, speech recognition, machine translation, medical image diagnosis, cheque and document reading.

   Federated Learning:
   - Learning mechanism: the model is sent to each device or branch, trained locally on local data, and only the model updates are sent back to a central server, which aggregates them into a global model.
   - Data usage: raw data never leaves the device, so privacy is preserved. Data is naturally distributed and often not identically distributed.
   - Applications: mobile keyboard prediction, healthcare where hospital data cannot be shared, and banking where each branch or bank keeps customer data local but a shared fraud model is still trained.

   Key difference in one line: RL learns from reward, DL learns from large labelled data in deep networks, and FL learns across many devices without moving the data.

2. **Explain reinforcement learning in the field of Machine Learning?** *[BTCL Assistant Manager (Technical) 2023 compact it 593 (ET: BUET)]*

   Answer: Reinforcement Learning is a machine learning approach where an agent learns which action to take by interacting with an environment and receiving a reward or a penalty for each action, so that the total reward over time becomes maximum.

   Main elements:
   - Agent: the learner or decision maker.
   - Environment: everything the agent interacts with.
   - State: the current situation of the environment.
   - Action: what the agent can do in that state.
   - Reward: the numeric feedback after an action.
   - Policy: the strategy that maps a state to an action.

   ```mermaid
   graph LR
       AG[Agent] -->|Action| ENV[Environment]
       ENV -->|State| AG
       ENV -->|Reward| AG
   ```

   - The agent must balance exploration, that is trying new actions, against exploitation, that is using the best known action.
   - Common algorithms are Q-Learning, SARSA and Deep Q-Network.
   - Example: a robot learning to walk gets a positive reward for moving forward and a negative reward for falling, and after many attempts it learns a stable walking policy.

3. **Weak and strong learner ensemble learning in Machine learning.** *[GTCL Assistant Engineer (CSE) 2022 compact it 686 (ET: BUET)]*

   Answer: Ensemble learning combines several models so that the group performs better than any single model.

   - Weak learner: a model whose accuracy is only slightly better than random guessing, for example a decision stump, which is a tree of depth one.
   - Strong learner: a model with high accuracy, which ensemble methods build by combining many weak learners.

   Main ensemble techniques:
   - Bagging: many models are trained in parallel on different bootstrap samples and their outputs are averaged or voted. It mainly reduces variance. Example: Random Forest.
   - Boosting: models are trained one after another, and each new model gives more weight to the samples the previous model got wrong. It mainly reduces bias. Examples: AdaBoost, Gradient Boosting, XGBoost.
   - Stacking: several different models are trained and a meta model learns how to combine their predictions.

   Why it works: individual weak learners make different errors, and combining them cancels out much of the random error, so accuracy and stability both improve.

## Search Algorithms (Informed vs Uninformed Search) (1)

1. **Write down the difference between informed and uninformed search algorithm.** *[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

   Answer:

   | Point | Uninformed (Blind) Search | Informed (Heuristic) Search |
   |---|---|---|
   | Domain knowledge | None beyond the problem definition | Uses a heuristic that estimates cost to the goal |
   | Guidance | Explores blindly in a fixed order | Guided towards the most promising node |
   | Efficiency | Explores many unnecessary nodes | Explores far fewer nodes |
   | Time and memory | Generally high | Generally lower |
   | Completeness | BFS and UCS are complete | Complete if the heuristic is admissible |
   | Optimality | BFS optimal for equal cost, UCS optimal | A* is optimal when the heuristic is admissible and consistent |
   | Examples | BFS, DFS, Depth Limited Search, Uniform Cost Search, Iterative Deepening | Greedy Best First Search, A* Search, AO* Search |

   - A heuristic h(n) is an estimate of the cost from node n to the goal, for example straight line distance in a map problem.
   - A* uses f(n) = g(n) + h(n), where g(n) is the actual cost already spent, which is why it is both efficient and optimal.

## Overfitting, Underfitting & Model Generalization (1)

1. **In machine learning. What will happen, when a machine is highly trained up a slight trained up?** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 395 (ET: BUET)]*

   Answer: If a model is trained too much it overfits, and if it is trained too little it underfits. Both reduce performance on new data.

   Overfitting (highly trained):
   - The model memorises the training data including its noise, instead of learning the general pattern.
   - Training accuracy becomes very high but validation and test accuracy fall.
   - It shows high variance and low bias.
   - Remedies: stop training early, use more training data, apply regularisation (L1 or L2), use dropout in neural networks, prune the decision tree, and use cross validation.

   Underfitting (slightly trained):
   - The model is too simple or trained for too few iterations, so it cannot capture the pattern even in the training data.
   - Both training and test accuracy stay low.
   - It shows high bias and low variance.
   - Remedies: train longer, use a more complex model, add better features, and reduce regularisation.

   The aim is the balanced point between the two, called a good fit, where training and validation error are both low and close to each other. This balance is known as the bias-variance tradeoff.

## Association Rule Learning (Market Basket Analysis) (1)

1. **Which Machine Learning Algorithm is suitable for the case of Market - Basket Analysis? Explain the steps involved.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1364 (ET: BUET)]*

   Answer: The Apriori algorithm, an association rule learning method under unsupervised learning, is suitable for Market Basket Analysis. FP-Growth is a faster alternative for very large datasets.

   Three measures used:
   - Support: how often an itemset appears. Support(A) = transactions containing A / total transactions.
   - Confidence: how often B is bought when A is bought. Confidence(A→B) = Support(A∪B) / Support(A).
   - Lift: how much more likely B is with A than by chance. Lift(A→B) = Confidence(A→B) / Support(B). A lift above 1 means a real positive association.

   Steps of the Apriori algorithm:
   - Set a minimum support and a minimum confidence threshold.
   - Scan the transaction database and count the support of every single item, giving the 1-itemsets.
   - Remove the items whose support is below the minimum, keeping only the frequent 1-itemsets.
   - Join the frequent 1-itemsets to form candidate 2-itemsets, count their support and prune the infrequent ones.
   - Repeat this join and prune step for 3-itemsets, 4-itemsets and so on, until no new frequent itemset is found. This uses the Apriori property, that any subset of a frequent itemset must also be frequent.
   - From each frequent itemset, generate all possible association rules.
   - Keep only the rules whose confidence is above the minimum threshold, and rank them by lift.

   Example: if the rule {bread, butter} → {milk} has support 20%, confidence 70% and lift 1.5, the shop can place milk near bread and butter, or offer a combined discount.

## Clustering & Unsupervised Learning (K-Means, Hierarchical) (1)

1. **Consider the five points: P1 (0.07, 0.83), P2 (0.85, 0.14), P3 (0.66, 0.89), P4 (0.49, 0.64), and P5 (0.80, 0.46). Group first two points considering single-linkage hierarchical clustering technique.** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 473 (ET: N/A)]*

   Answer:

   Formula: Euclidean distance between two points is
   d(A, B) = √[(x2 − x1)² + (y2 − y1)²]

   In agglomerative single-linkage clustering, every point starts as its own cluster and the two clusters having the smallest distance are merged first.

   Step 1: calculate the distance between every pair.
   - d(P1, P2) = √[(0.85 − 0.07)² + (0.14 − 0.83)²] = √[0.6084 + 0.4761] = √1.0845 = 1.0414
   - d(P1, P3) = √[(0.59)² + (0.06)²] = √[0.3481 + 0.0036] = √0.3517 = 0.5930
   - d(P1, P4) = √[(0.42)² + (−0.19)²] = √[0.1764 + 0.0361] = √0.2125 = 0.4610
   - d(P1, P5) = √[(0.73)² + (−0.37)²] = √[0.5329 + 0.1369] = √0.6698 = 0.8184
   - d(P2, P3) = √[(−0.19)² + (0.75)²] = √[0.0361 + 0.5625] = √0.5986 = 0.7737
   - d(P2, P4) = √[(−0.36)² + (0.50)²] = √[0.1296 + 0.2500] = √0.3796 = 0.6161
   - d(P2, P5) = √[(−0.05)² + (0.32)²] = √[0.0025 + 0.1024] = √0.1049 = 0.3239
   - d(P3, P4) = √[(−0.17)² + (−0.25)²] = √[0.0289 + 0.0625] = √0.0914 = 0.3023
   - d(P3, P5) = √[(0.14)² + (−0.43)²] = √[0.0196 + 0.1849] = √0.2045 = 0.4522
   - d(P4, P5) = √[(0.31)² + (−0.18)²] = √[0.0961 + 0.0324] = √0.1285 = 0.3585

   Step 2: find the minimum distance.
   - The smallest value among all pairs is 0.3023, which is d(P3, P4).

   Step 3: merge that pair.
   - P3 and P4 are joined into one cluster {P3, P4} at height 0.3023 in the dendrogram.
   - After this merge, the distance from {P3, P4} to any other point is taken as the minimum of the two individual distances, because the linkage is single-linkage.

   Final answer: the first two points grouped are P3 (0.66, 0.89) and P4 (0.49, 0.64), merging at a distance of 0.3023.

