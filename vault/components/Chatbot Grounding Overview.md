
Since we are (at least in the initial phase of this project) using an off-the-shelf frontier model to generate the response ultimately returned to a chatbot user, our actual job is to build a system around the LLM to shape its response and ground it in the information provided by our curated set of peer-reviewed publications on gun safety topics.

The technique for grounding LLM responses in sources of truth is known as Retrieval Augmented Generation, or [RAG](https://en.wikipedia.org/wiki/Retrieval-augmented_generation). 

![[Pasted image 20260528224925.png]]
In its most basic form, RAG passes the user's prompt to an LLM along with some specific information that is relevant and ideally provides a factual answer to the question. This way, the LLM actually receives a prompt containing the user question + the answer present in the corpus, and its task is then to produce a response to the question based on the given context rather than inventing an answer. If we asked any base LLM these types of questions without RAG grounding, the likelihood of hallucination would be very high.

If token cost and LLM performance degradation with context size were not an issue, we could just include the entire set of PLEDGE curriculum docs/papers along with every LLM query, but in reality this would result in poor answer quality and immense cost. See [this blog post on "context rot" from chromadb](https://www.trychroma.com/research/context-rot)

Se instead, the success of RAG depends on the LLM actually being provided with specifically retrieved 'chunks' from the corpus that answer the prompt. This is achieved with a pipeline of chunking, embedding, and retrieval. Essentially, all of the documents the bot needs to know about are broken up into reasonably-sized chunks, and then a "search engine" over these chunks returns the top $k$ most relevant chunks to the query, which get passed along to the LLM. Embeddings are numerical representations of text that capture semantic meaning, enabling mathematical similarity comparisons across chunks (and the user query). 

A large part of our work in building and improving the PLEDGE chatbot will be in tuning our RAG pipeline. See [[PLEDGE Quality Iteration]] for how we will perform this eval.


### Resources

- [This AWS info page has a very good, concise explanation of RAG](https://aws.amazon.com/what-is/retrieval-augmented-generation/#how-does-retrieval-augmented-generation-work--1xobboj)
- [A more in-depth resource from IBM](https://www.ibm.com/think/topics/retrieval-augmented-generation)
- [unstructured.io open source library docs. good practical reference on how to go from documents to embedded chunks in a production system](https://docs.unstructured.io/open-source/core-functionality/overview)