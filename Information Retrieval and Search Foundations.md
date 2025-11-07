**Why use RAG
**



<img width="907" height="467" alt="image" src="https://github.com/user-attachments/assets/fd401dce-700a-4e61-9673-a284c9d313d4" />



**What is RAG?**


The key idea of the RAG system is you can modify the prompt before sending it to the llm (Augmented prompt). 






**Lecture Retriever Introduction**


A retriever helps llm to find documents in knowledge base (outside its training data) to provide best possible results. In this module we will learn different primary techniques reteriever use to accomplish its taks.


<img width="967" height="320" alt="image" src="https://github.com/user-attachments/assets/2a446a2f-dcad-4b10-9197-942309d4c084" />



**Overview of Reteriever Architecture**

Overall RAG Architecture

Whenever we give prompt to RAG based llm. Prompt is send to the reteriever, then reteriever has the access to the knowledge base (bunch of text files sitting in the database. A reteriever needs to quickly decide
which documents are most relevant to the prompt and turn them to pass to the llm.


<img width="847" height="457" alt="image" src="https://github.com/user-attachments/assets/ec3663c0-c05e-440f-bf10-b13b01686251" />


**Flow of RAG
**




The very first component that receives the user's input query (prompt) is the Retriever.The LLM (Generator) only comes into play after the Retriever has finished its job.The Retriever takes the query, finds the relevant context, and combines the two. Only then is this augmented prompt given to the LLM to generate the final answer.





Flow: User Query -->  Retriever -->  Augmented Prompt --> LLM (Generator) --> Answer







Here is the complete, high-level process, segmented into the preparation and real-time stages:






<img width="913" height="402" alt="image" src="https://github.com/user-attachments/assets/5518c525-0899-4c8d-b9fc-809d5483371a" />







<img width="892" height="593" alt="image" src="https://github.com/user-attachments/assets/381c12fb-e7c3-47fa-bd7b-dc5b6bbe9a6e" />












Most reterivers use two search techniques as part of this process. 


1---> Keyword Search 


It is more traditional search technique in which reteriever looks for the documents that contains the exact words found in the prompt. This approach is time tested and has powered informations for decades.



2---> Sementic Search



In this technique reteriever looks for the documents that has the same meaning to the prompt. This approach makes reteriever more flexible by finding relevant documents but might not contain the exact words used in the prompt




**Hybrid Search**



It uses multiple techniques to produce final documents in the ranking. In RAG we have documents collected by the Semantic search and keyword search after applying metadata filters we finally collected final relevant documents. This type of searching is called hybrid search.




<img width="1021" height="463" alt="image" src="https://github.com/user-attachments/assets/ae6d1e46-aa7b-4cd5-91a5-440f5c6a2e30" />








**MetaData Filtering**

Metadata means data about the data. After a search (keyword or semantic), you might get 20–50 documents that match somehow, but not all are useful.
You can narrow them down by applying metadata filters.

It removes irrelevant results  Keep only the most context-appropriate documents and Save time and improve accuracy.

Paid and non-paid articles is the example. If we want unpaid articles of our favorite author we implement metadata filter to drop all paid articles and allow only unpaid to pass to the llm.



<img width="972" height="451" alt="image" src="https://github.com/user-attachments/assets/4a16c528-f377-4da0-87a9-a8f10f8b9bd5" />




Keyword Search 

This technique is used in browsers and database engines for decades. This technique retrieve documents based on wether they share words in common with the prompt. The idea is to collect all the documents that has more words in common with the prompt.
because they are more likely to be relevant. 




How it Works




Both documents and prompt treated as bag of words which means order of words does not matter instead all what it matters is how often a word appears in the prompt. 
<img width="1041" height="523" alt="image" src="https://github.com/user-attachments/assets/43cf0fc7-a422-4ca6-b0f6-68973911dca3" />



These words are stored in vectors. Each vector has specific spot in the system's vocabulary. Then they are treated as grid where each document is a column and each word is row





**TF-IDF (Term Frequency – Inverse Document Frequency) VS BM25
**



Both these techniques are used to find the most relevant document by giving scores to each document using how often a word appears yet they have differences in their working.




TF-IDF


TF (Term Frequency)---> Counts how many times a word appears in a document. e.g, if apple appears 5 times in a document of 100 words then TF = 5/100 = 0.05

IDF (Inverse Document Frequency)--> Checks how common the word is across all documents.e.g, if “apple” appears in 1000 documents out of 10,000 then IDF = log(10,000 / 1000) = 1

TF-IDF finds documents based on how often a keyword appears in them.




Limitation




TF IDF gives more weight to a document based on existance of more keyword which leads to incorrect results like if “wheat” appeared 40 times, the score becomes 40 × 1.3 = 52,
that’s too much. TF-IDF doesn’t know when to stop giving extra weight.




BM25

BM25 is an improved version of TF-IDF used in modern search engines. After 4 or 5 times, you stop caring about repetition and focus on overall relevance. It still uses the TF and IDF idea, but adds two smart features,




1--> (Capping Word Frequency) means it knows that after a certain point, repeating the same word doesn’t make the document more relevant. So instead of increasing, BM25 flattens the score like if
“wheat” appearing 5 times or 10 times gives almost the same boost.





2--> (Document Length Normalization) means Longer documents naturally have more words, so BM25 adjusts for that like 






Sementic Search

On higher level it initially works the same as keyword search but difference comes in storing vectors. For storing vectors semantic search uses a special methamatical model called embedding. Starting point is shared in both type of search techniques like both systems start by converting text into vectors butt he difference lies in How they store vectors. It uses dense vectors. These are generated by a mathematical model called an embedding model. This model converts the meaning of text into numbers. 





Query: "how to boost wheat production" → [0.56, 0.12, -0.43, 0.88, ..]
Document: "methods to improve crop yield" → [0.54, 0.10, -0.39, 0.86, ...]








