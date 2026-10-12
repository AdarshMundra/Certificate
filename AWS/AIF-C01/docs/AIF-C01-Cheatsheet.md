# AWS AIF-C01 Cheatsheet (Quick Revision)

## Exam at a Glance

| Detail | Info |
|--------|------|
| Duration | 85 minutes |
| Questions | 65 scored + 15 unscored |
| Passing | 700/1000 |
| Format | Multiple choice & multiple response |

| Domain | Weight |
|--------|--------|
| 1. AI & ML Fundamentals | ~20% |
| 2. Generative AI Fundamentals | ~24% |
| 3. Applications of Foundation Models | ~28% |
| 4. Responsible AI | ~14% |
| 5. Security, Compliance & Governance | ~14% |

---

## Domain 1: AI & ML Fundamentals (20%)

### AI Hierarchy
```
Artificial Intelligence > Machine Learning > Deep Learning > Generative AI
```

### ML Types

| Type | Data | Examples |
|------|------|----------|
| **Supervised** | Labeled | Classification (spam/not spam), Regression (house prices) |
| **Unsupervised** | Unlabeled | Clustering (K-Means), Anomaly Detection (Isolation Forest), Association Rules (Apriori) |
| **Semi-supervised** | Mix labeled + unlabeled | Pseudo-labeling |
| **Self-supervised** | Unlabeled (creates own labels) | Pretext tasks → downstream tasks |
| **Reinforcement** | Rewards/penalties | Gaming, robotics, autonomous vehicles |

### Neural Network Types

| Network | Use Case |
|---------|----------|
| **CNN** | Images |
| **RNN** | Sequential data, video, time series |
| **GAN** | Synthetic data generation |
| **Transformer** | LLMs (BERT, GPT) |
| **Diffusion** | Image generation (noise removal) |
| **VAE** | Latent space representations |

### ML Process
```
Data Collection → Preprocessing → Feature Engineering → Training → Evaluation → Deployment → Monitoring
```

### Data Splits

| Set | Purpose |
|-----|---------|
| **Training** (~70%) | Train the model |
| **Validation** (~15%) | Tune hyperparameters |
| **Test** (~15%) | Final evaluation (unseen data) |

### Feature Engineering
- **Feature Extraction** — pull useful info from raw data (e.g., edges from images)
- **Feature Selection** — pick the most relevant features, drop irrelevant ones
- **Feature Transformation** — normalize, scale, encode data

### Model Fit

| Problem | Cause | Fix |
|---------|-------|-----|
| **Overfitting** | High variance, too complex | Simplify model, more data, feature selection, regularization |
| **Underfitting** | High bias, too simple | More complex model, more features, more training |
| **Balanced** | Low bias + low variance | Target state |

### Classification Metrics

| Metric | Formula | Best When |
|--------|---------|-----------|
| **Precision** | TP / (TP + FP) | False positives are costly |
| **Recall** | TP / (TP + FN) | False negatives are costly |
| **F1 Score** | 2 * (P * R) / (P + R) | Balance between P and R, imbalanced datasets |
| **Accuracy** | (TP + TN) / Total | Balanced datasets only |
| **AUC-ROC** | 0 to 1 (1 = perfect) | Comparing models at different thresholds |

### Regression Metrics

| Metric | Measures |
|--------|----------|
| **MAE** | Average absolute error |
| **MAPE** | Average absolute percentage error |
| **RMSE** | Root mean squared error (penalizes large errors) |
| **R-squared** | Variance explained (closer to 1 = better) |

### Inference Types
- **Real-time** — immediate response (chatbots), speed > accuracy
- **Batch** — large datasets processed at once, accuracy > speed
- **Edge** — SLM on device, low latency, offline capability

### When ML is NOT Appropriate
- Deterministic problems (fixed rules, no patterns to learn)
- Not enough data
- Problem can be solved with simple if/else logic

---

## Domain 2: Generative AI Fundamentals (24%)

### Foundation Models (FMs)
- Trained on massive diverse data, cost millions to train
- Can be open-source (Meta Llama, Google BERT) or commercial (OpenAI, Anthropic)
- LLMs are a **subset** of FMs — focused on text
- LLMs are **non-deterministic** (same prompt → different outputs)
- LLMs are **generative** (create new content), not discriminative (classify)

### Key GenAI Concepts

| Concept | Definition |
|---------|------------|
| **Tokenization** | Breaking text into tokens (words/subwords) |
| **Context Window** | Max input size the model can process |
| **Embeddings** | Vector representations capturing semantic meaning |
| **Multi-modal** | Models that handle text + images + audio |

### Inference Parameters

| Parameter | What It Controls |
|-----------|-----------------|
| **Temperature** | Creativity (0 = deterministic, 1 = creative/random) |
| **Top K** | Number of most-likely next-token candidates |
| **Top P** | Cumulative probability threshold for candidates |
| **Stop Sequences** | Characters/tokens that stop generation |
| **Response Length** | Min/max tokens in output |

### Prompt Engineering Techniques

| Technique | Description | Changes Weights? |
|-----------|-------------|:---:|
| **Zero-shot** | No examples, just instruction | No |
| **Few-shot** | A few examples provided | No |
| **Chain-of-thought** | Step-by-step reasoning | No |
| **Negative prompting** | Specifying what to avoid | No |
| **System prompts** | Set model behavior/persona | No |

### Prompt Security
- **Prompt Injection** — embeds malicious instructions in prompts
- **Prompt Hijacking** — diverts model to unintended behavior
- **Prompt Leaking** — extracts system prompt
- **Jailbreaking** — bypasses safety restrictions
- **Prompt Poisoning** — corrupts training data via prompts
- **Protection** — input validation, guardrails, template design

### Model Customization (Cost Order: Low → High)

```
Prompt Engineering → RAG → Instruction Fine-tuning → Domain Adaptation (Continued Pre-training)
```

| Method | Changes Weights? | Data Needed | Best For |
|--------|:---:|------|----------|
| **Prompt Engineering** | No | None | Quick iteration, general tasks |
| **RAG** | No | External knowledge base | Dynamic/changing data, citations |
| **Fine-tuning** | Yes | Labeled data | Domain-specific expertise |
| **Continued Pre-training** | Yes | Unlabeled data | Deep domain adaptation |
| **Distillation** | Yes (student) | Teacher model outputs | Smaller, cheaper models |

### Model Evaluation

**Automatic Metrics (Quantitative):**

| Metric | Measures |
|--------|----------|
| **ROUGE** | Overlap between generated and reference text (summarization) |
| **BLEU** | Precision of generated vs reference (translation) |
| **BERTScore** | Semantic similarity using embeddings |
| **Perplexity** | How well model predicts next token (lower = better) |

**Human Evaluation (Qualitative):** Coherence, relevance, fluency, helpfulness

**Business Metrics:** User satisfaction, ARPU, conversion rate, efficiency

---

## Domain 3: Applications of Foundation Models (28%)

### Amazon Bedrock

| Feature | Purpose |
|---------|---------|
| **Base FMs** | Claude, Llama, Titan, Stable Diffusion, Mistral, Cohere, AI21 |
| **Knowledge Bases** | RAG implementation (vector search) |
| **Agents** | Orchestrate multi-step tasks with action groups |
| **Guardrails** | Filter content, redact PII, block topics |
| **Fine-tuning** | Supervised or Reinforcement fine-tuning |
| **Model Evaluation** | Automatic + human evaluation |
| **CloudWatch** | Invocation logging, metrics |

**Bedrock Data Privacy:** Your data is NOT used to improve base FMs, NOT shared with providers

**Bedrock Pricing:**

| Type | Use Case |
|------|----------|
| **On-Demand** | Pay per token, no commitment |
| **Batch** | 50% cheaper, async processing |
| **Provisioned Throughput** | Reserved capacity, predictable workloads |

**RAG Vector Databases:** OpenSearch, Aurora, Neptune Analytics, S3 Vectors

**RAG Data Sources:** S3, Confluence, SharePoint, Salesforce, Web pages

### Amazon Nova Models

| Model | Type |
|-------|------|
| **Nova Premier** | Most capable, complex tasks |
| **Nova Pro** | Balanced performance/cost |
| **Nova Lite** | Fast, low-cost text/image/video |
| **Nova Micro** | Text-only, lowest latency |
| **Nova Canvas** | Image generation |
| **Nova Reel** | Video generation |
| **Nova Sonic** | Speech-to-speech |

### SageMaker Services (KNOW ALL OF THESE)

| Service | One-Line Purpose |
|---------|-----------------|
| **SageMaker** | Full ML platform — build, train, deploy |
| **Studio** | IDE (JupyterLab, Code Editor, RStudio) |
| **Canvas** | No-code ML model building |
| **Data Wrangler** | Data prep, 300+ transforms, balance datasets |
| **Clarify** | Bias detection + model explainability |
| **Ground Truth** | Human-in-the-loop data labeling |
| **Feature Store** | Centralized feature repository (share/reuse) |
| **JumpStart** | Pre-built solutions, FM hub, one-click deploy |
| **Model Cards** | Document intended use, risk, metrics |
| **Model Dashboard** | Aggregates Cards + Monitor + Endpoints |
| **Model Monitor** | Production model quality tracking |
| **Model Registry** | Version and manage trained models |
| **Role Manager** | IAM role management for ML teams |
| **Pipelines** | CI/CD for ML workflows |
| **Automatic Model Tuning** | Hyperparameter optimization |

**SageMaker Deployment Types:**

| Type | Best For |
|------|----------|
| **Real-time** | Low-latency, persistent endpoints |
| **Serverless** | Intermittent, tolerates cold starts, scales to zero |
| **Asynchronous** | Large payloads (up to 1GB), long processing |
| **Batch Transform** | Entire datasets at once |

### Amazon Q / Quick Family

| Service | Purpose |
|---------|---------|
| **Amazon Quick** | Enterprise AI assistant (successor to Q Business) |
| **Q Developer** | Code suggestions, security scanning, IDE + Console + CLI |
| **Q for QuickSight** | Natural language BI dashboards |
| **Q for EC2** | Instance selection assistance |
| **Q for Glue** | Data integration assistance |
| **Q for Chatbot** | Slack/Teams integration |
| **PartyRock** | GenAI app-building playground |

### AWS Managed AI Services

| Service | What It Does |
|---------|-------------|
| **Comprehend** | NLP — sentiment, entities, PII, custom classification |
| **Comprehend Medical** | Clinical text, PHI detection, HIPAA eligible |
| **Translate** | Text translation |
| **Transcribe** | Speech-to-text (+ Medical variant) |
| **Polly** | Text-to-speech (Lexicons, SSML) |
| **Rekognition** | Image/video — objects, faces, text, content moderation |
| **Lex** | Chatbots (intents + slots) |
| **Textract** | OCR — extract text, tables, forms from documents |
| **Kendra** | Enterprise document search |
| **Personalize** | Recommendation engine |
| **A2I** | Human review of ML predictions |
| **Mechanical Turk** | Crowdsourced human tasks |
| **HealthScribe** | Clinical note generation |

### AWS AI Hardware

| Chip | Purpose |
|------|---------|
| **AWS Trainium** | ML training (25% more energy efficient) |
| **AWS Inferentia** | ML inference (cost effective) |
| **EC2 GPU instances** | General AI/ML compute |

---

## Domain 4: Responsible AI (14%)

### 8 Core Dimensions
1. **Fairness** — prevent discrimination
2. **Explainability** — understand why decisions are made
3. **Privacy & Security** — users control their data
4. **Transparency** — open about how AI works
5. **Veracity & Robustness** — reliable in unexpected situations
6. **Governance** — define and enforce responsible AI practices
7. **Safety** — beneficial for individuals and society
8. **Controllability** — align AI to human values

### Interpretability vs Performance Trade-off
```
High Interpretability / Poor Performance:  Linear Regression → Decision Tree → Logistic Regression
Poor Interpretability / High Performance:  SVM → Ensemble Methods → Neural Networks
```

- **Interpretability** = understand WHY and HOW (white box)
- **Explainability** = understand inputs/outputs WITHOUT knowing internals (black box)
- **Partial Dependence Plots (PDP)** — show how one feature affects predictions
- **Decision Trees** — high interpretability, clear visual, prone to overfitting

### Bias Types
- **Sampling/Selection bias** — non-representative training data
- **Measurement bias** — faulty data collection
- **Observer bias** — subjective interpretation
- **Confirmation bias** — seeking data that confirms beliefs
- **Algorithmic bias** — model amplifies data bias

### GenAI Risks
- **Hallucination** — plausible but factually incorrect output
- **Toxicity** — harmful, offensive content
- **Plagiarism** — reproducing copyrighted content

### AWS Responsible AI Tools
- **Bedrock Guardrails** — filter content, redact PII, block topics
- **SageMaker Clarify** — bias detection + model explainability
- **SageMaker Data Wrangler** — fix bias by balancing datasets
- **SageMaker Model Monitor** — production quality analysis
- **A2I** — human review of ML predictions
- **AWS AI Service Cards** — transparency docs for AWS AI services
- **RLHF** — train models using human feedback

---

## Domain 5: Security, Compliance & Governance (14%)

### AWS Shared Responsibility Model
- **AWS** — security OF the cloud (infrastructure, hardware, network)
- **Customer** — security IN the cloud (data, access, encryption, IAM)

### GenAI Security Scoping Matrix (5 Scopes)
```
Using pre-built AI service → Least security responsibility
Fine-tuning a model → More responsibility
Training your own model → Even more responsibility
Building from scratch → Maximum security ownership
```

### Key Security Services

| Service | Purpose |
|---------|---------|
| **IAM** | Users, groups, roles, policies — access control |
| **CloudTrail** | API call audit history |
| **AWS Config** | Continuous resource configuration monitoring |
| **Amazon Inspector** | Security vulnerability assessments |
| **AWS Artifact** | Compliance reports (SOC, ISO, HIPAA, etc.) |
| **AWS Audit Manager** | Automated audit evidence collection |
| **Trusted Advisor** | Account-level best practice checks |
| **AWS Macie** | PII detection in S3 |
| **KMS** | Encryption key management |
| **VPC / PrivateLink** | Network isolation for ML models |

### Compliance Frameworks
NIST, ENISA, ISO, SOC, HIPAA, GDPR, PCI DSS

### Governance Tools & Strategies
- **SageMaker Role Manager** — IAM roles per ML team
- **SageMaker Model Cards** — document model use, risk, metrics
- **SageMaker Model Dashboard** — centralized model tracking
- **Data Lineage** — track data origins, transformations, flow
- **Data Governance** — lifecycle, logging, residency, retention, monitoring

### MLOps
- Version control for models and data
- Automation of ML pipelines
- CI/CD with SageMaker Pipelines
- Continuous retraining and monitoring

### Bedrock Security
- Data encrypted in transit and at rest
- PrivateLink for VPC access
- IAM roles for team-level access control
- CloudTrail for access auditing
- KMS for encrypted S3 access

---

## Commonly Confused Services (Quick Diff)

| Pair | Difference |
|------|------------|
| **Comprehend vs Comprehend Medical** | General NLP vs clinical text (HIPAA) |
| **Textract vs Rekognition** | Document OCR vs image/video analysis |
| **Transcribe vs Transcribe Medical** | General speech-to-text vs medical (HIPAA) |
| **Ground Truth vs A2I** | Data labeling vs reviewing ML predictions |
| **Clarify vs Model Monitor** | Pre-deployment bias/explain vs post-deployment quality |
| **Model Cards vs Model Dashboard** | Document one model vs track all models |
| **Trainium vs Inferentia** | Training chip vs inference chip |
| **Fine-tuning vs RAG** | Changes weights (domain expertise) vs doesn't (dynamic data) |
| **Kendra vs OpenSearch** | Enterprise doc search vs vector DB for RAG |
| **Bedrock vs SageMaker** | Managed GenAI service vs full ML platform |
| **Canvas vs JumpStart** | No-code ML building vs pre-built solutions hub |
| **Precision vs Recall** | Of predicted positives, how many correct vs of actual positives, how many found |

---

## One-Liner Memory Hooks

- **Temperature** = thermostat of creativity
- **RAG** = open-book exam (look up answers)
- **Fine-tuning** = studying for weeks (knowledge becomes permanent)
- **Prompt Engineering** = asking the right question
- **Overfitting** = memorized the textbook, fails the real exam
- **Underfitting** = didn't study enough, fails everything
- **Guardrails** = bouncer at the door
- **RLHF** = learning from human grading
- **Embeddings** = GPS coordinates for words (similar meaning = nearby)
- **Tokenization** = chopping text into puzzle pieces
- **Context Window** = how much text the model can read at once
