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

2. **What does the axon of neural network do?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

3. **Write difference between machine learning and deep learning.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 681 (ET: N/A)]*

4. **What is Deep learning?** *[BARC Data Entry Officer 10.09.2022 compact it 703 (ET: N/A)]*

5. **What is Artificial Neural Network (ANN)? Difference between deep learning technique and Traditional machine learning technique.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 856 (ET: N/A)]*

6. **Write LSTM gates name in AI.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 858 (ET: N/A)]*

7. **Draw the single layer of ANN.** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 880 (ET: BUET)]*

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

## Search Algorithms (Informed vs Uninformed Search) (1)

1. **Write down the difference between informed and uninformed search algorithm.** *[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

## Overfitting, Underfitting & Model Generalization (1)

1. **In machine learning. What will happen, when a machine is highly trained up a slight trained up?** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 395 (ET: BUET)]*

## Association Rule Learning (Market Basket Analysis) (1)

1. **Which Machine Learning Algorithm is suitable for the case of Market - Basket Analysis? Explain the steps involved.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1364 (ET: BUET)]*

## Clustering & Unsupervised Learning (K-Means, Hierarchical) (1)

1. **Consider the five points: P1 (0.07, 0.83), P2 (0.85, 0.14), P3 (0.66, 0.89), P4 (0.49, 0.64), and P5 (0.80, 0.46). Group first two points considering single-linkage hierarchical clustering technique.** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 473 (ET: N/A)]*
