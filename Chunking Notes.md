**Chunking in RAG Systems**


Chunking -> Breaking longer text documents from the knowledge base into smaller, more manageable text chunks. This process allow llms to efficiently process and retrieve relevant information by staying within their token or context window limits.




**Why Chunking?**




Many embedding models have limits for the amount of text they can embed into vectors.

It improves search relevancy metrics for your retrievers and ensures better matching during query time.

Makes sure only the most relevant text is sent to the LLM instead of entire documents, which enhances both speed and accuracy.

Helps in maintaining context when dealing with large knowledge bases by breaking down documents intelligently.





**Advantages**





Fast retrieval: Smaller chunks make searching and indexing much quicker.

Efficient processing: Model context window limit is not filled unnecessarily with irrelevant data.

Better accuracy: Increases precision during retrieval by focusing on smaller, more meaningful text portions.


**Fixed-Size Chunking**



Fixed-size chunking means breaking a long text into smaller pieces (chunks) of equal size — usually based on a set number of characters, words, or tokens without caring about sentence meaning or topic.
It’s the simplest type of chunking used in RAG.


Example


Lets say, Wheat is one of the most important crops in Pakistan. It is grown in many regions and requires moderate rainfall.

If we apply fixed-size chunking with a chunk size of 10 words, it would split like this:

Chunk 1: “Wheat is one of the most important crops in”

Chunk 2: “Pakistan. It is grown in many regions and requires”

Chunk 3: “moderate rainfall.”





<img width="742" height="462" alt="image" src="https://github.com/user-attachments/assets/da1ebeed-5e90-47ff-9d36-f9dc7ca2b05f" />





**Normal Chunking vs Overlapping Chunking**






Normal Chunking: The text document is divided equally into fixed-size parts (e.g., every 500 tokens).

Problem: It may lose context or logical connections between chunks, especially when important information spans across boundaries.

Overlapping Chunking: Some parts of one chunk are repeated in the next chunk.

Benefit: Helps preserve continuity and context between neighboring chunks, improving retrieval consistency and semantic understanding.







<img width="692" height="381" alt="image" src="https://github.com/user-attachments/assets/431418fe-1271-499c-8e1e-8ae2a732c515" />








**Recursive Character Splitting**




This method splits text recursively at natural boundaries such as paragraphs, sentences, or punctuation marks.
It tries to find the largest possible chunks under a certain token limit, ensuring that each chunk remains semantically coherent.
It’s often used as a preprocessing step before embedding or retrieval in RAG pipelines.


**Advanced Chunking Techniques




Semantic Chunking**




Groups sentences together based on semantic similarity rather than arbitrary character or token limits. The algorithm works by analyzing sentence embeddings and merging sentences that share similar meanings.
A semantic chunker understands topic shifts using embeddings, allowing it to form contextually aware chunks.

**Advantages:**

Smart chunk boundaries that align with topic changes.

Higher recall and precision in retrieval results.

Reduces redundancy and improves the relevance of answers.

**Disadvantages:**

Computationally more expensive than simple character-based chunking.

Requires embedding models or similarity algorithms to work effectively.
