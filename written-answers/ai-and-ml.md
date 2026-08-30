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

   Answer: Artificial Intelligence (AI) is a technology that lets machines and computers do work which normally needs human thinking.

   An AI system can do three things:
   - It copies human intelligence by learning and reasoning.
   - It reads large amounts of data and finds patterns in it.
   - It keeps getting better through experience and feedback.

   Core concepts of AI:
   - Machine Learning: the system learns from data. We do not write a rule for every case.
   - Generative AI: it creates new content, such as text, image, audio or video.
   - Natural Language Processing (NLP): it lets a computer understand human language.
   - Expert Systems: it copies the decision making of a human expert, using stored rules.

   How AI works, step by step:
   - Collect data from many sources.
   - Clean and prepare the data.
   - Train a model on that data.
   - Test the model and check the result.
   - Use the model, and keep improving it with feedback.

   Types of AI based on capability:
   - Narrow AI: made for one fixed job, like speech recognition or a spam filter. All AI we use today is of this type.
   - General AI: can do any thinking job a human can do, in any field. It is only theory today.
   - Superintelligent AI: smarter than humans. It does not exist; it is a future idea.

   Types of AI based on functionality:
   - Reactive Machines: they answer only the current input. They have no memory.
   - Limited Memory: they use past data to make better decisions now.
   - Theory of Mind: they would understand human feelings and beliefs. Still theory.
   - Self-Aware AI: they would have their own consciousness. Still theory.

   Applications:
   - Healthcare: finding disease early, and suggesting treatment.
   - Retail: personal shopping suggestions and stock management.
   - Customer service: chatbots that answer all day and night.
   - Manufacturing: predicting machine failure before it happens.
   - Finance: fraud detection, risk analysis and investment support.

   Advantages:
   - It does repeated work automatically and makes fewer mistakes.
   - It gives better decisions by studying huge amounts of data.
   - It gives each user a personal experience.
   - It works 24 hours a day without rest.
   - It spots patterns humans miss, which helps in fraud detection and diagnosis.

   Challenges:
   - It needs a lot of data, which raises privacy and security worries.
   - If the training data is biased, the output becomes unfair.
   - Its decisions are often not transparent, so we cannot explain them.
   - Automation can take away jobs.
   - It raises ethical questions in sensitive fields.

2. **An artificial intelligence is an agent is an entity that continuously revious its enviornment.....** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 449 (ET: BUET)]*

3. **Write PEAS for (a) Auto taxi (b) Automatic clinical test.** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 457 (ET: BUET)]*

   Answer: PEAS stands for Performance measure, Environment, Actuators and Sensors. We write the PEAS of an agent before we design it, because it describes the agent's task environment.

   The four parts:
   - Performance measure: the things we use to judge how well the agent is doing its job.
   - Environment: the surroundings the agent works in. The agent takes input from it and acts on it.
   - Actuators: the parts the agent uses to act on the environment. For a human agent, hands and legs are the actuators.
   - Sensors: the parts the agent uses to take input. For a human agent, eyes, ears and nose are the sensors.

   (a) Automated taxi

   | Component | Details |
   |---|---|
   | Performance measure | Safe driving, reaching the destination, less time and fuel, following traffic rules, passenger comfort, more profit |
   | Environment | Roads, other vehicles, pedestrians, traffic signals, road signs, weather, passengers |
   | Actuators | Steering, accelerator, brake, gear, indicator, horn, display and speaker for the passenger |
   | Sensors | Camera, GPS, speedometer, odometer, radar or LIDAR, engine sensors, accelerometer, microphone |

   (b) Automatic clinical test system

   | Component | Details |
   |---|---|
   | Performance measure | Correct diagnosis, accurate test result, low cost, less pain to the patient, fast report |
   | Environment | Patient, hospital or laboratory, sample, medical staff, old patient records |
   | Actuators | Result shown on screen, printed report, questions asked to the patient, treatment advice |
   | Sensors | Keyboard input of symptoms, laboratory machine readings, imaging machines, patient history database |

4. **Intelligence can not be measured only by intelligence test because it is related to other subjects. (True or False)** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)]*

   Answer: True.

   - An IQ test checks only a few abilities, mainly logic, reasoning and pattern finding.
   - Intelligence is much wider than that. It also includes creativity, emotional intelligence, practical skill and social judgement.
   - These other parts are linked with psychology, biology and social science, not with a single test.
   - So one intelligence test cannot measure the whole of a person's intelligence.

5. **Machine learning is a subset of cloud computing that can be built AI-Based. (True or False).** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)], [BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

   Answer: False.

   - Machine Learning is a subset of Artificial Intelligence, not of cloud computing.
   - The correct order is: Artificial Intelligence > Machine Learning > Deep Learning.
   - Cloud computing is a separate field. It only supplies the storage and the processing power.
   - We can train and run an ML model on the cloud, but that does not make ML a part of cloud computing.

6. **What is the father of AI?** *[BARC Data Entry Officer 10.09.2022 compact it 703 (ET: N/A)]*

   Answer: John McCarthy is known as the father of Artificial Intelligence.

   - He first used the term "Artificial Intelligence" in 1955.
   - He organised the Dartmouth Conference in 1956, where AI was born as a subject of study.
   - He also created the LISP programming language, which was used for AI work for many years.

7. **(i) ‘Knowledge’ কী? Human Knowledge কে Computer এ প্রকাশ করার একটি flow diagram দেখান।** *[BPSC Assistant Network Engineer 2020 compact it 952 (ET: N/A)]*

   Answer: Knowledge means real world information stored and organised in such a way that a machine can reason with it, learn from it and take decisions like a human.

   Types of knowledge:
   - Declarative knowledge: facts, that is what something is. Example: Dhaka is the capital of Bangladesh.
   - Procedural knowledge: how to do a task. Example: the steps of a sorting algorithm.
   - Meta knowledge: knowledge about knowledge itself, that is knowing what we know and how to use it.
   - Heuristic knowledge: rules of thumb from experience, used by experts.
   - Structural knowledge: how concepts relate to each other, such as a class hierarchy.

   Knowledge Representation (KR) is the way we write human knowledge in a form a computer can store and process.

   Techniques of knowledge representation:
   - Logical representation: uses formal rules and logic, such as propositional logic and predicate logic. It reasons well, but it is hard to read and can be slow.
   - Semantic network: shows knowledge as a graph. The nodes are concepts or objects, and the arcs are the relations between them, such as IS-A and kind-of. It is easy to picture, but searching a big network is slow.
   - Frame representation: groups related information into slots and values, like a record. It is flexible, but its inference is not efficient.
   - Production rules: knowledge written as IF-THEN rules. It has a rule set, a working memory and a recognise-act cycle. It is simple and modular, but slow when there are too many rules.

   Flow diagram — putting human knowledge into a computer:

   ```mermaid
   graph TD
       A[Human Knowledge: facts, rules, experience] --> B[Knowledge Acquisition]
       B --> C[Knowledge Representation<br/>logic, semantic net, frame, production rules]
       C --> D[(Knowledge Base)]
       D --> E[Inference Engine]
       E --> F[Conclusion / Decision]
       F --> G[User Interface]
       G --> H[User]
   ```

   Steps in the diagram:
   - Knowledge acquisition: we collect knowledge from experts, documents and data.
   - Knowledge representation: we write it in a formal form the machine can read.
   - Knowledge base: the written knowledge is stored here.
   - Inference engine: it applies the rules on the knowledge base and finds new facts.
   - User interface: the result is shown to the user.

   This is exactly how an expert system is built.

8. **Who is Largely credited for breaking the German Enigma codes that provided a foundation for artificial intelligence?** *[Sadharan Bima Corporation Programmer/ AP/AME 2020 compact it 1002 (ET: DU)]*

   Answer: Alan Turing.

   - He led the codebreaking work at Bletchley Park during the Second World War and broke the German Enigma cipher.
   - He built the machine called Bombe, which is seen as an early step towards the modern computer.
   - In 1950 he gave the Turing Test, which asks whether a machine can talk so well that a human cannot tell it apart from another human. This test became a base idea of artificial intelligence.

## Deep Learning & Neural Networks (ANN, CNN, RNN) (7)

1. **(c) What is activation function in Deep Neural Network? What is the usability of this?** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*

   Answer: An activation function is a small maths function used inside a neuron. The neuron first adds up all its weighted inputs. Then the activation function takes that sum and decides what value the neuron will send to the next layer.

   Why we need it (usability):
   - It adds non-linearity. Without it, even 100 layers act like one straight line equation. Then the network cannot learn hard patterns.
   - It keeps the output inside a fixed range. This makes training stable.
   - It decides if a neuron should fire or stay quiet for a given input. So the network can pick useful features.
   - It lets the gradient flow back during backpropagation. This is how the weights get updated.

   Common activation functions:

   | Function | Output range | Where we use it |
   |---|---|---|
   | Sigmoid | 0 to 1 | Output layer for yes/no problems. Problem: vanishing gradient |
   | Tanh | -1 to 1 | Hidden layers. Trains faster than sigmoid because it is zero centred |
   | ReLU | 0 to input value | Most used in hidden layers. Simple and no vanishing gradient |
   | Leaky ReLU | small negative to input | Fixes the dying ReLU problem by allowing a small negative value |
   | Softmax | 0 to 1, all add to 1 | Output layer when there are many classes |

   ReLU in one line: if the input is positive, pass it as it is. If it is negative, give 0.

2. **What does the axon of neural network do?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

   Answer: The axon carries the output of a neuron and sends it to the next neurons.

   In an artificial neural network, the axon is the output connection. It takes the value produced by the activation function, multiplies it by the connection weight, and passes it to the neurons of the next layer.

3. **Write difference between machine learning and deep learning.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 681 (ET: N/A)]*

   Answer:

   | Point | Machine Learning | Deep Learning |
   |---|---|---|
   | Relation | A part of AI | A part of Machine Learning |
   | Feature extraction | The engineer picks the features by hand | The network finds the features on its own |
   | Data needed | Works fine with small or medium data | Needs very large data |
   | Hardware | Normal CPU is enough | Usually needs GPU or TPU |
   | Training time | Short, minutes to hours | Long, hours to days |
   | Structure | Algorithms like decision tree, SVM, KNN | Neural networks with many layers (ANN, CNN, RNN) |
   | Explaining the result | Easy to explain why it decided so | Works like a black box, hard to explain |
   | Example | Spam filter using Naive Bayes | Face recognition using CNN |

   Simple way to remember: in Machine Learning we tell the model what to look at. In Deep Learning the model finds out what to look at.

4. **What is Deep learning?** *[BARC Data Entry Officer 10.09.2022 compact it 703 (ET: N/A)]*

   Answer: Deep Learning is a part of Machine Learning. It uses artificial neural networks that have many hidden layers, and it learns patterns straight from raw data.

   Key points:
   - The word "deep" means there are many hidden layers between the input and the output.
   - Each layer learns a bigger idea than the layer before it. Example for a face: first layer finds edges, next finds shapes like eye and nose, last finds the full face.
   - We do not need to pick features by hand. The network does it.
   - But it needs a lot of data and a lot of computing power.

   Where we use it: image recognition, speech recognition, language translation and self-driving cars.

5. **What is Artificial Neural Network (ANN)? Difference between deep learning technique and Traditional machine learning technique.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 856 (ET: N/A)]*

   Answer: An Artificial Neural Network (ANN) is a computing model that copies the idea of the human brain. It is made of small units called neurons. These neurons sit in three kinds of layers: one input layer, one or more hidden layers, and one output layer.

   How it works:
   - Every connection between two neurons has a number called a weight.
   - A neuron adds up its weighted inputs and passes the sum through an activation function.
   - The output goes to the next layer.
   - Backpropagation compares the output with the correct answer and slowly changes the weights. This is how the network learns.

   Difference between Deep Learning and Traditional Machine Learning:

   | Point | Traditional Machine Learning | Deep Learning |
   |---|---|---|
   | Feature extraction | A person picks the features by hand | The network learns the features itself |
   | Data needed | Works well with small data | Needs very large data |
   | Computing power | Light, CPU is enough | Heavy, GPU is usually needed |
   | Accuracy on hard data | Stops improving after some point | Keeps improving as data grows |
   | Explaining the result | Fairly easy to explain | Mostly a black box |

6. **Write LSTM gates name in AI.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 858 (ET: N/A)]*

   Answer: An LSTM (Long Short Term Memory) cell has three gates:
   - Forget gate: decides which old information should be thrown away from the cell state.
   - Input gate: decides which new information should be saved into the cell state.
   - Output gate: decides which part of the cell state should go out as the cell output.

   Simple idea: the forget gate erases, the input gate writes, and the output gate reads.

7. **Draw the single layer of ANN.** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 880 (ET: BUET)]*

   Answer: A single layer ANN is also called a perceptron. It has only an input layer joined straight to an output layer. There is no hidden layer.

   ```mermaid
   graph LR
       X1["Input x1"] -->|w1| S["Summation<br/>net = w1x1 + w2x2 + w3x3 + b"]
       X2["Input x2"] -->|w2| S
       X3["Input x3"] -->|w3| S
       B["Bias b"] --> S
       S --> F["Activation Function"]
       F --> Y["Output y"]
   ```

   How it works:
   - Each input is multiplied by its own weight.
   - All the products are added together, and the bias is also added.
   - This sum goes into an activation function, such as step or sigmoid.
   - The result of the activation function is the final output.

   Limitation: a single layer network can only draw a straight line between two classes. So it cannot solve the XOR problem. For that we need at least one hidden layer.

## Machine Learning Paradigms (Supervised vs Unsupervised) (6)

1. **(a) Describe the following terms:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*
 * **(i) Supervised learning**
 * **(ii) Unsupervised learning**
 * **(iii) Reinforcement learning**

   Answer:

   (i) Supervised learning
   - We train the model on labelled data. Every input already has its correct output written with it.
   - The model learns the link between input and output. Then it predicts the output for new, unseen data.
   - Two types: classification (output is a category, like spam or not spam) and regression (output is a number, like price).
   - Example: we give the model 10,000 old emails already marked spam or not spam. Now it can mark a new email.

   (ii) Unsupervised learning
   - We train the model on unlabelled data. No correct answer is given.
   - The model finds hidden groups or patterns on its own.
   - Two types: clustering (K-Means, Hierarchical) and association (market basket analysis).
   - Example: we give the model customer spending data with no groups marked. It makes groups like high spenders, normal spenders and inactive customers.

   (iii) Reinforcement learning
   - An agent works inside an environment. It takes an action and gets a reward or a penalty.
   - There is no labelled dataset. The agent learns by trial and error and tries to collect the highest total reward.
   - Main parts: agent, environment, state, action, reward.
   - Example: a robot learns to walk. Each step forward gives a reward, each fall gives a penalty.

   Comparison of the three:

   | Criteria | Supervised Learning | Unsupervised Learning | Reinforcement Learning |
   |---|---|---|---|
   | Definition | Learns from labelled data | Finds patterns in unlabelled data | Learns by acting inside an environment |
   | Type of data | Labelled data | Unlabelled data | No dataset; it gets reward or penalty |
   | Type of problem | Classification, Regression | Clustering, Association | Step by step decision making |
   | Supervision | Needs a teacher (the correct label) | No supervision | No supervision, only reward |
   | Algorithms | Decision Tree, SVM, KNN, Linear Regression | K-Means, Hierarchical, Apriori | Q-Learning, Deep Q-Network, SARSA |
   | Goal | Predict the correct output | Find hidden groups or rules | Get the highest total reward |
   | Applications | Medical diagnosis, fraud detection, spam filtering, price forecasting | Customer segmentation, anomaly detection | Self-driving cars, robotics, game AI |

2. **a) Define the term "Data Mining". Explain supervised and unsupervised classification with suitable example.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*

   Answer: Data Mining is the process of finding useful patterns, relations and knowledge from a large amount of data. It uses statistics, machine learning and database techniques together. It is the main step of the KDD process (Knowledge Discovery in Databases).

   In simple words: we have a mountain of data. Data mining digs into it and pulls out the useful facts.

   Supervised classification
   - The training data is labelled. Every record already has its class written on it.
   - The model learns the border between the classes. Then it puts a new record into one of those classes.
   - Example: a bank has old loan records. Each record is marked "defaulter" or "non-defaulter". We train a decision tree on them. Now the tree can say whether a new applicant is risky.

   Unsupervised classification (clustering)
   - The data has no label. The algorithm groups the records only by how similar they are.
   - Nobody tells it how many groups there are, or what each group means. It finds that from the data.
   - Example: a bank runs K-Means on customer transaction data. It gets natural groups such as high value customers, regular customers and dormant customers. No one marked these groups first.

   Main difference in one line: in supervised classification the classes are known before training. In clustering the groups come out of the data itself.

3. **Briefly explain supervised learning, unsupervised learning & reinforcement learning.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1341 (ET: N/A)]*

   Answer:
   - Supervised learning: learns from labelled data where the correct answer is already known, and then predicts the answer for new input. Used in classification and regression. Example: spam filtering, house price prediction.
   - Unsupervised learning: learns from unlabelled data and finds hidden groups or patterns by itself. Used in clustering and association. Example: grouping customers by spending habit.
   - Reinforcement learning: an agent acts inside an environment, gets reward or penalty, and slowly learns the best way to act. Example: robots, game playing, automatic trading.

   | Criteria | Supervised Learning | Unsupervised Learning | Reinforcement Learning |
   |---|---|---|---|
   | Definition | Learns from labelled data | Finds patterns in unlabelled data | Learns by acting inside an environment |
   | Type of data | Labelled data | Unlabelled data | No dataset; it gets reward or penalty |
   | Type of problem | Classification, Regression | Clustering, Association | Step by step decision making |
   | Supervision | Needs a teacher (the correct label) | No supervision | No supervision, only reward |
   | Algorithms | Decision Tree, SVM, KNN, Linear Regression | K-Means, Hierarchical, Apriori | Q-Learning, Deep Q-Network, SARSA |
   | Goal | Predict the correct output | Find hidden groups or rules | Get the highest total reward |
   | Applications | Medical diagnosis, fraud detection, spam filtering, price forecasting | Customer segmentation, anomaly detection | Self-driving cars, robotics, game AI |

4. **(b) What is the difference between supervised and unsupervised learning? Explain with examples.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)], [SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)], [DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

   Answer:

   | Point | Supervised Learning | Unsupervised Learning |
   |---|---|---|
   | Training data | Labelled. The correct output is given | Unlabelled. No output is given |
   | Goal | Predict the output for new input | Find hidden structure in the data |
   | Supervision | Learns with the help of known answers | Learns with no help at all |
   | Main types | Classification, Regression | Clustering, Association |
   | Algorithms | Decision Tree, SVM, KNN, Linear Regression | K-Means, Hierarchical clustering, Apriori |
   | Checking accuracy | Easy. Compare the prediction with the true label | Hard. There is no true answer to compare with |
   | Number of classes | Known before training | Not known. Found from the data |

   Example of supervised learning:
   We have 10,000 old emails. Each one is already marked "spam" or "not spam". We train the model on them. Now when a new email comes, the model marks it. Here the label was given, so it is supervised.

   Example of unsupervised learning:
   A bank has data of 50,000 customers, but no groups are marked. We run K-Means on it. The algorithm makes three groups by spending behaviour. Nobody told it about these groups, so it is unsupervised.

5. **Given some features of diabetic patient dataset with some labeled data. From this it can be predict whether this patient is diabetic or not. Is this supervised learning or unsupervised learning problem. Explain in one sentence.** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 433 (ET: BUET)]*

   Answer: It is a supervised learning problem, and more exactly a binary classification problem, because the dataset already has labels showing which patient is diabetic and which is not, and the model learns from those labels to classify a new patient.

6. **What do you mean by machine learning? Name three machine learning application in our daily life?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 680 (ET: N/A)]*

   Answer: Machine Learning is a branch of Artificial Intelligence. In it, a computer learns patterns from data and gets better at a job with experience. We do not write a fixed rule for every case.

   Simple example: to find spam, we do not write "if the subject has the word LOTTERY then it is spam". Instead we show the model thousands of old spam and non-spam emails, and it learns the pattern itself.

   Three applications in daily life:
   - Email spam filtering. Gmail looks at old mail patterns and puts new spam into the spam folder.
   - Recommendation systems. YouTube, Netflix and Daraz show you videos or products that people like you also liked.
   - Fraud detection. If your card is suddenly used in another country, the bank's model marks it as unusual and sends an alert.

## Model Evaluation & Datasets (5)

1. **Write down the Role of Validation set in ML.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1448 (ET: N/A)]*

   Answer: The validation set is a part of the data that we keep aside from training. We use it to tune the model and to check how well it is doing, before we touch the final test set.

   Roles of the validation set:
   - Choosing hyperparameters: things like learning rate, tree depth or number of hidden layers are picked by trying them and checking the validation score.
   - Catching overfitting early: training accuracy keeps going up but validation accuracy starts falling. That gap is the warning sign.
   - Model selection: if we have three or four candidate models, we compare them on the validation set and keep the best one.
   - Early stopping: we stop training as soon as the validation error stops getting better.
   - Protecting the test set: because all tuning happens on the validation set, the test set stays unseen. So the final score we report is honest.

2. **(b) Given following values:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*
 * **True Positive \text{(TP)} = 560**
 * **True Negative \text{(TN)} = 330**
 * **False Positive \text{(FP)} = 60**
 * **False Negative \text{(FN)} = 50**
**Calculate the following: (i) Accuracy (ii) Precision (iii) Recall (iv) F1 Score**

   Answer:

   Given: TP = 560, TN = 330, FP = 60, FN = 50
   Total = 560 + 330 + 60 + 50 = 1000

   (i) Accuracy

   Formula: Accuracy = (TP + TN) / (TP + TN + FP + FN)

   = (560 + 330) / 1000
   = 890 / 1000
   = 0.89 or 89%

   (ii) Precision

   Formula: Precision = TP / (TP + FP)

   = 560 / (560 + 60)
   = 560 / 620
   = 0.9032 or 90.32%

   (iii) Recall

   Formula: Recall = TP / (TP + FN)

   = 560 / (560 + 50)
   = 560 / 610
   = 0.9180 or 91.80%

   (iv) F1 Score

   Formula: F1 = 2 × (Precision × Recall) / (Precision + Recall)

   = 2 × (0.9032 × 0.9180) / (0.9032 + 0.9180)
   = 2 × 0.8291 / 1.8212
   = 1.6582 / 1.8212
   = 0.9105 or 91.05%

   Final answer: Accuracy = 89%, Precision = 90.32%, Recall = 91.80%, F1 Score = 91.05%

3. **b) How can we validate and check reliability of a machine learning model?** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*

   Answer: We validate a model by testing it on data that it never saw during training, and by using the right measure for the problem.

   Validation methods:
   - Train-validation-test split: we cut the data into three parts, often 70:15:15. The test part is used only once, at the very end.
   - K-fold cross validation: we cut the data into k parts. We train k times. Each time a different part is used as validation. Then we take the average score. This is more reliable than a single split.
   - Stratified k-fold: same as above, but it keeps the same class ratio in every fold. We need this when the data is imbalanced.
   - Hold-out validation: we test on a fresh dataset collected later.

   How to check reliability:
   - Compare training error and validation error. A big gap means overfitting. Both high means underfitting.
   - Pick the correct metric. Accuracy is fine for balanced data. For imbalanced data like fraud detection, use precision, recall, F1 and ROC-AUC. In fraud data, a model that says "not fraud" every time can still get 99% accuracy, which is useless.
   - Look at the confusion matrix to see which class is being mixed up.
   - Test on fresh production data now and then, because data drift slowly lowers accuracy.
   - Run the model with different random seeds and different splits. If the score jumps around a lot, the model is not stable.

4. **You are a designing a machine learning model for a binary classification problem. The model has three features: f1, f2, f3. Derive the objective and loss function for this problem.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 746 (ET: N/A)]*

   Answer:

   Model: for a binary classification problem with three features, we use logistic regression.

   Step 1: the linear part

   z = w1·f1 + w2·f2 + w3·f3 + b

   Here w1, w2, w3 are the weights and b is the bias.

   Step 2: the prediction

   ŷ = σ(z) = 1 / (1 + e^(−z))

   The sigmoid function squeezes z into a value between 0 and 1, so we can read it as a probability.

   Decision rule: class 1 if ŷ ≥ 0.5, otherwise class 0.

   Step 3: the loss function for one sample (binary cross entropy)

   L = −[ y·log(ŷ) + (1 − y)·log(1 − ŷ) ]

   Why this works:
   - If the true label y = 1, the formula becomes −log(ŷ). This is small only when ŷ is near 1.
   - If the true label y = 0, the formula becomes −log(1 − ŷ). This is small only when ŷ is near 0.
   - So the loss is low only when the model predicts the correct side with confidence.

   Step 4: the objective function over all n samples

   J(w, b) = −(1/n) × Σ [ yi·log(ŷi) + (1 − yi)·log(1 − ŷi) ]

   With L2 regularisation to stop overfitting:

   J(w, b) = −(1/n) × Σ [ yi·log(ŷi) + (1 − yi)·log(1 − ŷi) ] + (λ/2n) × Σ wj²

   Objective: make J(w, b) as small as possible by changing w1, w2, w3 and b.

   We normally do this with gradient descent, updating each weight as:

   wj = wj − α·(∂J/∂wj)

   where α is the learning rate.

5. **Write down the difference between test set and validation set.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033 (ET: BUET)]*

   Answer:

   | Point | Validation Set | Test Set |
   |---|---|---|
   | Purpose | Tune the hyperparameters and pick the best model | Give the final, honest score of the model |
   | When used | During training and tuning | Only once, after everything is finished |
   | How many times used | Many times | One time |
   | Effect on the model | It shapes the model, because we make choices from it | No effect at all |
   | Risk | Using it again and again leaks information, so the model can overfit to it | Stays clean, so the reported score can be trusted |

## Supervised Learning (Decision Trees) (4)

1. **What is Machine Learning? Mention some real-life applications.** *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer: Machine Learning is a branch of Artificial Intelligence. In it, a system learns patterns from data and gets better at a job with experience. We do not write a rule for every case by hand.

   Basic working steps:
   - Collect the data and clean it.
   - Pick the features, and split the data into training, validation and test sets.
   - Train the model so that its error on the training data becomes as small as possible.
   - Validate it, tune it, and finally test it on data it has never seen.

   Real life applications:
   - Fraud detection in card and mobile banking transactions.
   - Credit scoring, where a bank predicts if a person will repay the loan.
   - Email spam filtering.
   - Product and video recommendation on Daraz, YouTube and Netflix.
   - Face recognition and fingerprint matching in national ID and office attendance systems.
   - Speech recognition in voice assistants and call centres.
   - Medical diagnosis from X-ray and pathology images.
   - Demand and price forecasting in shops and agriculture.

2. **Decisiontree model in Machine Learning.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1448 (ET: N/A)]*

   Answer: A Decision Tree is a supervised learning model that looks like a tree. Each internal node asks a question about one feature. Each branch is an answer to that question. Each leaf gives the final class or value.

   ```mermaid
   graph TD
       A{Income >= 50000?} -->|Yes| B{Credit history good?}
       A -->|No| C[Reject loan]
       B -->|Yes| D[Approve loan]
       B -->|No| E[Reject loan]
   ```

   How it is built:
   - At each node we pick the feature that separates the classes best.
   - To measure "best" we use Information Gain or Gini Index for classification, and variance reduction for regression.
   - Then we repeat the same step on each branch, until a stopping rule is reached.

   Advantages:
   - Very easy to understand and to explain to a non-technical person.
   - Needs little data preparation. No scaling or normalisation required.
   - Handles both number data and category data.

   Disadvantages:
   - A deep tree overfits easily. It memorises the training data.
   - A small change in the data can change the whole tree.

   How we fix these: pruning (cutting back the tree), or using an ensemble like Random Forest.

3. **What is machine learning? Differentiate among supervised learning vs unsupervised learning vs reinforcement learning.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 339 (ET: BIBM)]*

   Answer: Machine Learning is the part of Artificial Intelligence where a computer learns from data and improves with experience, without being programmed with a rule for each case.

   | Point | Supervised | Unsupervised | Reinforcement |
   |---|---|---|---|
   | Input data | Labelled | Unlabelled | No dataset. It has an environment |
   | Learns from | The known correct output | Hidden structure in the data | Reward and penalty |
   | Goal | Predict the output for new input | Find groups or patterns | Collect the highest total reward |
   | Feedback | Direct, from the label | None | Delayed, through the reward |
   | Main types | Classification, Regression | Clustering, Association | Value based, Policy based |
   | Algorithms | Decision Tree, SVM, KNN | K-Means, Apriori | Q-Learning, SARSA |
   | Example | Predicting loan default | Grouping customers | Robot learning to walk |

4. **(ক) Decision Tree কী? উদাহরণসহ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 605 (ET: N/A)]*

   Answer: A Decision Tree is a supervised machine learning model. It takes a decision by asking a series of questions about the features. It has a tree shape:
   - Root node: the first question.
   - Internal nodes: the next questions.
   - Branches: the answers to a question.
   - Leaf nodes: the final decision.

   Example: should we play cricket today, based on the weather?

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

   Reading the tree:
   - Outlook is asked first, because it separates the classes best. We measure this with Information Gain.
   - If Outlook is Overcast, the answer is always Play. So it becomes a leaf at once.
   - If Outlook is Sunny, we then ask about Humidity. If it is Rainy, we ask about Wind.

   Each path from the root to a leaf gives a simple rule. For example: "if Outlook is Sunny and Humidity is High, then do not play".

   This is why decision trees are popular where the decision must be explained, such as loan approval in a bank. The bank can show the customer the exact rule that was applied.

## Generative AI & Explainable AI (XAI) (4)

1. **Imagine a government agency is developing an AI-based citizen service chatbot that can automatically generate responses, summarize documents, and provide policy information to citizens. Explain how Generative AI can be used to power such a system, and how Explainable AI (XAI) techniques can ensure that its responses are transparent, reliable, and accountable.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1428 (ET: E-Zone)]*

   Answer:

   How Generative AI can power the chatbot:
   - A Large Language Model reads the citizen's question written in normal Bangla or English, and writes a human-like reply. It does not pick from a fixed list of canned answers.
   - Retrieval Augmented Generation (RAG) is used. The model first searches the agency's own circulars, acts and forms. Then it writes the answer using only those documents. This keeps the reply tied to real policy and cuts down hallucination.
   - Document summarisation lets a citizen get a short summary of a long gazette or policy paper.
   - Multilingual support lets the same system serve both Bangla and English users.
   - Form filling help guides the citizen step by step through an application.

   ```mermaid
   flowchart LR
     U[Citizen question] --> R[Retriever]
     R --> D[(Agency circulars,<br/>acts, forms)]
     D --> R
     R --> L[Large Language Model]
     L --> A[Generated answer<br/>+ source citation]
     A --> U
   ```

   How Explainable AI keeps it transparent, reliable and accountable:
   - Source citation: every reply shows which circular or section it came from, so the citizen can check it himself.
   - Confidence score: when the model is not sure, it says so and passes the case to a human officer.
   - Feature attribution using LIME or SHAP: these show which input words pushed the answer the most. Developers use this to audit the behaviour.
   - Highlighting the used text: the system shows which part of the retrieved document it actually used.
   - Decision logging: every question and every reply is stored. So an audit can be done later and responsibility can be fixed.
   - Human in the loop: for sensitive matters like legal or financial advice, a human officer checks before the reply goes out.

   In short, Generative AI gives the service its quality, and Explainable AI gives it the accountability that a government service must have.

2. **b) Briefly discuss "Generative Artificial Intelligence (GAI)" & "Large Language Models (LLMs)".** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1346 (ET: N/A)]*

   Answer:

   Generative AI (GAI):
   - It is the type of AI that creates new content, such as text, image, audio, video or code. Older AI only classified or predicted; this one produces something new.
   - It learns the pattern of the training data and then makes new data that follows the same pattern.
   - Main techniques: GAN (Generative Adversarial Network), VAE (Variational Autoencoder), Diffusion models, and Transformer based language models.
   - Examples: ChatGPT for text, DALL-E and Midjourney for images, GitHub Copilot for code.

   Large Language Models (LLMs):
   - An LLM is a very large neural network built on the Transformer architecture. It is trained on a huge amount of text, and its basic job is to predict the next token.
   - It has billions of parameters. From the training text it picks up grammar, facts and reasoning patterns.
   - What it can do: answer questions, summarise, translate, generate code, and hold a conversation.
   - Limitations: it can hallucinate, that is give a wrong answer with full confidence. It has a knowledge cutoff date. It can carry bias from its training data. And training and running it costs a lot.

3. **LLM stands for __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: Large Language Model.

4. **What is ChatGPT? Write down the Pros and cons of ChatGPT.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 521 (ET: MIST)]*

   Answer: ChatGPT is a conversational AI system made by OpenAI. It is built on a Large Language Model of the GPT family. It takes a question in normal language and writes a human-like reply. It can also hold a long conversation, because it remembers the earlier messages of the same session.

   Pros:
   - Answers questions in normal language and explains hard topics in a simple way.
   - Available all day, replies at once, and can serve many users at the same time.
   - Helps in writing letters, reports, summaries and code, so it saves time.
   - Supports many languages, including Bangla.
   - Useful for study, because it can give examples and step by step explanations.

   Cons:
   - It can hallucinate, that is give a wrong answer with full confidence.
   - Its knowledge has a cutoff date, so very new events may be missing.
   - It can repeat the bias present in its training data.
   - Privacy risk if someone types confidential official information into it.
   - Depending on it too much can weaken a person's own thinking and writing skill.
   - It does not really understand meaning. It only predicts the most likely next word.

## Advanced Machine Learning & Deep Learning (RL, DL, Federated Learning) (3)

1. **Explain the concepts of Reinforcement Learning (RL), Deep Learning (DL), and Federated Learning (FL) in the context of Machine Learning. Briefly describe how each approach differs in its learning mechanism, data usage, and real-world applications.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1427 (ET: E-Zone)]*

   Answer:

   Reinforcement Learning (RL)
   - Learning mechanism: an agent takes an action inside an environment. It gets a reward or a penalty. It then updates its policy so that the total future reward becomes highest.
   - Data usage: there is no labelled dataset. The agent makes its own experience by trial and error.
   - Applications: robot navigation, game playing, traffic signal control, automated trading, dynamic pricing.

   Deep Learning (DL)
   - Learning mechanism: a neural network with many layers learns the features on its own. Backpropagation adjusts the weights to reduce the loss.
   - Data usage: needs a very large labelled dataset and heavy computing power, normally a GPU.
   - Applications: image and face recognition, speech recognition, machine translation, medical image diagnosis, cheque and document reading.

   Federated Learning (FL)
   - Learning mechanism: the model is sent to each device or branch. It is trained locally on local data. Only the model updates, not the data, are sent back to a central server. The server merges all the updates into one global model.
   - Data usage: the raw data never leaves the device, so privacy is protected. The data sits spread across many places and is often not of the same type everywhere.
   - Applications: mobile keyboard prediction, healthcare where hospital data cannot be shared, and banking where each branch keeps its customer data local but all of them still help train one shared fraud model.

   ```mermaid
   flowchart TD
     S[Central Server<br/>global model] -->|send model| D1[Device 1]
     S -->|send model| D2[Device 2]
     S -->|send model| D3[Device 3]
     D1 -->|send updates only| S
     D2 -->|send updates only| S
     D3 -->|send updates only| S
     D1 -.raw data stays here.- D1
   ```

   Key difference in one line: RL learns from reward, DL learns from large labelled data using deep networks, and FL learns across many devices without ever moving the data.

2. **Explain reinforcement learning in the field of Machine Learning?** *[BTCL Assistant Manager (Technical) 2023 compact it 593 (ET: BUET)]*

   Answer: Reinforcement Learning is a machine learning method where an agent learns which action to take by working inside an environment. For each action it gets a reward or a penalty. Its aim is to collect the highest total reward over time.

   Main elements:
   - Agent: the learner, the one who decides.
   - Environment: everything around the agent that it interacts with.
   - State: the current situation of the environment.
   - Action: what the agent can do in that state.
   - Reward: the number that the environment gives back after an action.
   - Policy: the strategy that tells which action to take in which state.

   ```mermaid
   graph LR
       AG[Agent] -->|Action| ENV[Environment]
       ENV -->|State| AG
       ENV -->|Reward| AG
   ```

   Working points:
   - The agent must balance exploration and exploitation. Exploration means trying new actions. Exploitation means using the best action it already knows.
   - Common algorithms: Q-Learning, SARSA and Deep Q-Network.
   - Example: a robot learns to walk. Moving forward gives a positive reward, falling gives a negative reward. After many tries, it learns a stable way to walk.

3. **Weak and strong learner ensemble learning in Machine learning.** *[GTCL Assistant Engineer (CSE) 2022 compact it 686 (ET: BUET)]*

   Answer: Ensemble learning means joining several models together, so that the group gives a better result than any single model alone.

   - Weak learner: a model whose accuracy is only a little better than random guessing. Example: a decision stump, which is a decision tree with only one level.
   - Strong learner: a model with high accuracy. Ensemble methods build a strong learner by combining many weak learners.

   Main ensemble techniques:

   | Technique | How models are trained | What it reduces | Example |
   |---|---|---|---|
   | Bagging | Many models trained in parallel on different random samples, then averaged or voted | Variance | Random Forest |
   | Boosting | Models trained one after another. Each new model focuses on the samples the last one got wrong | Bias | AdaBoost, Gradient Boosting, XGBoost |
   | Stacking | Several different models are trained, then a meta model learns how to combine them | Both | Stacked ensemble |

   ```mermaid
   flowchart TD
     D[Training Data] --> M1[Weak Learner 1]
     D --> M2[Weak Learner 2]
     D --> M3[Weak Learner 3]
     M1 --> C[Combine:<br/>vote / average / meta model]
     M2 --> C
     M3 --> C
     C --> S[Strong Learner]
   ```

   Why it works: each weak learner makes different mistakes. When we combine them, the random mistakes cancel each other out. So the accuracy and the stability both go up.

## Search Algorithms (Informed vs Uninformed Search) (1)

1. **Write down the difference between informed and uninformed search algorithm.** *[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

   Answer:

   | Point | Uninformed (Blind) Search | Informed (Heuristic) Search |
   |---|---|---|
   | Extra knowledge | Knows nothing beyond the problem itself | Uses a heuristic that guesses the cost to the goal |
   | Guidance | Searches blindly in a fixed order | Moves towards the most promising node |
   | Efficiency | Visits many useless nodes | Visits far fewer nodes |
   | Time and memory | Generally high | Generally lower |
   | Completeness | BFS and UCS are complete | Complete if the heuristic is admissible |
   | Optimality | BFS is optimal for equal cost, UCS is optimal | A* is optimal if the heuristic is admissible and consistent |
   | Examples | BFS, DFS, Depth Limited Search, Uniform Cost Search, Iterative Deepening | Greedy Best First Search, A* Search, AO* Search |

   About the heuristic:
   - h(n) is a guess of the cost from node n to the goal. Example: in a map problem, the straight line distance from a city to the destination.
   - A* uses f(n) = g(n) + h(n). Here g(n) is the real cost already spent, and h(n) is the guessed cost still remaining. This is why A* is both fast and optimal.

## Overfitting, Underfitting & Model Generalization (1)

1. **In machine learning. What will happen, when a machine is highly trained up a slight trained up?** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 395 (ET: BUET)]*

   Answer: If a model is trained too much it overfits. If it is trained too little it underfits. Both make the model perform badly on new data.

   Overfitting (highly trained up):
   - The model memorises the training data, including its noise. It does not learn the general pattern.
   - Training accuracy becomes very high, but validation and test accuracy fall.
   - It has high variance and low bias.
   - How to fix: stop training early, add more training data, use regularisation (L1 or L2), use dropout in neural networks, prune the decision tree, and use cross validation.

   Underfitting (slightly trained up):
   - The model is too simple, or it was trained for too few rounds. So it cannot catch the pattern even in the training data.
   - Both training accuracy and test accuracy stay low.
   - It has high bias and low variance.
   - How to fix: train longer, use a bigger model, add better features, and reduce regularisation.

   ```
   Underfitting            Good fit               Overfitting
   (high bias)                                   (high variance)

     o   o                   o   o                  o   o
   ---------              /‾‾‾‾‾‾\               /\  /\  /     o   o               /   o   o\             /  \/  \/                                                  (line touches every point)

   Training error: HIGH    Training error: LOW    Training error: VERY LOW
   Test error:     HIGH    Test error:     LOW    Test error:     HIGH
   ```

   The aim is the middle case, called a good fit. There, training error and validation error are both low and close to each other. This balance is called the bias-variance tradeoff.

## Association Rule Learning (Market Basket Analysis) (1)

1. **Which Machine Learning Algorithm is suitable for the case of Market - Basket Analysis? Explain the steps involved.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1364 (ET: BUET)]*

   Answer: The Apriori algorithm is suitable for Market Basket Analysis. It is an association rule learning method, and it comes under unsupervised learning. For very large datasets, FP-Growth is a faster choice.

   Three measures used:
   - Support: how often an itemset appears.
     Support(A) = number of transactions containing A / total transactions
   - Confidence: how often B is bought when A is bought.
     Confidence(A→B) = Support(A ∪ B) / Support(A)
   - Lift: how much more likely B becomes when A is present, compared to chance.
     Lift(A→B) = Confidence(A→B) / Support(B)
     A lift above 1 means there is a real positive link.

   Steps of the Apriori algorithm:
   - Fix a minimum support and a minimum confidence value.
   - Scan the transaction database and count the support of every single item. These are the 1-itemsets.
   - Drop the items whose support is below the minimum. Keep only the frequent 1-itemsets.
   - Join the frequent 1-itemsets to make candidate 2-itemsets. Count their support and drop the infrequent ones.
   - Repeat this join and prune step for 3-itemsets, 4-itemsets and so on, until no new frequent itemset is found.
   - From each frequent itemset, make all possible association rules.
   - Keep only the rules whose confidence is above the minimum. Then rank them by lift.

   ```mermaid
   flowchart TD
     A[Transaction database] --> B[Count support of 1-itemsets]
     B --> C{Support >= min_support?}
     C -->|No| D[Prune]
     C -->|Yes| E[Frequent 1-itemsets]
     E --> F[Join to make candidate 2-itemsets]
     F --> G[Count support and prune]
     G --> H{Any new frequent itemset?}
     H -->|Yes| F
     H -->|No| I[Generate association rules]
     I --> J{Confidence >= min_confidence?}
     J -->|Yes| K[Final rules, ranked by lift]
     J -->|No| D
   ```

   The Apriori property, which makes the pruning possible: if an itemset is frequent, then all its subsets must also be frequent. So if {bread} is not frequent, we do not even need to check {bread, milk}.

   Example: if the rule {bread, butter} → {milk} has support 20%, confidence 70% and lift 1.5, then the shop can keep milk near bread and butter, or give a combo discount.

## Clustering & Unsupervised Learning (K-Means, Hierarchical) (1)

1. **Consider the five points: P1 (0.07, 0.83), P2 (0.85, 0.14), P3 (0.66, 0.89), P4 (0.49, 0.64), and P5 (0.80, 0.46). Group first two points considering single-linkage hierarchical clustering technique.** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 473 (ET: N/A)]*

   Answer:

   Formula: the Euclidean distance between two points is

   d(A, B) = √[(x2 − x1)² + (y2 − y1)²]

   In agglomerative single-linkage clustering, every point starts as its own cluster. Then we merge the two clusters that have the smallest distance between them.

   Step 1: find the distance between every pair.
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

   Distance matrix:

   | | P1 | P2 | P3 | P4 | P5 |
   |---|---|---|---|---|---|
   | P1 | 0 | 1.0414 | 0.5930 | 0.4610 | 0.8184 |
   | P2 | 1.0414 | 0 | 0.7737 | 0.6161 | 0.3239 |
   | P3 | 0.5930 | 0.7737 | 0 | 0.3023 | 0.4522 |
   | P4 | 0.4610 | 0.6161 | 0.3023 | 0 | 0.3585 |
   | P5 | 0.8184 | 0.3239 | 0.4522 | 0.3585 | 0 |

   Step 2: find the smallest distance.
   - The smallest value in the whole matrix is 0.3023, which is d(P3, P4).

   Step 3: merge that pair.
   - P3 and P4 join into one cluster {P3, P4} at height 0.3023 in the dendrogram.
   - After this merge, the distance from {P3, P4} to any other point is the smaller of the two separate distances. This is what "single linkage" means.

   Final answer: the first two points grouped are P3 (0.66, 0.89) and P4 (0.49, 0.64), merged at a distance of 0.3023.
