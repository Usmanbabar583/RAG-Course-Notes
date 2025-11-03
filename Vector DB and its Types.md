**What are the vectors?**


Vectors are lists of numbers that represent some meaning. In AI and machine learning, we use them to represent words, sentences not by what they look like, but by what they mean.
The word “king” might become a vector like [0.21, 0.89, 0.13dlnlfmk.]
The word “queen” might become [0.19, 0.91, 0.10, ...]



They look like random numbers, but they capture relationships and meaning — e.g.
king - man + woman ≈ queen




What is a Vector Database?



A vector database is a special type of database that stores and searches these “meaning-based fingerprints”. A normal database (like SQL, MongoDB, etc.) searches using exact matches, e.g:



“Find all products where name = ‘wheat’”.



But a vector database searches by similarity in meaning.
For example:

“Find all products similar to ‘wheat’ in meaning” -> it will also bring “grain”, “barley”, etc.

So instead of matching text, it matches context — using mathematical distance between vectors (cosine similarity, Euclidean distance, etc.).




Steps for working with Vector DataBases





<img width="786" height="507" alt="image" src="https://github.com/user-attachments/assets/4023f62e-842f-4989-ba42-c40667f95e2f" />





Steps to use Weaviate Vector Database


1-> Creating a database instance or use an existing one





1-> Create and load Client





The Weaviate client is your program’s connection interface — a Python (or JS/Java/etc.) object that lets your code communicate with the Weaviate server.Normally, Weaviate runs as a separate server but here no need for a separate server. Starts Weaviate locally and gives you a client to talk to it (the variable client).






<img width="930" height="247" alt="image" src="https://github.com/user-attachments/assets/09b1c84f-e513-45cf-b8c8-ad6e23d2e0fc" />










2-> Create a collection (grouping of related data records) to hold Data


here collection is article that holds body of article and title.







<img width="1027" height="271" alt="image" src="https://github.com/user-attachments/assets/e8d2ce60-2c73-423c-baa6-1f7c578956ec" />








3->Add Data in the Collection




after configuring our collection the next step is to add data in the collection. This code is adding data into the collection using batch method of the collection.







<img width="1012" height="292" alt="image" src="https://github.com/user-attachments/assets/28a9460c-95ec-41c0-94db-dbddf2a10645" />





Now we are ready for vector data search






<img width="990" height="307" alt="image" src="https://github.com/user-attachments/assets/b13b8ff6-bed4-4d9c-98b2-3e4f636403e3" />





Use Weaviate Vector DB




1-> Create and load Client





The Weaviate client is your program’s connection interface — a Python (or JS/Java/etc.) object that lets your code communicate with the Weaviate server.Normally, Weaviate runs as a separate server but here no need for a separate server. Starts Weaviate locally and gives you a client to talk to it (the variable client).








