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

   Answer: An activation function is a function we apply to the weighted sum of the inputs of a neuron, before the neuron gives its output. Its main job is to add non-linearity, so the network can learn complex patterns.

   Why we need it:
   - Without it, the network becomes only a straight line. However many layers we stack, if all of them are linear, the final output is just a linear combination of the input. So all the layers collapse into one.
   - Real data needs curved decision boundaries. A non-linear activation function lets the network draw those curves.
   - Without it, no network could do image recognition, NLP or speech processing.
   - It also keeps the output inside a fixed range, which makes training stable.
   - It lets the gradient flow backward during backpropagation, which is how the weights get updated.

   Common activation functions:

   | Function | Formula | Output range | Where we use it |
   |---|---|---|---|
   | Linear | y = x | −∞ to +∞ | Output layer for regression. We avoid it in hidden layers |
   | Sigmoid | σ(x) = 1 / (1 + e^−x) | 0 to 1 | Output layer for yes/no problems |
   | Tanh | f(x) = 2 / (1 + e^−2x) − 1 | −1 to +1 | Hidden layers. Zero centred, so it learns faster than sigmoid |
   | ReLU | A(x) = max(0, x) | 0 to ∞ | Hidden layers. Fast and simple, the most used one |
   | Leaky ReLU | f(x) = x if x > 0, else αx | −∞ to ∞ | Fixes the dying ReLU problem |
   | Softmax | turns outputs into probabilities | 0 to 1, all add to 1 | Output layer when there are many classes |

   Effect on training:
   - ReLU trains faster, because it avoids the vanishing gradient problem.
   - Sigmoid and Tanh can slow down learning in deep networks, because their gradients become very small.

2. **What does the axon of neural network do?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

   Answer: The axon carries the output of a neuron and sends it to the next neurons.

   - In a biological neuron, dendrites take the input, the cell body processes it, and the axon carries the output away.
   - In an artificial neural network, the axon matches the output connection of a neuron.
   - It takes the value produced by the activation function, multiplies it by the connection weight, and passes it to the neurons of the next layer.

3. **Write difference between machine learning and deep learning.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 681 (ET: N/A)]*

   Answer:

   | Basis | Machine Learning | Deep Learning |
   |---|---|---|
   | Definition | Algorithms that learn from data and get better with experience | A subset of ML that uses neural networks with many layers |
   | Data requirement | Works well with small to medium datasets | Needs large datasets to learn well |
   | Feature extraction | Manual. An expert must pick the features | Automatic. It learns the features straight from the data |
   | Training time | Faster, needs fewer resources | Slower, needs much more computing power |
   | Accuracy | Depends on the quality of the features and the algorithm | Usually higher, if there is enough data |
   | Hardware | Can run on a normal CPU | Often needs a GPU or TPU |
   | Interpretability | Easy to explain the decision | Hard to explain. It works like a black box |
   | Examples | Spam detection, stock prediction, recommendation systems | Image classification, speech recognition, NLP |

   Two main points to remember:
   - In Machine Learning, we tell the model which features to look at. In Deep Learning, the model finds the features itself.
   - Deep Learning is a subset of Machine Learning, and Machine Learning is a subset of Artificial Intelligence.

4. **What is Deep learning?** *[BARC Data Entry Officer 10.09.2022 compact it 703 (ET: N/A)]*

   Answer: Deep Learning is a subset of Machine Learning. It uses artificial neural networks with many hidden layers, and it learns complex patterns straight from raw data such as images, sound and text.

   Key points:
   - The word "deep" means the network has many hidden layers between the input and the output.
   - Each layer learns a bigger idea than the layer below it. For a face: the first layer finds edges, the next finds shapes like an eye or a nose, and the last finds the whole face.
   - We do not have to pick the features by hand. The network learns them itself.
   - It needs a large dataset and heavy computing power, usually a GPU or TPU.

   Common architectures:
   - ANN: the basic multi-layer network, used for normal table data.
   - CNN, Convolutional Neural Network: used for images and video.
   - RNN and LSTM: used for sequence data such as text, speech and time series.

   Applications: image recognition, speech recognition, machine translation, self-driving cars and medical image diagnosis.

5. **What is Artificial Neural Network (ANN)? Difference between deep learning technique and Traditional machine learning technique.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 856 (ET: N/A)]*

   Answer: An Artificial Neural Network (ANN) is a computing model built on the idea of the human brain. It is made of small units called neurons, arranged in layers.

   Structure:
   - Input layer: takes the raw data in.
   - Hidden layers: one or more layers that do the actual processing.
   - Output layer: gives the final result.

   How it works:
   - Every connection between two neurons carries a number called a weight.
   - A neuron adds up all its weighted inputs, adds a bias, and passes the sum through an activation function.
   - The result goes forward to the next layer. This is called forward propagation.
   - Backpropagation then compares the output with the correct answer and slowly changes the weights to reduce the error. This is how the network learns.

   Difference between Deep Learning and Traditional Machine Learning:

   | Basis | Machine Learning | Deep Learning |
   |---|---|---|
   | Definition | Algorithms that learn from data and get better with experience | A subset of ML that uses neural networks with many layers |
   | Data requirement | Works well with small to medium datasets | Needs large datasets to learn well |
   | Feature extraction | Manual. An expert must pick the features | Automatic. It learns the features straight from the data |
   | Training time | Faster, needs fewer resources | Slower, needs much more computing power |
   | Accuracy | Depends on the quality of the features and the algorithm | Usually higher, if there is enough data |
   | Hardware | Can run on a normal CPU | Often needs a GPU or TPU |
   | Interpretability | Easy to explain the decision | Hard to explain. It works like a black box |
   | Examples | Spam detection, stock prediction, recommendation systems | Image classification, speech recognition, NLP |

6. **Write LSTM gates name in AI.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 858 (ET: N/A)]*

   Answer: An LSTM (Long Short Term Memory) cell has three gates.

   | Gate | What it does |
   |---|---|
   | Forget gate | Decides which old information to throw away from the cell state |
   | Input gate | Decides which new information to store in the cell state |
   | Output gate | Decides which part of the cell state to send out as the cell output |

   Simple way to remember: the forget gate erases, the input gate writes, and the output gate reads.

   Why LSTM was made: a normal RNN forgets long term information, because of the vanishing gradient problem. These three gates let an LSTM hold information for a long time, so it works well on long sequences such as sentences and time series.

7. **Draw the single layer of ANN.** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 880 (ET: BUET)]*

   Answer: A single layer ANN is also called a perceptron. It has only an input layer joined directly to an output layer. There is no hidden layer.

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
   - All the products are added together, and the bias b is added too.
   - This sum goes into an activation function, such as a step function or sigmoid.
   - The result of the activation function is the final output.

   Limitation: a single layer network can only separate data with a straight line. So it cannot solve the XOR problem. To solve XOR we need at least one hidden layer, which makes it a multi-layer perceptron.

## Machine Learning Paradigms (Supervised vs Unsupervised) (6)

1. **(a) Describe the following terms:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*
 * **(i) Supervised learning**
 * **(ii) Unsupervised learning**
 * **(iii) Reinforcement learning**

   Answer:

   (i) Supervised learning
   - It learns from labelled data. Every input already carries its correct output.
   - The model learns the link between input and output. Then it predicts the output for new data.
   - Two types: classification, where the output is a category, and regression, where the output is a number.
   - It needs a teacher, because the correct answers are supplied.
   - Example: we give the model 10,000 old emails, each already marked spam or not spam. Now it can mark a new email.

   (ii) Unsupervised learning
   - It learns from unlabelled data. No correct answer is given.
   - The model finds hidden structure or groups on its own.
   - Two types: clustering, which makes groups, and association, which finds rules between items.
   - Example: we give it customer spending data with no groups marked. It forms groups such as high spenders, normal spenders and inactive customers.

   (iii) Reinforcement learning
   - An agent acts inside an environment. After each action it gets a reward or a penalty.
   - There is no dataset. The agent learns by trial and error, and tries to collect the highest total reward.
   - Main parts: agent, environment, state, action, reward.
   - Example: a robot learns to walk. Each step forward gives a reward, each fall gives a penalty.

   Comparison:

   | Criteria | Supervised Learning | Unsupervised Learning | Reinforcement Learning |
   |---|---|---|---|
   | Definition | Learns from labelled data | Finds patterns in unlabelled data | Learns by acting inside an environment |
   | Type of data | Labelled data | Unlabelled data | No dataset. It gets a reward or a penalty |
   | Type of problem | Classification, Regression | Clustering, Association | Step by step decision making |
   | Supervision | Needs a teacher, that is the correct label | No supervision | No supervision, only reward |
   | Algorithms | Decision Tree, SVM, KNN, Linear Regression | K-Means, Hierarchical, Apriori | Q-Learning, Deep Q-Network, SARSA |
   | Goal | Predict the correct output | Find hidden groups or rules | Collect the highest total reward |
   | Applications | Medical diagnosis, fraud detection, spam filtering, price forecasting | Customer segmentation, anomaly detection | Self-driving cars, robotics, game AI |

2. **a) Define the term "Data Mining". Explain supervised and unsupervised classification with suitable example.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*

   Answer: Data Mining is the process of finding useful patterns and insights inside large datasets. It uses statistics, machine learning and computing techniques together.

   Why we use it: an organisation studies its old data through data mining, and then takes decisions based on that data instead of on guesswork.

   Main tasks of data mining:
   - Classification and prediction: Bayes classification, rule based classification, k-nearest neighbour.
   - Regression analysis: linear and multiple linear regression, support vector regression.
   - Clustering: partitioning methods such as k-means, and hierarchical methods.
   - Association rule mining: frequent pattern mining, Apriori algorithm, FP-Growth, market basket analysis.
   - Outlier detection: finding records that do not fit the normal pattern.

   Supervised classification
   - The training data is labelled. Every record already carries its class.
   - The model learns the boundary between the classes. Then it puts a new record into one of them.
   - The number of classes and their meaning are fixed before training.
   - Example: a bank has old loan records, each marked "defaulter" or "non-defaulter". We train a decision tree on them. Now the tree can say whether a new applicant is risky.

   Unsupervised classification, also called clustering
   - The data has no label. The algorithm groups the records only by how similar they are.
   - Nobody tells it how many groups there are, or what each group means. It finds that from the data itself.
   - Example: a bank runs K-Means on customer transaction data. It gets natural groups such as high value customers, regular customers and inactive customers. No one marked these groups first.

   Main difference in one line: in supervised classification the classes are known before training, but in clustering the groups come out of the data itself.

3. **Briefly explain supervised learning, unsupervised learning & reinforcement learning.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1341 (ET: N/A)]*

   Answer:
   - Supervised learning: learns from labelled data, where the correct answer is already known. Then it predicts the answer for new input. Used for classification and regression. Example: spam filtering, house price prediction.
   - Unsupervised learning: learns from unlabelled data and finds hidden groups or patterns by itself. Used for clustering and association. Example: grouping customers by spending habit.
   - Reinforcement learning: an agent acts inside an environment, gets a reward or a penalty, and slowly learns the best way to act. Example: robots, game playing, automatic trading.

   | Criteria | Supervised Learning | Unsupervised Learning | Reinforcement Learning |
   |---|---|---|---|
   | Definition | Learns from labelled data | Finds patterns in unlabelled data | Learns by acting inside an environment |
   | Type of data | Labelled data | Unlabelled data | No dataset. It gets a reward or a penalty |
   | Type of problem | Classification, Regression | Clustering, Association | Step by step decision making |
   | Supervision | Needs a teacher, that is the correct label | No supervision | No supervision, only reward |
   | Algorithms | Decision Tree, SVM, KNN, Linear Regression | K-Means, Hierarchical, Apriori | Q-Learning, Deep Q-Network, SARSA |
   | Goal | Predict the correct output | Find hidden groups or rules | Collect the highest total reward |
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
   | Complexity | Simpler | More complex |

   Example of supervised learning:
   We have 10,000 old emails. Each one is already marked "spam" or "not spam". We train the model on them. When a new email arrives, the model marks it. The label was given to us, so this is supervised.

   Example of unsupervised learning:
   A bank has data on 50,000 customers, but no groups are marked. We run K-Means on it. The algorithm forms three groups by spending behaviour. Nobody told it about these groups, so this is unsupervised.

5. **Given some features of diabetic patient dataset with some labeled data. From this it can be predict whether this patient is diabetic or not. Is this supervised learning or unsupervised learning problem. Explain in one sentence.** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 433 (ET: BUET)]*

   Answer: It is a supervised learning problem. More exactly, it is a binary classification problem, because the dataset already carries labels showing which patient is diabetic and which is not, and the model learns from those labels to classify a new patient.

6. **What do you mean by machine learning? Name three machine learning application in our daily life?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 680 (ET: N/A)]*

   Answer: Machine Learning is a branch of Artificial Intelligence. It lets a computer learn patterns from data and make predictions or decisions, without a human writing a rule for every case.

   Simple example: to catch spam, we do not write "if the subject has the word LOTTERY then it is spam". Instead we show the model thousands of old spam and non-spam emails, and it learns the pattern itself.

   Three applications in daily life:
   - Email spam filtering: Gmail studies old mail patterns and moves new spam into the spam folder.
   - Recommendation systems: YouTube, Netflix and Daraz show you videos or products that similar users also liked.
   - Fraud detection: if your card is suddenly used in another country, the bank's model marks it as unusual and sends an alert.

## Model Evaluation & Datasets (5)

1. **Write down the Role of Validation set in ML.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1448 (ET: N/A)]*

   Answer: The validation set is the part of the data we keep aside from training. We use it to tune the model and to check how well it is doing, before we ever touch the test set.

   Roles of the validation set:
   - Tuning hyperparameters: we set values like learning rate, tree depth or number of hidden layers by trying them and checking the validation score.
   - Catching overfitting early: training accuracy keeps rising while validation accuracy starts falling. That gap is the warning sign.
   - Model selection: if we have several candidate models, we compare them on the validation set and keep the best one.
   - Early stopping: we stop training as soon as the validation error stops improving.
   - Keeping the test set clean: because all tuning happens on the validation set, the test set stays unseen. So the final score we report is honest.

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

   Accuracy = (TP + TN) / (TP + TN + FP + FN)

   = (560 + 330) / 1000
   = 890 / 1000
   = 0.89 or 89%

   (ii) Precision

   Precision = TP / (TP + FP)

   = 560 / (560 + 60)
   = 560 / 620
   = 0.9032 or 90.32%

   (iii) Recall

   Recall = TP / (TP + FN)

   = 560 / (560 + 50)
   = 560 / 610
   = 0.9180 or 91.80%

   (iv) F1 Score

   F1 = 2 × (Precision × Recall) / (Precision + Recall)

   = 2 × (0.9032 × 0.9180) / (0.9032 + 0.9180)
   = 2 × 0.8291 / 1.8212
   = 1.6582 / 1.8212
   = 0.9105 or 91.05%

   Final answer: Accuracy = 89%, Precision = 90.32%, Recall = 91.80%, F1 Score = 91.05%

3. **b) How can we validate and check reliability of a machine learning model?** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*

   Answer: We validate a model by testing it on data it never saw during training, and by using the right metric for the problem.

   Validation methods:
   - Train-validation-test split: we cut the data into three parts, often 70:15:15. We use the test part only once, at the very end.
   - K-fold cross validation: we cut the data into k parts and train k times. Each time a different part becomes the validation set. Then we take the average score. This is more reliable than a single split.
   - Stratified k-fold: the same idea, but it keeps the class ratio the same in every fold. We need this when the data is imbalanced.
   - Hold-out validation: we test on a completely fresh dataset collected later.

   How we check reliability:
   - Compare training error with validation error. A big gap means overfitting. Both high means underfitting.
   - Use the correct metric. Accuracy is fine for balanced data. For imbalanced data such as fraud detection, accuracy is misleading, because a model that always says "not fraud" can still score 99%. There we must use precision, recall, F1 and ROC-AUC.
   - Study the confusion matrix, to see which class is being mixed up.
   - Test on fresh production data from time to time, because data drift slowly lowers accuracy.
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

   Step 3: the loss function for one sample, called binary cross entropy

   L = −[ y·log(ŷ) + (1 − y)·log(1 − ŷ) ]

   Why this formula works:
   - If the true label y = 1, the formula becomes −log(ŷ). This is small only when ŷ is close to 1.
   - If the true label y = 0, the formula becomes −log(1 − ŷ). This is small only when ŷ is close to 0.
   - So the loss stays low only when the model predicts the correct side with confidence.

   Step 4: the objective function over all n samples

   J(w, b) = −(1/n) × Σ [ yi·log(ŷi) + (1 − yi)·log(1 − ŷi) ]

   With L2 regularisation, to stop overfitting:

   J(w, b) = −(1/n) × Σ [ yi·log(ŷi) + (1 − yi)·log(1 − ŷi) ] + (λ/2n) × Σ wj²

   Objective: make J(w, b) as small as possible by changing w1, w2, w3 and b.

   We normally do this with gradient descent. Each weight is updated as:

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

   Answer: Machine Learning is a branch of Artificial Intelligence. It lets a computer learn patterns from data and make predictions or decisions, without a human writing a rule for every case. It gets better with experience.

   Basic working steps:
   - Collect the data and clean it.
   - Pick the features, and split the data into training, validation and test sets.
   - Train the model, so its error on the training data becomes as small as possible.
   - Validate it, tune it, and finally test it on data it has never seen.
   - Put it to use, and keep improving it with new data.

   Real life applications:
   - Fraud detection in card and mobile banking transactions.
   - Credit scoring, where a bank predicts if a person will repay a loan.
   - Email spam filtering.
   - Product and video recommendation on Daraz, YouTube and Netflix.
   - Face recognition and fingerprint matching in national ID and office attendance systems.
   - Speech recognition in voice assistants and call centres.
   - Medical diagnosis from X-ray and pathology images.
   - Demand and price forecasting in shops and agriculture.

2. **Decisiontree model in Machine Learning.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1448 (ET: N/A)]*

   Answer: A Decision Tree is a supervised learning algorithm. We use it for both classification and regression. It has a tree structure made of a root node, branches, internal nodes and leaf nodes.

   Terminology:
   - Root node: the starting point. It holds all the training data.
   - Internal node: a test on one attribute, that is a question.
   - Branch: one possible answer to that question. It leads from one node to the next.
   - Leaf node: the end point. It gives the final prediction, a class label for classification or a number for regression.

   How splitting works:
   - The tree divides the dataset again and again. Each time it picks the feature that gives the purest groups.
   - It keeps dividing until a group holds only one class, or until no further split makes the groups purer.

   Measures used to pick the best attribute:
   - Entropy: it measures the impurity of a dataset. Higher entropy means more uncertainty.
     H(X) = −Σ(p_i × log₂ p_i)
   - Information Gain: it measures how much the uncertainty falls after a split. We pick the attribute with the highest gain.
     Gain(S, A) = Entropy(S) − Σ(|S_v| / |S|) × Entropy(S_v)
   - Gini Index: it measures how often a randomly picked item would be put in the wrong class. A lower value means a purer split.
     Gini = 1 − Σ(p_i²)

   Example:

   ```mermaid
   graph TD
       A{Income >= 50000?} -->|Yes| B{Credit history good?}
       A -->|No| C[Reject loan]
       B -->|Yes| D[Approve loan]
       B -->|No| E[Reject loan]
   ```

   Advantages:
   - Easy to understand and easy to explain to a non-technical person.
   - Flexible. It handles both number data and category data.
   - Needs very little data preparation. No scaling or normalisation is required.

   Disadvantages:
   - A deep tree overfits easily. It memorises the training data instead of learning the pattern.
   - A small change in the data can change the whole tree.
   - Gini Index tends to prefer child nodes of equal size, even when that is not best for accuracy.

   How we control these: pruning, that is cutting the tree back, or using an ensemble such as Random Forest.

3. **What is machine learning? Differentiate among supervised learning vs unsupervised learning vs reinforcement learning.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 339 (ET: BIBM)]*

   Answer: Machine Learning is the branch of Artificial Intelligence where a computer learns from data and improves with experience, instead of being programmed with a rule for each case.

   | Criteria | Supervised | Unsupervised | Reinforcement |
   |---|---|---|---|
   | Input data | Labelled | Unlabelled | No dataset. It has an environment |
   | Learns from | The known correct output | Hidden structure in the data | Reward and penalty |
   | Goal | Predict the output for new input | Find groups or patterns | Collect the highest total reward |
   | Feedback | Direct, from the label | None | Delayed, through the reward |
   | Main types | Classification, Regression | Clustering, Association | Value based, Policy based |
   | Algorithms | Decision Tree, SVM, KNN | K-Means, Apriori | Q-Learning, SARSA |
   | Example | Predicting loan default | Grouping customers by spending | A robot learning to walk |

   One line each:
   - Supervised: learning with a teacher who gives the answers.
   - Unsupervised: learning with no teacher, only finding groups.
   - Reinforcement: learning from reward and punishment, like training a pet.

4. **(ক) Decision Tree কী? উদাহরণসহ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 605 (ET: N/A)]*

   Answer: A Decision Tree is a supervised learning algorithm. It reaches a decision by asking a series of questions about the features. It has a tree structure:
   - Root node: the first question. It holds all the data.
   - Internal nodes: the next questions.
   - Branches: the possible answers to a question.
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
   - Outlook is asked first, because it gives the highest Information Gain, that is it separates the classes best.
   - If Outlook is Overcast, the answer is always Play. So it becomes a leaf at once.
   - If Outlook is Sunny, we then ask about Humidity. If it is Rainy, we ask about Wind.

   Each path from the root to a leaf gives us one simple rule. For example: if Outlook is Sunny and Humidity is High, then do not play.

   Why decision trees are popular: the rules are readable. In a bank loan system, the bank can show the customer the exact rule that was applied to reject the loan. Most other models cannot do that.

## Generative AI & Explainable AI (XAI) (4)

1. **Imagine a government agency is developing an AI-based citizen service chatbot that can automatically generate responses, summarize documents, and provide policy information to citizens. Explain how Generative AI can be used to power such a system, and how Explainable AI (XAI) techniques can ensure that its responses are transparent, reliable, and accountable.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1428 (ET: E-Zone)]*

   Answer:

   How Generative AI can power the chatbot:
   - A Large Language Model reads the citizen's question written in normal Bangla or English, and writes a human-like reply. It does not pick from a fixed list of ready made answers.
   - Retrieval Augmented Generation (RAG) is the key technique here. The system first searches the agency's own circulars, acts and forms. Then the model writes the answer using only those documents. RAG grounds the reply in real papers, so hallucination goes down sharply.
   - Summarisation lets a citizen get a short summary of a long gazette or policy paper.
   - Multilingual support lets the same system serve Bangla and English users.
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

   How Explainable AI makes it transparent, reliable and accountable:
   - Source citation: every reply shows which circular or section it came from. The citizen can then check it himself.
   - Confidence score: when the model is not sure, it says so and passes the case to a human officer.
   - Feature attribution with LIME or SHAP: these show which input words pushed the answer the most. Developers use this to audit the behaviour.
   - Highlighting the used text: the system shows which part of the retrieved document it actually used.
   - Decision logging: every question and every reply is stored. So an audit can be done later, and responsibility can be fixed.
   - Human in the loop: for sensitive matters such as legal or financial advice, a human officer checks the reply before it goes out.

   In short: Generative AI gives the service its quality, and Explainable AI gives it the accountability that a government service must have.

2. **b) Briefly discuss "Generative Artificial Intelligence (GAI)" & "Large Language Models (LLMs)".** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1346 (ET: N/A)]*

   Answer:

   Generative AI (GAI)
   - Generative AI is a type of artificial intelligence that creates new content, such as text, image, music or even code. It learns the patterns of existing data and then produces original output that looks human made.
   - How it differs from traditional AI: older, discriminative AI only sorts data into classes, such as marking an email spam or not spam. Generative AI actually produces new data.

   Main model types:
   - Transformer or autoregressive models: they predict the next token one at a time. Self attention lets the model see the whole input so far. GPT models work this way.
   - Diffusion models: they start from pure random noise and slowly clean it up, step by step, until an image appears. Stable Diffusion and DALL·E work this way.
   - GAN, Generative Adversarial Network: a generator and a discriminator train against each other. It gives sharp output, but training can be unstable.
   - VAE, Variational Autoencoder: it compresses data into a small representation, which gives controlled generation.
   - Encoder-decoder models: the encoder turns the input into a dense form, and the decoder writes the output. Good for translation and summarisation.

   Large Language Models (LLMs)
   - An LLM is a very large neural network built on the Transformer architecture. It is pre-trained on a huge amount of text by self-supervised learning, and its basic job is to predict the next token.
   - It has billions of parameters. From the training text it picks up grammar, facts and reasoning patterns.
   - We can adapt an LLM by fine tuning, using methods such as LoRA, QLoRA and RLHF.
   - We can also improve it with Retrieval Augmented Generation (RAG). There the model first fetches real documents and answers from them, which cuts down hallucination.
   - What it can do: answer questions, summarise, translate, write code and hold a conversation.

   Limitations:
   - The output is only as good and as fair as the training data.
   - It can give irrelevant results, and we have limited control over it.
   - It needs huge computing power, so it is expensive.
   - It raises worries about deepfakes, misinformation and privacy.

3. **LLM stands for __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: Large Language Model.

4. **What is ChatGPT? Write down the Pros and cons of ChatGPT.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 521 (ET: MIST)]*

   Answer: ChatGPT is a conversational AI system made by OpenAI. It is built on a Large Language Model of the GPT family. It takes a question in normal language and writes a human-like reply. It can also hold a long conversation, because it remembers the earlier messages of the same session.

   Pros:
   - It answers questions in normal language and explains hard topics simply.
   - It is available all day, replies at once, and serves many users at the same time.
   - It helps in writing letters, reports, summaries and code, so it saves time.
   - It supports many languages, including Bangla.
   - It is useful for study, because it gives examples and step by step explanations.

   Cons:
   - It can hallucinate, that is give a wrong answer with full confidence.
   - Its knowledge has a cutoff date, so very recent events may be missing.
   - It can repeat the bias present in its training data.
   - There is a privacy risk if someone types confidential official information into it.
   - Depending on it too much can weaken a person's own thinking and writing skill.
   - It does not really understand meaning. It only predicts the most likely next word.

## Advanced Machine Learning & Deep Learning (RL, DL, Federated Learning) (3)

1. **Explain the concepts of Reinforcement Learning (RL), Deep Learning (DL), and Federated Learning (FL) in the context of Machine Learning. Briefly describe how each approach differs in its learning mechanism, data usage, and real-world applications.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1427 (ET: E-Zone)]*

   Answer:

   Reinforcement Learning (RL)
   - Learning mechanism: an agent learns by trial and error. It takes an action in an environment, gets a reward or a penalty, and updates its policy so the total future reward becomes highest.
   - Data usage: there is no labelled dataset. The agent makes its own data by interacting with the environment.
   - Applications: robotics, game playing AI, industrial process control, traffic signal control, automated trading.

   Deep Learning (DL)
   - Learning mechanism: a neural network with many hidden layers learns the features on its own. Backpropagation adjusts the weights to cut the loss.
   - Data usage: it needs a very large labelled dataset and heavy computing power, normally a GPU or TPU.
   - Applications: image and face recognition, speech recognition, machine translation, medical image diagnosis, cheque and document reading.

   Federated Learning (FL)
   - Learning mechanism: the model is sent to each device or branch. It trains locally on local data. Only the model updates go back to a central server, which merges them into one global model.
   - Data usage: the raw data never leaves the device, so privacy is protected. The data is spread out, and it is often not of the same kind everywhere.
   - Applications: mobile keyboard prediction, healthcare where hospital data cannot be shared, and banking where each branch keeps its customer data local but all branches still help train one shared fraud model.

   ```mermaid
   flowchart TD
     S[Central Server<br/>global model] -->|send model| D1[Device 1]
     S -->|send model| D2[Device 2]
     S -->|send model| D3[Device 3]
     D1 -->|send weight updates only| S
     D2 -->|send weight updates only| S
     D3 -->|send weight updates only| S
   ```

   Key difference in one line: RL learns from reward, DL learns from large labelled data using deep networks, and FL learns across many devices without ever moving the data.

2. **Explain reinforcement learning in the field of Machine Learning?** *[BTCL Assistant Manager (Technical) 2023 compact it 593 (ET: BUET)]*

   Answer: Reinforcement Learning is a branch of machine learning where an agent learns to take decisions by trial and error, so that its total reward over time becomes highest. It learns by interacting with an environment and getting feedback on its performance.

   Key elements:
   - Agent: the decision maker, the one who acts.
   - Environment: the world in which the agent works.
   - State: the current situation of the environment.
   - Action: the moves the agent can make.
   - Reward: the feedback from the environment, positive or negative.

   Core components of an RL system:
   - Policy: it maps a state to an action. It can be a simple rule or a complex computation.
   - Reward signal: it guides the agent. It represents the goal of the whole problem.
   - Value function: it judges the long term benefit, not just the reward right now.
   - Model: it copies the environment, so the agent can predict what an action will do.

   Agent-environment interaction loop:

   ```mermaid
   graph LR
       AG[Agent] -->|Action| ENV[Environment]
       ENV -->|New State| AG
       ENV -->|Reward| AG
   ```

   The steps repeat like this:
   - The agent looks at the current state of the environment.
   - It picks an action using its policy, and performs it.
   - The environment gives back a new state and a reward.
   - The agent updates its policy or value function from that reward.
   - The loop repeats.

   Exploration and exploitation:
   - Exploration means trying new actions, to find a better strategy.
   - Exploitation means using the best action we already know.
   - The agent must balance the two. Too much exploration wastes time, too much exploitation misses better options.

   Main algorithm, Q-Learning:

   Q(s,a) = Q(s,a) + α[ r + γ · max Q(s',a') − Q(s,a) ]

   Here α is the learning rate and γ discounts the future rewards.

   Other algorithms: SARSA and Deep Q-Network (DQN).

   Applications: robotics and factory automation, game playing AI such as chess and Go, industrial process control, and personalised learning systems.

   Example: a robot learns to walk. Moving forward gives a positive reward, falling gives a negative reward. After many attempts it learns a stable way to walk.

3. **Weak and strong learner ensemble learning in Machine learning.** *[GTCL Assistant Engineer (CSE) 2022 compact it 686 (ET: BUET)]*

   Answer: Ensemble learning means joining several models together, so the group gives a better result than any single model alone.

   - Weak learner: a model whose accuracy is only slightly better than random guessing. Example: a decision stump, that is a decision tree with only one level.
   - Strong learner: a model with high accuracy. Ensemble methods build a strong learner out of many weak learners.

   Main ensemble techniques:

   | Technique | How the models are trained | What it reduces | Example |
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

   Why it works: each weak learner makes different mistakes. When we combine them, the random mistakes cancel each other out. So both accuracy and stability go up.

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
