# Architecture Diagram

## Pipeline Flow

```mermaid
graph LR
  Input["📝 Input<br/>Text + Image"] --> Classify["1️⃣ Classify<br/>Disaster Type<br/>& Severity"]
  Classify --> Location["2️⃣ Location<br/>Extract Places<br/>spaCy NER"]
  Location --> RAG["3️⃣ RAG<br/>Find Similar<br/>Events"]
  RAG --> Router["4️⃣ Router<br/>Need VLM?"]
  Router -->|Image + High Severity| VLM["5️⃣ VLM<br/>Damage<br/>Assessment"]
  Router -->|No Image| Report["6️⃣ Report<br/>Synthesize<br/>All Signals"]
  VLM --> Report
  Report --> Output["📊 Output<br/>Structured JSON<br/>& Summary"]