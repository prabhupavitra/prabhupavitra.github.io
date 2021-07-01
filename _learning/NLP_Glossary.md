---
title: "NLP Series - Essentials "
excerpt: "Core terminologies and techniques used in NLP"
date:   2021-04-15 22:12:28 -0500
theme : "mint"
---

<img src="/img/Learning/NLP/NLP Dictionary Featured.png" alt="this is a placeholder image" width="100%" height = "50%" class="center" >

> <span style="font-family:Georgia; font-size:20px;"> Natural Language Processing Basics - Core Terminologies and Techniques</span>   

<span style="font-family:Georgia; font-size:16px;"> If there's one form of media which we are exposed to every single day, it's text. There is huge amounts of data created by people and devices, every single day. This data includes and is not limited to comments on social media, product reviews, tweets and reddit messages. Generally speaking, the data from these sources are useful for the purposes of research and commerce. </span>  

<span style="font-family:Georgia; font-size:16px;"> This article serves as a detailed  of all the NLP core terminologies discussed in the NLP series and more. This page is updated frequently and the topics discussed has been categorized for easier understanding. I request you to follow the references and learn more on the topics listed below. </span>   

### Data Collection

<span style="font-family:Georgia; font-size:16px;">**Synonym Replacement & Antonym replacement**</span>  
<span style="font-family:Georgia; font-size:16px;">Synonym replacement is a technique in which we replace a word by one of its synonyms. This technique works by collapsing related terms and reducing the vocabulary of the corpus without losing meaning, thus saving a lot of memory. These individual identifiers are a set of one or more synonyms that are interchangeable in some context without changing the truth value of the proposition in which they are embedded and are called *synsets*.</span>  

<span style="font-family:Georgia; font-size:16px;">As we know that an antonym is a word having opposite meaning of another word, and the opposite of synonym replacement is called antonym replacement.</span>  

<span style="font-family:Georgia; font-size:16px;">**Back Translation**</span>  
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**TF-IDF based word replacement**</span>  
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Bigram Flipping**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Replacing entities**</span>  
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Adding noise to data**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Snorkel**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Easy Data Augmentation**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Active learning**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

### Data Cleaning

<span style="font-family:Georgia; font-size:16px;">**Unicode Normalization**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Text Encoding**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Bag-of-words**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Optical character recognition**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

### Text Pre-processing

<span style="font-family:Georgia; font-size:16px;">**Sentence Segmentation**</span>   
<span style="font-family:Georgia; font-size:16px;">*Sentence segmentation*, also known as *sentence boundary disambiguation*, *sentence breaking* and *sentence boundary detection* is one of the foremost problems of NLP referring to dividing text into its component sentences.</span>   

<span style="font-family:Georgia; font-size:16px;">**Tokenization**</span>   
<span style="font-family:Georgia; font-size:16px;">The process of breaking a piece of text into its constituent parts is called *Tokenization*. Usually, the fo job in an NLP project is to divide the text into a list of tokens. The granularity of the resulting tokens will differ depending on the objective of our NLP task. In other words, tokens can be individual words, phrases or even whole sentences. Almost every NLP task uses some sort of tokenization technique. Some of the techniques used for tokenization include white space tokenization, dictionary based tokenization and subword tokenization.*White space tokenization* is the simplest form of tokenization where the sentence or paragraph is broken into terms whenever a whitespace is encountered. On the contrary, **Dictionary based tokenization is a more advanced method compared to the whitespace tokenization and the tokens are found based on the tokens already existing in the dictionary. *Subword tokenization* is a recent strategy that uses unsupervised machine learning techniques to help us combat problems of misspellings, rare words, and multilingual sources by breaking unknown words into “subword units”. </span>   

<span style="font-family:Georgia; font-size:16px;">**Stemming**</span>  
<span style="font-family:Georgia; font-size:16px;">*Stemming* usually refers to a crude heuristic process that chops off the ends of words in the hope of achieving this goal correctly most of the time, and often includes the removal of derivational affixes. The first stemming algorithm was created by Julie Beth Lovins in 1968, although there had been earlier work done on the subject. In 1980, Martin Porter created the Porter Stemmer. This is certainly the most well-known stemming algorithm that has repeatedly been shown to be empirically very effective, and is called the Porter's algorithm. Stemming requires no memory and it can be easily tuned since its based on an algorithm. But, since it may not return an actual word, it is not always interpretable, and hence not useful if this result facing end-users.</span>   

<span style="font-family:Georgia; font-size:16px;">**Lemmatization**</span>  
<span style="font-family:Georgia; font-size:16px;">*Lemmatization* is the process of grouping together the inflected forms of a word so they can be analysed as a single word. This word is called its *lemma*, or the head word. For example, "eating", "eat" and "ate" can be counted as one word and as variations of the word "eat". Lemmatization returns the base or dictionary form of a word, and hence the result of this process is interpretable. Lemmatization is usually slower than stemming.</span>  

<span style="font-family:Georgia; font-size:16px;">**Text Normalization**</span>  
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Language Detection**</span>  
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Code Mixing and Transliteration**</span>  
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Chunking**</span>  
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**POS Tagging**</span>  
<span style="font-family:Georgia; font-size:16px;">Part-of-speech tagging refers to a technique of identifying whether words in a sentence are nouns, verbs, adjectives, and so on.</span>  

<span style="font-family:Georgia; font-size:16px;">**Parse Tree**</span>  
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Coreference Resolution**</span>  
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Lowercasing**</span>  
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Collocation Extraction for Phrase Detection**</span>  
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**HYPOTHESIS TESTING FOR COLLOCATION EXTRACTION**</span>  
<span style="font-family:Georgia; font-size:16px;"></span>  

### Feature Engineering of Text Data

<span style="font-family:Georgia; font-size:16px;">**Bag-of-Words**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Bag-of-n-Grams**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Removing Stopwords**</span>    
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Frequency-Based Filtering**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Rare words**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

### NLP Tasks

<span style="font-family:Georgia; font-size:16px;">**Information Extraction**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Topic Modeling**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Word Embeddings**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Text Classification**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Sentiment Analysis**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Sequence Modeling**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Chatbots**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Text Summarization**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Document Classification**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Grammatical Error Correction/Autocorrect**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Text-to-Speech**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Speech-to-Text**</span>   
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Dialogue Understanding**</span>     
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Fake News Detection/Hate Speech Detection**</span>     
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Image captioning**</span>     
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Question and answering**</span>     
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Semantic textual similarity**</span>     
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Word Sense Disambiguation**</span>     
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Keyword Extraction**</span>     
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Annotation**</span>     
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Document Ranking**</span>     
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**   Relation extraction**</span>     
<span style="font-family:Georgia; font-size:16px;"></span>  

<span style="font-family:Georgia; font-size:16px;">**Named entity recognition**</span>      
<span style="font-family:Georgia; font-size:16px;"></span>  



### References

<span style="font-family:Georgia; font-size:16px;">1. Alice Zheng and Amanda Casari. 2018. Feature engineering for machine learning: principles and techniques for data scientists. O'Reilly Media, Inc.</span>   

<span style="font-family:Georgia; font-size:16px;">2. Alex Thomas. 2020. Natural Language Processing with Spark NLP. O'Reilly Media, Inc.</span>   

<span style="font-family:Georgia; font-size:16px;">3. Sowmya Vajjala, Bodhisattwa Majumder, Anuj Gupta, Harshit Surana. 2020. Practical Natural Language Processing. O'Reilly Media, Inc.</span>   

<span style="font-family:Georgia; font-size:16px;">4. Bird, Steven, Ewan Klein, and Edward Loper. Natural Language Processing with Python. Sebastopol, CA: O’Reilly Media, 2009.</span>   

<!-- <span style="font-family:Georgia; font-size:16px;">5.

<span style="font-family:Georgia; font-size:16px;">6.

<span style="font-family:Georgia; font-size:16px;">7.

<span style="font-family:Georgia; font-size:16px;">8.

<span style="font-family:Georgia; font-size:16px;">9.

<span style="font-family:Georgia; font-size:16px;">10. -->


<span style="font-family:Georgia; font-size:16px;"> Thanks for reading! I hope you found this article helpful. Read more data science articles <a href="https://prabhupavitra.github.io/learning/"> here </a> including tutorials from beginner to advanced levels!  </span> 
