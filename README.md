<div align="center">
  <h1>Medical Diabetes RAG Agent</h1>
  <p><strong>A production-ready, clinical Retrieval-Augmented Generation (RAG) agent for diabetes management queries.</strong></p>

  <p>
    <a href="#tech-stack"><b>Tech Stack</b></a> •
    <a href="#key-features"><b>Key Features</b></a> •
    <a href="#setup--installation"><b>Setup</b></a> •
    <a href="#future-roadmap"><b>Roadmap</b></a>
  </p>
</div>

<hr />

<h2>Overview</h2>
<p>
  This project features an automated medical AI agent engineered to deliver accurate, guideline-grounded diabetes information. By pairing <strong>n8n</strong> workflow orchestration with <strong>Qdrant</strong> vector search, <strong>Hugging Face</strong> embeddings, and <strong>Groq API</strong> inference, the system ensures fast, factual, and medically aligned responses delivered seamlessly via <strong>Telegram API</strong>.
</p>

<h2>Architecture & Data Flow</h2>
<pre><code>[ User (Telegram Interface) ]
              │
              ▼ (Webhook Execution)
       [ n8n Workflow ] ◄────────► [ Google Drive ] (Clinical Guides / Data Source)
              │                                 │
              ▼                                 ▼
      [ Groq LLM API ] ◄───► [ Hugging Face Embeddings ] ───► [ Qdrant Vector DB ]
</code></pre>

<h2 id="key-features">Key Features</h2>
<ul>
  <li><strong>Grounded Clinical Context:</strong> Utilizes vector retrieval from medical guidelines to prevent model hallucinations and maintain factual safety.</li>
  <li><strong>High-Performance Inference:</strong> Leverages Groq API for rapid LLM response generation with low latency.</li>
  <li><strong>Reliable Automation Engine:</strong> Built on n8n with active error handling, automatic retries, and rate-limit mitigation (429 handling).</li>
  <li><strong>Production Deployment:</strong> Fully containerized via Docker and securely routed using Ngrok tunnels to handle Telegram Webhook events.</li>
  <li><strong>Automated Data Pipeline:</strong> Syncs clinical documentation directly from Google Drive into the vector indexing workflow.</li>
</ul>

<h2 id="tech-stack">Tech Stack</h2>
<table>
  <tr>
    <th>Component</th>
    <th>Technology</th>
  </tr>
  <tr>
    <td><strong>Orchestration & Workflow</strong></td>
    <td>n8n</td>
  </tr>
  <tr>
    <td><strong>LLM Inference Engine</strong></td>
    <td>Groq API</td>
  </tr>
  <tr>
    <td><strong>Vector Database</strong></td>
    <td>Qdrant</td>
  </tr>
  <tr>
    <td><strong>Embeddings Engine</strong></td>
    <td>Hugging Face Inference APIs</td>
  </tr>
  <tr>
    <td><strong>Data Storage & Sync</strong></td>
    <td>Google Drive</td>
  </tr>
  <tr>
    <td><strong>User Interface</strong></td>
    <td>Telegram Bot API</td>
  </tr>
  <tr>
    <td><strong>Deployment & Tunneling</strong></td>
    <td>Docker, Ngrok</td>
  </tr>
</table>

<h2>Project Structure</h2>
<pre><code>.
├── RAG-chatbot.json    # Exported n8n workflow configuration
├── RAG-chatbot.png     # Visual architecture & node configuration
└── README.md           # Project documentation
</code></pre>

<h2 id="setup--installation">Setup & Local Installation</h2>

<h3>Prerequisites</h3>
<ul>
  <li><strong>Docker</strong> engine installed and active.</li>
  <li><strong>Telegram Bot Token</strong> generated via <code>@BotFather</code>.</li>
  <li>Valid API keys for <strong>Groq API</strong>, <strong>Hugging Face</strong>, and <strong>Qdrant</strong>.</li>
</ul>

<h3>Installation Steps</h3>
<ol>
  <li>
    <strong>Clone the Repository:</strong>
    <pre><code>git clone https://github.com/Mohamedawad114/medical-diabetes-rag-agent.git
cd medical-diabetes-rag-agent</code></pre>
  </li>
  <li>
    <strong>Import Workflow into n8n:</strong>
    <ul>
      <li>Open your n8n dashboard.</li>
      <li>Navigate to <strong>Workflows</strong> &gt; <strong>Import from File</strong>.</li>
      <li>Select the <code>RAG-chatbot.json</code> file.</li>
    </ul>
  </li>
  <li>
    <strong>Set Up API Credentials:</strong>
    <ul>
      <li>Configure Telegram Bot API token.</li>
      <li>Set up Groq API key and Hugging Face embedding endpoints.</li>
      <li>Provide host URL and authentication for Qdrant.</li>
    </ul>
  </li>
  <li>
    <strong>Expose Local Webhook:</strong>
    <pre><code>ngrok http 5678</code></pre>
  </li>
  <li>
    <strong>Activate Workflow:</strong>
    <p>Toggle the n8n workflow switch to <strong>Active</strong> to begin processing incoming messages.</p>
  </li>
</ol>

<h2>Error Handling & Reliability</h2>
<ul>
  <li><strong>Plain Text Formatting:</strong> Stripped unstable Markdown styling to guarantee 100% delivery success over Telegram API.</li>
  <li><strong>Retry Logic:</strong> Configured retry delays on LLM and embedding nodes to gracefully manage API rate limits.</li>
  <li><strong>Extended Timeouts:</strong> Configured workflow timeout parameters to accommodate complex vector queries.</li>
</ul>

<h2 id="future-roadmap">Future Roadmap</h2>
<ul>
  <li>Expand the vector dataset to encompass broader endocrinology and clinical dietetics guidelines.</li>
  <li>Introduce conversational session memory within Qdrant and n8n.</li>
  <li>Fine-tune system prompts for enhanced medical context precision and structured output delivery.</li>
</ul>

<h2>Medical Disclaimer</h2>
<blockquote style="border-left: 4px solid #f39c12; padding-left: 10px; color: #555;">
  <p><em>This system is built for informational and educational purposes only and should not be used as a substitute for professional clinical advice, diagnosis, or treatment.</em></p>
</blockquote>

<h2>License</h2>
<p>This project is open-source under the <a href="LICENSE">MIT License</a>.</p>
