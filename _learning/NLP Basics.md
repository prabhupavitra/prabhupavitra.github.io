---
title: "NLP Series - Linguistics"
excerpt: "Natural Language Processing"
date:   2021-04-01 22:12:28 -0500
theme : "dark"
---

<img src="/img/Learning/LearningTeaser/linguistics.jpg" alt="this is a placeholder image" width="100%" height = "50%" class="center" >

> <span style="font-family:Georgia; font-size:20px;"> Natural Language Processing Basics - Linguistics </span>   

<span style="font-family:Georgia; font-size:16px;"> Natural language processing (NLP) is a field at the intersection of computer science, artificial intelligence, and linguistics. NLP is performed by solving a number of sub-problems, where each sub-problem constitutes a level. Note that, a portion of those levels could be applied, not necessarily all of them. Also, the levels could be applied in a different order independent of their granularity.  </span>  

<span style="font-family:Georgia; font-size:16px;">This article is part of **Natural Language Processing** series where we cover most prominent building blocks in building Natural Language Processing(NLP) applications. In this article, we shall discuss some of the linguistic concepts that help in understanding NLP techniques.</span>  


<span style="font-family:Georgia; font-size:16px;"> Let's dive in to some of the subfields of linguistics that are vital for understanding NLP systems:</span>


<span style="font-family:Georgia; font-size:16px;"> 1. [Phonetics & Phonology](#phonetics--phonology)</span>   
<span style="font-family:Georgia; font-size:16px;"> 2. [Morphology](#morphology)</span>   
<span style="font-family:Georgia; font-size:16px;"> 3. [Syntax](#syntax)</span>   
<span style="font-family:Georgia; font-size:16px;"> 4. [Semantics](#semantics)<span>   
<span style="font-family:Georgia; font-size:16px;"> 5. [Pragmatics](#pragmatics)</span>   

<span style="font-family:Georgia; font-size:16px;">There are a couple of other topics we should keep in mind when understanding linguistics for the purpose of building NLP systems and understanding them certainly helps in understanding how NLP systems work.</span>  

<span style="font-family:Georgia; font-size:16px;"> 1. [Sociolinguistics](#Sociolinguistics)</span> 
<span style="font-family:Georgia; font-size:16px;"> 2. [Computational Linguistics](#computational-linguistics)</span> 
<span style="font-family:Georgia; font-size:16px;"> 2. [Writing Systems](#writing-systems)</span> 

<figure>
<img src="/img/Learning/NLP/major_levels_of_linguistic_structure.png" alt="this is a placeholder image" width="100%" height = "50%" class="center" >
  <figcaption style="color: grey"> Figure 1: Major Subfields of Linguistics</figcaption>
</figure>

### Phonetics & Phonology

<span style="font-family:Georgia; font-size:16px;"> **Phonetics** is the study of individual sounds in verbal languages, or handshapes in sign languages. It deals with the production of speech sounds by humans, often without prior knowledge of the language being spoken. It also looks at the concept of voicing, occurring at the pair of muscles found in your voice box. For instance, the same sound may be represented by many letters or combination of letters(i.e. All underlined letters have same pronounciation: h<u>e</u>, p<u>eo</u>ple, k<u>e</u>y, bel<u>ie</u>ve, s<u>ei</u>ze, mach<u>i</u>ne, s<u>ea</u>s, s<u>ee</u>, am<u>oe</u>ba). The same letter may even represent a variety of sounds.   </span>

<span style="font-family:Georgia; font-size:16px;">In 1888, the International Phonetic Alphabet (IPA) was invented in order to have a system in which there was a oneto-one correspondence between each sound in language and each phonetic symbol. The IPA uses symbols to represent a great variety of sounds. </span>

<span style="font-family:Georgia; font-size:16px;">**Phonology** refers to the study of how the individual sounds or handshapes are combined into specific patterns. It is a branch of linguistics that studies how languages or dialects systematically organize their sounds. The  fundamental unit of sound in a language is the *Phoneme*. Phonemes are specifically important in applications involving speech understanding, such as speech recognition, speech-to-text transcription, and text-to-speech conversion.
Languages have phonologies, which are collections of phonemes and rules about how to use and realize the phonemes.</span>

### Morphology
<span style="font-family:Georgia; font-size:16px;">**Morphology** is the study of morphemes. A morpheme is the smallest unit of language that has a meaning. Not all morphemes are words, but all prefixes and suffixes are morphemes. For instance, in the word "multitasking", "multi-" is not a word but a prefix that changes the meaning when put together with “task". "Multi-" is a morpheme. Lexemes are the structural variations of morphemes related to one another by meaning. Morphological analysis, analyzes the structure of words by studying its morphemes and lexemes, and is a foundational block for many NLP tasks, such as tokenization, stemming, learning word embeddings, and part-of-speech tagging. </span>

<span style="font-family:Georgia; font-size:16px;">There are four kinds of morphemes, defined by unbound versus bound and content versus functional: Content morphemes, Functional morphemes, derivational affixes and inflectional affixes. Content morphemes(Unbound content morphemes or lexical morphemes) express a concrete meaning or content, and function morphemes have more of a grammatical role. For example, the morphemes cat and fast can be considered content morphemes. On the other hand, the unbound functional morphemes are words that perform a function in a sentence. The examples include words like "they" and "will" which are used to make the future tense. Then, there is bound content morphemes(also called derivational affixes), that turn one word into another. For instance,"er" used with word "call" can turn the word into another word "caller". The last one, Bound functional morphemes or inflectional affixes, refers to the affixes that indicate the function of a word in a sentence. Examples : "-ed" (past tense, "cook" + "-ed" = "cooked", "-(e)s" (plural, "flower"+"-(e)s" = "flowers", "pass"+"-(e)s" = "passes")</span>   

### Syntax
<span style="font-family:Georgia; font-size:16px;">Syntax is a set of rules to construct grammatically correct sentences out of words and phrases in a language. Syntactic structure in linguistics is represented in many different ways. A common approach to representing sentences is a parse tree, also called as phrase structure trees (PSTs). Let’s look at the PST in Figure 2 for the following sentence:   </span>

<span style="font-family:Georgia; font-size:16px;">*The chef cooks the soup.*</span>   

<figure>
<img src="/img/Learning/NLP/pst.png" alt="this is a placeholder image" width="100%" height = "50%" class="center" >
  <figcaption style="color: grey"> Figure 2: Syntactic structure of the sentence (Phrase Structure Tree)</figcaption>
</figure>


### Semantics

<span style="font-family:Georgia; font-size:16px;">Semantics, is the study of the meaning of linguistic elements. It is the direct meaning of the words and sentences without external context. One feature of the field of semantics is, modeling how meaning is composed from the structures of language, so semantics is most closely related to syntax. Most projects that use NLP are looking for the meaning in the text being analyzed, so we will be revisiting this field multiple times. </span>

### Pragmatics
<span style="font-family:Georgia; font-size:16px;">Pragmatics is a subfield that looks at the use and meaning of language in context. It will help us understand the intent behind the text we are analyzing. It adds world knowledge and external context of the conversation to enable us to infer implied meaning. It is sometimes defined in contrast with linguistic semantics, which can be described as the study of the rule systems that determine the literal meanings of linguistic expressions. </span>

<span style="font-family:Georgia; font-size:16px;">According to Roman Jakobson, we can divide the functions of language into six factors which are required for communication. This model of pragmatics considers messages as focusing on some combination of these factors. Following are the six functions (with the associated factor):</span>

<span style="font-family:Georgia; font-size:16px;">- Emotive (the addresser)</span>  
<span style="font-family:Georgia; font-size:16px;">- Conative (the addressee)</span>  
<span style="font-family:Georgia; font-size:16px;">- Poetic (the message)</span>   
<span style="font-family:Georgia; font-size:16px;">- Metalingual (the code)</span>   
<span style="font-family:Georgia; font-size:16px;">- Phatic (the channel)</span>   
<span style="font-family:Georgia; font-size:16px;">- Referential (the context)</span>     


<figure>
<img src="/img/Learning/NLP/roman_jakobson_model.jpeg" alt="this is a placeholder image" width="100%" height = "50%" class="center" >
  <figcaption style="color: grey"> Figure 3: Roman Jakobson’s functions of language</figcaption>
</figure>

### Sociolinguistics

<span style="font-family:Georgia; font-size:16px;"> Sociolinguistics is the study of the complex relationship between language and society. Although sociolinguistics is not a major subfield of linguistics, it is an interdisciplinary field between sociology and linguistics. Understanding the social context of text is important in understanding how to interpret the text.  </span>

<span style="font-family:Georgia; font-size:16px;">Every individual has their own unique personal version of language. The collection of varieties that an individual speaks can be considered an *idiolect*. The different varieties that an individual uses are called *registers*. Registers covers the concept of formality as well as other manners of speech, gesture, and writing.</span>

### Computational Linguistics

<span style="font-family:Georgia; font-size:16px;">Computational linguistics is the scientific and engineering discipline concerned with understanding written and spoken language from a computational perspective, and building artifacts that usefully process and produce language, either in bulk or in a dialogue setting. It is the study of linguistics from a computational perspective. This means using computers and algorithms to perform linguistics tasks such as marking your text as a part of speech (such as noun or verb), instead of performing this task manually.</span>

### Writing Systems

<span style="font-family:Georgia; font-size:16px;">In this article we’ve discussed many aspects of language, but so far we’ve focused on aspects that are part of language that is either only spoken or both spoken and written. Writing system, also called as Orthography, refers to the set of conventions used to represent a language in writing.</span>

<span style="font-family:Georgia; font-size:16px;">The smallest meaningful contrastive unit in a writing system is called a **grapheme**. There are various kinds of writing systems depending upon what the grapheme is used to represent. Alphabets, abjads, abugidas, syllabaries and logographs are some of them. We shall discuss each one of them in detail.  </span>

<span style="font-family:Georgia; font-size:16px;"> An **alphabet** is a phonetic-based writing system in which there is a symbol representing consonants and vowels. Examples of alphabet writing systems include Latin, Cyrillic, Greek, Hangul and so on. Latin is used throughout the world for many languages in Western Europe, like English and Finnish, and for ones that were influenced by European colonization, like Vietnamese and Swahili. The Cyrillic alphabet is used in many countries in Eastern Europe, Central Asia, and North Asia. Some languages that use Cyrillic alphabets include Russian and Bulgarian. Whereas the Greek alphabet is used by modern Greek and its dialects, and by some minority languages in Greek-speaking majority areas, the Hangul alphabet, is used to write Korean. </span>

<span style="font-family:Georgia; font-size:16px;"> An **abjad**, is a phonetic-based writing system in which the consonants get their own symbols, and vowels can be left unwritten. One important thing to keep in mind when creating UIs for languages that use these scripts is that these writing systems are almost entirely written right-to-left. Examples include many Semitic languages like Arabic and Hebrew. </span>   

<span style="font-family:Georgia; font-size:16px;">A **syllabary** is a phonetic-based system of writing in which there is a different symbol for each possible syllable in a language. In contrast to the other phonetic-based systems, syllabaries are often invented, instead of being derived. Examples include Hiragana, which is one of the syllabaries used to write Japanese, and Katakana, used to write Ainu, an interesting language spoken in northern Japan and unrelated to Japanese. Then there is Tsalagi, the syllabary invented by Sequoyah for writing his native Cherokee language.</span>    

<span style="font-family:Georgia; font-size:16px;">An **abugida**, sometimes known as alphasyllabary, neosyllabary or pseudo-alphabet, is a segmental writing system in which consonant-vowel sequences are written as a unit; each unit is based on a consonant letter, and vowel notation is secondary.Consider the most widely used abugida today, Devanagari. It originated some time before the 10th century AD, developed from the earlier Brahmi script. The other examples include, Thai, derived from the Brahmi script, and Ge’ez, used in East Africa to write various languages of Ethiopia.</span>

<span style="font-family:Georgia; font-size:16px;">Finally, we have writing systems where each grapheme can represent a whole word or morpheme of any length. They are called **logographic** writing systems. There is only one such system widely used today—Han Chinese characters. It is used to write most of the languages of China, as well as Japanese uses Hanji, Chinese logographs, combined with Hiragana.</span>

<span style="font-family:Georgia; font-size:16px;"> Thanks for reading! I hope you found this article helpful. Read more data science articles <a href="https://prabhupavitra.github.io/learning/"> here </a> including tutorials from beginner to advanced levels!  </span> 
