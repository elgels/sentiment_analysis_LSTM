<h1>LSTM with Attention — Sentiment Analysis (SST)</h1>

<h2>Project Overview</h2>

<p>
This project applies deep learning techniques to a <strong>sentiment analysis</strong> task using the Stanford Sentiment Treebank (SST) dataset. The goal is to classify sentences into sentiment categories (positive, negative, and neutral).
</p>

<p>
The model builds on a standard recurrent neural network (RNN) architecture by incorporating 
<strong>pretrained GloVe embeddings, convolutional feature extraction, a bidirectional LSTM, and an attention mechanism</strong> 
to improve performance and capture both local patterns and long-range dependencies in text.
</p>

<hr>

<h2>Dataset</h2>

<ul>
  <li>Stanford Sentiment Treebank (SST)</li>
  <li>Text data consisting of sentences labeled by sentiment</li>
  <li>Classes: positive, negative, neutral</li>
</ul>

<p>
The text is tokenized, lowercased, and converted into numerical sequences using a vocabulary built from the training data.
</p>

<hr>

<h2>Model Architecture</h2>

<p align="center">
  Input Sequence  
  <br>↓<br>
  GloVe Embedding Layer (300-dim)  
  <br>↓<br>
  CNN Layers (kernel sizes 2, 3, 4)  
  <br>↓<br>
  ReLU → Dropout → Concatenation  
  <br>↓<br>
  Bidirectional LSTM (2 layers)  
  <br>↓<br>
  Layer Normalization  
  <br>↓<br>
  Attention Mechanism  
  <br>↓<br>
  Dropout  
  <br>↓<br>
  Fully Connected Layer  
  <br>↓<br>
  Output (sentiment logits)
</p>

<hr>

<h2>Key Components</h2>

<h3>GloVe Pretrained Embeddings</h3>
<p>
Pretrained word embeddings (300-dimensional) from GloVe were used to initialize word representations. 
These embeddings capture semantic relationships between words and improve performance on smaller datasets.
</p>

<h3>Convolutional Layers</h3>
<p>
Convolutional layers with kernel sizes 2, 3, and 4 extract local patterns such as bigrams and trigrams, 
helping the model identify meaningful phrases (e.g., "not good", "very interesting").
</p>

<h3>Bidirectional LSTM</h3>
<p>
A two-layer bidirectional LSTM captures contextual dependencies from both past and future tokens, 
improving understanding of sentence structure and ambiguity.
</p>

<h3>Attention Mechanism</h3>
<p>
An attention layer assigns importance weights to tokens, allowing the model to focus on the most relevant words 
when forming predictions.
</p>

<ul>
  <li>Computes attention scores from LSTM outputs</li>
  <li>Masks padding and unknown tokens</li>
  <li>Generates a context vector via weighted averaging</li>
</ul>

<p>
This improves interpretability and helps the model capture nuanced sentiment.
</p>

<h3>Regularization and Optimization</h3>
<ul>
  <li>Dropout applied in multiple layers</li>
  <li>Layer normalization for stable training</li>
  <li>Weighted cross-entropy to handle class imbalance</li>
  <li>Learning rate scheduling for improved convergence</li>
</ul>

<hr>

<h2>Results</h2>

<p>
The final model achieved a validation accuracy of <strong>65.38%</strong>.
</p>

<p>
Training and validation curves show improved stability due to normalization and regularization techniques.
</p>

<h3>Confusion Matrix Insights</h3>

<p>
Neutral sentences were the most frequently misclassified.
</p>

<ul>
  <li>Neutral sentiment often overlaps with both positive and negative expressions</li>
  <li>Subtle phrasing and ambiguity increase classification difficulty</li>
  <li>This highlights the limitations of recurrent models in capturing nuanced sentiment</li>
</ul>



<h3>Attention Behavior</h3>

<p>
Attention visualizations show that the model often focuses on a small number of tokens when making predictions.
</p>

<ul>
  <li>Important keywords are often correctly identified</li>
  <li>However, the model may over-rely on individual words rather than combining full sentence context</li>
</ul>

<p>
This behavior can lead to errors when sentiment depends on interactions between words rather than isolated terms.
</p>

<hr>
<h2>Future Improvements</h2>

<ul>
  <li>Transition to transformer-based architectures (e.g., BERT)</li>
  <li>Improve handling of neutral and ambiguous sentiment</li>
  <li>Expand dataset or apply data augmentation techniques</li>
</ul>

<hr>

<h2>Technologies Used</h2>

<p>
Python • PyTorch • torchtext • GloVe • NumPy • Matplotlib • Seaborn • Jupyter Notebook
</p>

<hr>

<h2>Repository Structure</h2>

<pre>
├── lstm_attention_model.ipynb
├── figures/
│   ├── loss_plot.png
│   ├── accuracy_plot.png
│   ├── confusion_matrix.png
│   └── attention_heatmap.png
└── README.md
</pre>

<hr>

<h2>Key Takeaways</h2>

<ul>
  <li>Pretrained embeddings significantly improve performance on small NLP datasets</li>
  <li>Combining CNN, LSTM, and attention enhances feature extraction and sequence modeling</li>
  <li>Neutral sentiment remains the most challenging class</li>
  <li>Attention provides useful interpretability but does not fully resolve ambiguity</li>
</ul>

<hr>

<h2>License</h2>

<p>
This project is licensed under the MIT License.
</p>
