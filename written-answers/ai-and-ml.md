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

2. **a) Define the term "Data Mining". Explain supervised and unsupervised classification with suitable example.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*

3. **Briefly explain supervised learning, unsupervised learning & reinforcement learning.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1341 (ET: N/A)]*

4. **(b) What is the difference between supervised and unsupervised learning? Explain with examples.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)], [SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)], [DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

5. **Given some features of diabetic patient dataset with some labeled data. From this it can be predict whether this patient is diabetic or not. Is this supervised learning or unsupervised learning problem. Explain in one sentence.** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 433 (ET: BUET)]*

6. **What do you mean by machine learning? Name three machine learning application in our daily life?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 680 (ET: N/A)]*

## Model Evaluation & Datasets (5)

1. **Write down the Role of Validation set in ML.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1448 (ET: N/A)]*

2. **(b) Given following values:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*
 * **True Positive \text{(TP)} = 560**
 * **True Negative \text{(TN)} = 330**
 * **False Positive \text{(FP)} = 60**
 * **False Negative \text{(FN)} = 50**
**Calculate the following: (i) Accuracy (ii) Precision (iii) Recall (iv) F1 Score**

3. **b) How can we validate and check reliability of a machine learning model?** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*

4. **You are a designing a machine learning model for a binary classification problem. The model has three features: f1, f2, f3. Derive the objective and loss function for this problem.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 746 (ET: N/A)]*

5. **Write down the difference between test set and validation set.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033 (ET: BUET)]*

## Supervised Learning (Decision Trees) (4)

1. **What is Machine Learning? Mention some real-life applications.** *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

2. **Decisiontree model in Machine Learning.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1448 (ET: N/A)]*

3. **What is machine learning? Differentiate among supervised learning vs unsupervised learning vs reinforcement learning.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 339 (ET: BIBM)]*

4. **(ক) Decision Tree কী? উদাহরণসহ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 605 (ET: N/A)]*

## Generative AI & Explainable AI (XAI) (4)

1. **Imagine a government agency is developing an AI-based citizen service chatbot that can automatically generate responses, summarize documents, and provide policy information to citizens. Explain how Generative AI can be used to power such a system, and how Explainable AI (XAI) techniques can ensure that its responses are transparent, reliable, and accountable.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1428 (ET: E-Zone)]*

2. **b) Briefly discuss "Generative Artificial Intelligence (GAI)" & "Large Language Models (LLMs)".** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1346 (ET: N/A)]*

3. **LLM stands for __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

4. **What is ChatGPT? Write down the Pros and cons of ChatGPT.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 521 (ET: MIST)]*

## Advanced Machine Learning & Deep Learning (RL, DL, Federated Learning) (3)

1. **Explain the concepts of Reinforcement Learning (RL), Deep Learning (DL), and Federated Learning (FL) in the context of Machine Learning. Briefly describe how each approach differs in its learning mechanism, data usage, and real-world applications.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1427 (ET: E-Zone)]*

2. **Explain reinforcement learning in the field of Machine Learning?** *[BTCL Assistant Manager (Technical) 2023 compact it 593 (ET: BUET)]*

3. **Weak and strong learner ensemble learning in Machine learning.** *[GTCL Assistant Engineer (CSE) 2022 compact it 686 (ET: BUET)]*

## Search Algorithms (Informed vs Uninformed Search) (2)

1. **Write down the difference between informed and uninformed search algorithm.** *[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

2. **How $\alpha$-$\beta$ pruning is better than minimax search in game planning?** *[ICT Ministry Assistant Programmer 2017 compact it 1243 (ET: N/A)]*

## Overfitting, Underfitting & Model Generalization (1)

1. **In machine learning. What will happen, when a machine is highly trained up a slight trained up?** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 395 (ET: BUET)]*

## Association Rule Learning (Market Basket Analysis) (1)

1. **Which Machine Learning Algorithm is suitable for the case of Market - Basket Analysis? Explain the steps involved.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1364 (ET: BUET)]*

## Clustering & Unsupervised Learning (K-Means, Hierarchical) (1)

1. **Consider the five points: P1 (0.07, 0.83), P2 (0.85, 0.14), P3 (0.66, 0.89), P4 (0.49, 0.64), and P5 (0.80, 0.46). Group first two points considering single-linkage hierarchical clustering technique.** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 473 (ET: N/A)]*
