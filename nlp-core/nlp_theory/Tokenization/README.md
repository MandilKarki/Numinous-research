# Overview
- This article focuses the significance of tokenization in NLP and how it helps machines to learn the meaning of words and phrases.
- Teaching machines to read and understand text is a challenging task, but it is possible with the right approach. The goal is to enable them to read and understand the meaning of text.
- To process text, machines first need to tokenize it, which means dividing the text into smaller units called tokens.
- To be used by language models like BERT, text must first be tokenized, which is the process of dividing it into smaller units called tokens.
- The ability of models to understand the meaning of text is still being investigated, but it is thought that they learn syntactic knowledge at lower levels of the neural network and semantic knowledge at higher levels.[Source](https://hal.inria.fr/hal-02131630/document)
- Instead of treating text as a single string, it can be broken down into a list of individual words, called tokens. This is called tokenization.

# Tokenization

Tokenization is the process of splitting a text into smaller units, called tokens, which can be words, subwords, or characters. It is one of the first steps in an NLP pipeline.

![tokenization](https://github.com/ghimiresunil/LLM-PowerHouse-A-Curated-Guide-for-Large-Language-Models-with-Custom-Training-and-Inferencing/assets/40186859/9a5b49b1-4adf-4bdb-8a7f-856cb525235a)

| Tokenization Type | Description | Advantages | Disadvantages | Example |
| ----------------- | ----------- | ----------- | ------------ | -------- |
| Word-based tokenization	| Breaks a text into words based on a delimiter, such as a space or punctuation mark.	| Simple and efficient.	| Large vocabulary size and many OOV tokens, which can lead to a heavier model and loss of information.	| "This is a sentence." → ["This", "is", "a", "sentence"].|
| Character-based tokenization	| Splits the raw text into individual characters.	| Very small vocabulary and no or very few OOV tokens.	| Results in very long sequences and characters do not carry as much meaning as words.	| "This is a sentence." → ["T", "h", "i", "s", " ", "i", "s", " ", "a", " ", "s", "e", "n", "t", "e", "n", "c", "e"]. |
| Subword-based tokenization | Splits words into smaller units, called subwords.	| Reduces the vocabulary size and number of OOV tokens.	| More complex and computationally expensive than word-based tokenization.	| "This is a sentence." → ["This", "is", "a", "sent", "enc", "e"]. |

# Why Tokenization
- Tokenization helps split unstructured data or text into chunks of information.
- Chunks represent the discrete elements whose occurrences in a corpus document can be represented as a vector of the corresponding document. 
- The unstructured data can be represented as a numerical data structure which can be fed directly to machine learning algorithm.

# Tokenization: How Tokenization works?
- Tokenization is the process of breaking text into smaller units called tokens. There are many different ways to tokenize text, but some common methods include removing spaces, adding a split character between words, or simply breaking the input sequence into separate words. The image you provided shows a visualization of the tokenization process. 
- We can use one of these methods to tokenize the text, which means dividing it into smaller units called tokens. These tokens can then be used as input to the model.
- To learn the relationships between words in a sequence of text, we need to represent the text as a vector.
- We use a vector representation of text instead of hard coding grammatical rules, as this is more scalable and can be applied to any language. This is because the complexity of hard coding grammatical rules would be exponential, as it would need to be done for each language.
- The vector representation of a word encodes the word's meaning, including its syntactic and semantic properties.


# Sub-word Tokenization
- Sub-word tokenization is a technique that can be used to handle rare and out-of-vocabulary words by breaking words down into smaller units. This is because many words in a language share common prefixes or suffixes.
- Subword tokenization can help handle out-of-vocabulary (OOV) words by breaking them down into smaller units, such as "any" and "body" for the word "anybody". This approach can reduce the model size and improve efficiency, while also enabling the model to handle a broader range of vocabulary.
- The choice of subword tokenization algorithm depends on the NLP task. Different algorithms have different strengths and weaknesses, so it is important to choose the one that is best suited for the task at hand.
    - Example: 
        - The word "refactoring" can be split into the subwords "re", "factor", and "ing".
        - The word "uninteresting" can be split into the subwords "un", "inter", "est", and "ing".
        - The word "outperforming" can be split into the subwords "out", "per", "form", and "ing".

# Byte Pair Encoding (BPE)
- BPE is a subword tokenization algorithm that breaks down words into smaller units by merging the most common pairs of characters. It has been used in GPT-2 and RoBERTa, which are large language models.
- The algorithm starts by creating subwords from individual characters. It then repeatedly replaces the most frequent pairs of characters in the text with a new subword, which is represented by an unused byte.
- The process is repeated for a specified number of times or until the desired number of sub-words is obtained.
-  It was first described in the article “[A New Algorithm for Data Compression](https://www.derczynski.com/papers/archive/BPE_Gage.pdf)”
- The following example, taken from [Wikipedia](https://en.wikipedia.org/wiki/Byte_pair_encoding), will explain BPE.
> Suppose we have data $aaabdaaabac$ which needs to be encoded (compressed). The byte pair aa occurs most often, so we will replace it with $Z$ as $Z$ does not occur in our data. So we now have ZabdZabac where $Z = aa$. The next common byte pair is ab so let’s replace it with $Y$. We now have $ZYdZYac$ where $Z = aa$ and $Y = ab$. The only byte pair left is ac which appears as just one so we will not encode it. We can use recursive byte pair encoding to encode ZY as X. Our data has now transformed into XdXac where $X = ZY$, $Y = ab$, and $Z = aa$. It cannot be further compressed as there are no byte pairs appearing more than once. We decompress the data by performing replacements in reverse order.
- BPE is a subword-based tokenization algorithm that merges the most common pairs of characters into single tokens, while breaking down rare words into multiple tokens. 
- Consider augmenting the given words, namely `"old," "older," "“finest”," and "lowest"` with a special end token `"</w>"` attached to the end of each word. Upon calculating their occurrences in the corpus, the resulting frequency counts are as follows.

```python
# Before special end token </w>
{“old”: 7, “older”: 3, “finest”: 9, “lowest”: 4}

# After special end token </w>
{“old</w>”: 7, “older</w>”: 3, “finest</w>”: 9, “lowest</w>”: 4}
```
> To identify word boundaries, the algorithm adds the “</w>” token to the end of each word. This helps the algorithm find the most frequent character pairs by looking through each character.

- Next, we will tokenize each word into its characters, including the “</w>” token to mark the end of the word. Then, we will count the frequency of each character.

| Number | Token | Frequency |
| ------- | ----- | --------- |
| 1 | <\w> | 23 | 
| 2 | o | 14 | 
| 3 | l | 14 |
| 4 | d | 10 |
| 5 | e | 16 |
| 6 | r | 3 |
| 7 | f | 9 |
| 8 | i | 9 |
| 9 | n | 9 |
| 10 | s | 13 |
| 11 | t | 13 |
| 12 | w | 4 |

- The number of `“</w>”` tokens is equal to the number of words, which is 23. The second most frequent token is `“e”`, and there are a total of 12 different tokens.
- The next step in the BPE algorithm is to find the most frequently occurring pair of characters and merge them. This process is repeated until we reach the desired vocabulary size or the maximum number of iterations is reached.
- The goal of the BPE algorithm is to represent the corpus with the least number of tokens, which is achieved by merging the most frequently occurring byte pairs. In English, a character is the same as a byte, but this may not be the case in other languages. Once the most common byte pairs are merged, they are added to the list of tokens and the frequency of each token is recalculated. This process is repeated until the desired number of iterations is reached or the maximum token limit is reached.

- Iterations
    - Iteration 1:
    
    Starting with the second most common token `"e"`. The most common byte pair in our corpus with `“e”` is `“e”` and `“s”` which is in the words (finest and lowest). We merged the most common byte pair "e" and "s" (which occurred 9 + 4 = 13 times) to form a new token "es". The frequency of "es" is 13. We also reduced the count of "e" and "s" by 13. We can see that "s" does not occur alone and "e" occurs 3 times.

    | Number | Token | Frequency |
    | ------- | ----- | --------- |
    | 1 | <\w> | 23 | 
    | 2 | o | 14 | 
    | 3 | l | 14 |
    | 4 | d | 10 |
    | 5 | e | 16 - 13 = 3 |
    | 6 | r | 3 |
    | 7 | f | 9 |
    | 8 | i | 9 |
    | 9 | n | 9 |
    | 10 | s | 13 - 13 = 0 |
    | 11 | t | 13 |
    | 12 | w | 4 |
    | 13 | es | 9 + 4 = 13 |

    Iteration 2:

    Continuing the process, we merged the token "es" and "t" (which occurred 13 times) to form a new token "est". The frequency of "est" is 13. We also reduced the count of "es" and "t" by 13.

    | Number | Token | Frequency |
    | ------- | ----- | --------- |
    | 1 | <\w> | 23 | 
    | 2 | o | 14 | 
    | 3 | l | 14 |
    | 4 | d | 10 |
    | 5 | e | 3 |
    | 6 | r | 3 |
    | 7 | f | 9 |
    | 8 | i | 9 |
    | 9 | n | 9 |
    | 10 | s | 0 |
    | 11 | t | 13 - 13 = 0 |
    | 12 | w | 4 |
    | 13 | es | 13  - 13 = 0|
    | 14 | est | 13 |

    Iteration 3: 

    Continuing the process, the byte pair consisting of the characters "o" and "l" occurred 10 times in our corpus.


    | Number | Token | Frequency |
    | ------- | ----- | --------- |
    | 1 | <\w> | 23 | 
    | 2 | o | 14 - 10 = 4 | 
    | 3 | l | 14 - 10 = 4|
    | 4 | d | 10 |
    | 5 | e | 3 |
    | 6 | r | 3 |
    | 7 | f | 9 |
    | 8 | i | 9 |
    | 9 | n | 9 |
    | 10 | s | 0 |
    | 11 | t | 0 |
    | 12 | w | 4 |
    | 13 | es | 0|
    | 14 | est | 13 |
    | 15 | ol | 7 + 3 = 10 | 

    Iteration 4: 
    
    We now see that byte pairs “ol” and “d” occurred 10 times in our corpus.

    | Number | Token | Frequency |
    | ------- | ----- | --------- |
    | 1 | <\w> | 23 | 
    | 2 | o | 4 | 
    | 3 | l | 4|
    | 4 | d | 10 - 10 = 0|
    | 5 | e | 3 |
    | 6 | r | 3 |
    | 7 | f | 9 |
    | 8 | i | 9 |
    | 9 | n | 9 |
    | 10 | s | 0 |
    | 11 | t | 0 |
    | 12 | w | 4 |
    | 13 | es | 0|
    | 14 | est | 13 |
    | 15 | ol | 10 - 10 = 0| 
    | 16 | old | 10  | 

    Iteration 4:

    The stop token "</w>" is important in the BPE algorithm because it helps to distinguish between words that share common prefixes or suffixes. For example, the words "established" and "highest" both share the prefix "est". However, the algorithm can tell them apart because "established" ends with the stop token "</w>", while "highest" does not. This is because the algorithm knows that "</w>" marks the end of a word.

    | Number | Token | Frequency |
    | ------- | ----- | --------- |
    | 1 | <\w> | 23 - 13 = 10 | 
    | 2 | o | 4 | 
    | 3 | l | 4|
    | 4 | d | 0|
    | 5 | e | 3 |
    | 6 | r | 3 |
    | 7 | f | 9 |
    | 8 | i | 9 |
    | 9 | n | 9 |
    | 10 | s | 0 |
    | 11 | t | 0 |
    | 12 | w | 4 |
    | 13 | es | 0|
    | 14 | est | 13 - 13 = 0 |
    | 15 | ol |  0| 
    | 16 | old | 10  | 
    | 17 | `est</w>` | 13 | 

> Note: The frequency of the byte pair "fin" is 9, but we do not merge them because there is only one word that contains these characters. For the sake of brevity, let us stop the iterations here and examine the tokens.

| Number | Token | Frequency |
| ------- | ----- | --------- |
| 1 | <\w> |  10 | 
| 2 | o | 4 | 
| 3 | l | 4|
| 4 | e | 3 |
| 5 | r | 3 |
| 6 | f | 9 |
| 7 | i | 9 |
| 8 | n | 9 |
| 9 | w | 4 |
| 10 | old | 10  | 
| 11 | `est</w>` | 13 | 

- The number of tokens in the vocabulary was reduced from 12 to 11 after removing the tokens with zero frequency count. This is a small corpus, but in practice, the vocabulary size is much smaller.
- The token count increases and then decreases as we add more tokens. The stopping criterion can be either the number of tokens or the number of iterations. We choose the stopping criterion that breaks down the dataset into tokens in the most efficient way.


# Encoding and Decoding

| Process     | Description                                                                                             |
|-------------|---------------------------------------------------------------------------------------------------------|
| **Decoding**  | Reconstructs words by concatenating tokens.                                                         |
|             | Encoded Sequence: ["the</w>", "high", "est</w>", "range</w>", "in</w>", "Seattle</w>"]                |
|             | Decoded Output: ["the", "highest", "range", "in", "Seattle"]                                         |
|             | (Not: ["the", "high", "estrange", "in", "Seattle"])                                                  |
|             | "</w>" in "est" indicates word boundaries.                                                           |
| **Encoding**  | Replaces substrings in a sequence with training tokens.                                            |
|             | Word Sequence: ["the</w>", "highest</w>", "range</w>", "in</w>", "Seattle</w>"]                      |
|             | Iterates through tokens to replace substrings in sequence.                                          |
|             | Unmatched substrings replaced by unknown tokens.                                                     |
| **Vocabulary** | Vocabulary is large; potential for unknown words.                                                  |
| **Enhancement** | Maintains dictionary of pre-tokenized words.                                                      |
|             | Utilizes encoding to tokenize new words and adds to dictionary.                                     |


# Isn’t it greedy? 
| Aspect | Description | 
| Approach | Greedy approach to merge frequent character/subword pairs iteratively. | 
| Efficiency | Efficiently represents the corpus by breaking words into subword units. | 
| Handling Rare Words | Improves handling of rare words and morphemes for better generalization. | 
| Performance | Widely used in NLP tasks due to its ability to handle morphological variations and rare words. | 

> Note: Keep in mind that while BPE is a widely used technique, there are other subword tokenization methods like Unigram Language Model and SentencePiece that offer similar benefits. The choice of method depends on the specific task and dataset you're working with.


# Unigram Sub-word Tokenization 
- The algorithm first creates a vocabulary of the most common words in the text. Then, it represents all other words in the text as a combination of words in the vocabulary.
- The algorithm iteratively decomposes the most probable word into smaller subwords until the desired number of subwords is reached.
- A unigram model is a probabilistic language model that trains by removing the token that has the least impact on the overall likelihood of the model, until it reaches the desired number of tokens.

**Mathematical Calculation**:
- The process begins with a large vocabulary and removes tokens until the desired size is reached.

Let me explain step by step with an example. Let our corpus with frequency be
``` python
        ("t","u",g",9), 
        ("m","u",g",7), 
        ("f","u","n",11), 
        ("h","u",g",5),
        ("r","u",n",8)
```

**Step 1**: Pretokenization
- There are two main ways to build the initial vocabulary: by taking the most common substrings in pre-tokenized words, or by using *BPE*.

Let the whole vocabulary be:

```python
["t","u","g","m","f","r","h","n","tu","ug","mu","fu","un","hu","ru"]
```

**Step2**: Calculate the probability and tokens of all words based on vocabulary.

To start, we will count how many times each word appears in the vocabulary. This will give us the frequency of each word.

```python
    {
        "t" = 9
        "u" = 40
        "g" = 21
        "m" = 7
        "f" = 11
        "r" = 8
        "h" = 5
        "n" = 8
        "tu" = 9
        "ug" = 21
        "mu" = 7
        "fu" = 11
        "un" = 19
        "hu" = 5
        "ru" = 8
    }
```

The vocabulary has a total of 189 words. To tokenize a word, we will find the probability of each possible way to split the word into tokens. We do this by using the Unigram model, which assumes that each token is independent of the others. So, the probability of a segmentation is just the product of the probabilities of the individual tokens.

$$P(X) = \prod_{i=1}^{M} p(x_i)$$
$$\forall{i}\ x_i \  \in  v, \sum_{x_i \  \in\ v} p(x) = 1$$

The most probable segmentation is given as
$$X^{*} = arg max\ P(X)$$ 
$$X \in S(X)$$

Let me give you an example. Let's take the word "hug".

```python
p("h","u",g") = p("h") x p("u") x p("g")
              = (5/189) x (40/189) x (21/189)
              = 0.000620

p("h","ug") = p("h") x p("ug") 
            = (5/189) x (21/189) 
            = 0.00293

p("hu","g") = (5/189) x (21/189)
            = 0.00293
```

> Generally tokenization with least sub words or tokens will have the highest probability.  If two tokenizations have the same number of probability, then the algorithm will choose the one that it encounters first. Therefore, the word "hug" could be tokenized as either `["hu", "g"] or ["h", "ug"]`, depending on the training data.

> Similarly we have to find probabilities for all words which we need to tokenize.

**Step 3**: Compute the loss by removing a token from vocabulary. Repeat it for all tokens and choose the remove the token which decreases loss least.

Loss is given by equation:
$$\mathcal{L} = \sum_{s=1}^{|D|}\ log(P(X^{(s)}))\ = \sum_{s=1}^{|D|}\ log(\sum_{x \in S(X^{(x)})} P(x)$$ 

Let the tokenization of all words result in following tokens and sum of probability scores.

```python
    "tug": ["tu","g"] (score 0.071428)
    "mug": ["mu", "g"] (score 0.007710)
    "fun": ["f", "un"] (score 0.006168)
    "hug": ["h","ug"] (score: 0.00648)
    "run": ["r", "un"] (score 0.001451)
```

The loss is the sum of the negative log probabilities of all the words in the corpus, where the negative log probability of a word is the logarithm of the probability that the word will occur in the corpus.

```python
9 * (-log(0.071428)) + 7* (-log(0.007710)) + 11 * (-log(0.006168)) + 5 * (-log(0.00293)) + 8 * (-log(0.001701)) = 382.106.
```

The total loss is 382.106. We want to find out which tokens in the vocabulary have the least impact on the loss. We could compute the loss for each token, but that would make the article too long. Here's an intuitive explanation: if we remove the token "hu", the score will not change because the probability of the sequence `["hu", "g"]` is the same as the probability of the sequence `["h", "ug"]`. So, we can remove the token "hu" from the vocabulary.

Suppose, if there is another word `mugs` with score `0.001701`. Then, removing `mug` will make the loss worse, because the tokenization of `mug` and `mugs`

```python
"mug": ["mu", "g"] (score 0.007710)
"mugs": ["mu", "gs"] (score 0.001701)
```

These changes will cause the loss to rise by:

```python
- 10 * (-log(0.007710)) + 10 * (-log(0.001701)) = 25.741
```

So, the token `hu` will probably be removed from the vocabulary, but not `mug`.


> Note: `Steps 2` and `Step 3` are repeated with the new vocabulary. These steps are repeated until the loss threshold is met or a fixed number of iterations is reached. 

# WordPiece

- WordPiece is a subword tokenization algorithm that starts with a vocabulary of individual characters and iteratively adds the most frequent and meaningful sequences of characters to the vocabulary. It is used in models like BERT and DistilBERT.
- The algorithm starts by splitting the most probable word into smaller parts. It then assigns a probability to each sub-word based on its frequency in the text. This process is repeated until the desired number of sub-words is reached.
> `WordPiece` algorithm is not very different from `BPE`, so I recommend you first understand BPE before going through `WordPiece`. 
- To recall, BPE iteratively merges the most frequent pairs of tokens (bytes) until a predefined vocabulary size is reached. This process is greedy, meaning that it always merges the pair with the highest combined frequency.
- Problem with `BPE`: The issue with `BPE` is that it can sometimes encode a word in multiple ways, making it hard for the algorithm to decide which subword tokens to use first. This can result in different encodings for the same input, affecting the accuracy of learned representations. 

    Please refer to the following table of subword tokens.

    | Number | Token | Frequency |
    | ------- | ------ | -------- |
    |  1     | li    |     3       |
    |  2     | l    |     5       |
    |  3     | ea    |     2       |
    |  4    | eb    |     4       |
    |  5     | near    |     6      |
    |  6     | bra    |     2       |
    |  7     | al    |     4       |
    |  8     | n    |     5       |
    |  9     | r    |     1       |
    |  10     | ge   |     11       |
    |  11     | g    |     7       |
    |  12    | e    |     8       |

    Given the vocabulary for a small corpus, we can tokenize the input phrase "linear algebra" as follows:

    | word | Tokenize 01 | Tokenize 02 |
    | ----- | ---------- | ----------- |
    | linear |  li + near | li + n + ea + r |
    | algebra | al + ge + bra | al + g + e + bra |

    The phrase **"linear algebra"** can be tokenized into four different ways and there are two different ways to tokenize each word in the phrase, and the order of the subwords can also be different. This can be a problem, as it can make it difficult for the algorithm to choose the correct subword tokens. 

    When we consider progress and enhancement in any field, we often seek a more effective and true-to-life method. One possible improvement over BPE's frequency-based approach is to consider the impact of merging a particular byte-pair (symbol pair) at each step. 

    > WordPiece and BPE are both probabilistic approaches to tokenization. The main difference is that WordPiece chooses the symbol pair that maximizes the likelihood of the training data, while BPE chooses the most frequent symbol pair.

    FOr example, `WordPiece` algorithm merges two characters if the probability of the two-character sequence occurring is greater than the probability of the two characters occurring separately. Mathematically, this can be expressed as:

    ```python
    p(es) > p(e) * p(s)
    ```

    ```python
    p(es): the probability of the two-character sequence "es" occurring
    p(e): the probability of the character "e" occurring
    p(s): the probability of the character "s" occurring
    ```

    In other words, the algorithm will merge the two characters "e" and "s" if the probability of them occurring together is more than the probability of them occurring separately. This is because it is more likely that the two characters will occur together if they are merged into a single symbol.

    Let's say, if the probability of "es" occurring is 0.5, the probability of "e" occurring is 0.2, and the probability of "s" occurring is 0.3, then the algorithm would merge the two characters "e" and "s". This is because 0.5 is greater than 0.2 * 0.3.

    - The WordPiece algorithm is iterative and the summary of the algorithm according to the [paper](https://static.googleusercontent.com/media/research.google.com/ja//pubs/archive/37842.pdf) is as follows:
        - Initialize the word unit inventory with the base characters. This means starting with the individual characters in the language, such as "a", "b", "c", and so on.
        - Build a language model on the training data using the word inventory from 1. This means creating a statistical model that predicts the probability of each word in the training data occurring. The model is trained using the word inventory, which in this case is just the individual characters.
        - Generate a new word unit by combining two units out of the current word inventory. This means taking two characters from the word inventory and combining them into a single unit. For example, if the word inventory contains the characters "a" and "b", then we could generate the word unit "ab".
        - The word unit inventory will be incremented by 1 after adding this new word unit. This means adding the new word unit to the word inventory.
        - The new word unit is chosen from all the possible ones so that it increases the likelihood of the training data the most when added to the model. This means choosing the new word unit that is most likely to occur in the training data.
        - Repeat steps 2-5 until the word inventory reaches a pre-defined size or the likelihood increase falls below a certain threshold.

# Is it still greedy?

`WordPiece` is a greedy algorithm, but it follows a probabilistic approach to choosing the pairs to merge. This makes it more likely to produce accurate encodings, even though it does not always choose the best pair at each iteration.

# Summary of `WordPiece`
The WordPiece algorithm starts with a base vocabulary of individual characters. It then iteratively trains a language model on the vocabulary, and picks the pair of characters with the highest likelihood to merge. The new pair is added to the vocabulary, and the language model is retrained on the new vocabulary. This process is repeated until the desired vocabulary size or likelihood threshold is reached.

**Pros**
-  WordPiece helps in reducing the vocabulary size and can effectively handle OOV words by breaking them down into known sub-words. It also aids in preserving semantic meaning as some subwords can stand as individual words.

**Cons**
- If the sub-word unit does not exist in the vocabulary, WordPiece further breaks it down into individual characters, which might result in loss of semantic meaning.

**Time Complexity**
- The `WordPiece` use brute-force approach to training a language model is computationally expensive, with a time complexity of O(K²), where K is the number of word units. This is because the algorithm needs to test all possible pairs of word units and train a new language model for each pair.

# SentencePiece

| Feature | Description |
| -------- | ----------- |
| Type | Unsupervised text tokenizer and detokenizer |
| Usage | Mainly for Neural Network-based text generation systems | 
| Vocabulary Size Determination	 | Predetermined prior to neural model training |
| Tokenization Methods | BPE and unigram language model, with direct training from raw sentences |
| Supervised/Unsupervised | Unsupervised, no external training data required| 
| Sub-word Unit Learning | Learns directly from input text |
| Handling Out-of-Vocabulary Words	| Generates new sub-word units on the fly |
| Multilingual Support	| Handles multiple languages with a single model |
| Text Normalization | Can be used for text normalization |
| Usage in Transformer Models	| Widely used in models like BERT, RoBERTa, and GPT-3 |
| Pros | 1. No pre-tokenization required. <br> 2. Language-independent. <br> 3. No language-specific pre/post-processing. |
| Cons |  It could lead to inefficient encoding for languages with many multi-byte characters (e.g., Asian languages), as it treats each Unicode character as a potential token. | 

**Problems is SentencePiece addressing :**
| Feature |	SentencePiece |	BPE/Unigram Models|
| ------- | -------------- | ----------------|
| Input Tokenization |	Raw text input; no pre-tokenization needed	| Requires input to be pre-tokenized |
| Language Agnostic	| Language-independent; works for all languages	| Requires language-specific rules
| Decoding Ambiguity | 	Avoids ambiguity in token encoding	| Ambiguity in token encoding rules |
| End-to-End Solution |	Provides a complete end-to-end solution	| Only part of a tokenization solution | 

# Comparative Analysis Summary

| Algotithm | Description	| Supervised? | 	Popularity | 	Applications | 
| --------- | -------------- | ------------ | ------------- | -------------- |
| Byte-Pair Encoding (BPE)	| Starts with a set of individual characters as the initial subwords. Iteratively replaces the most frequent pair of bytes (or characters) in the text with a new, unused byte.	| Yes | Widely used	| Neural machine translation, text summarization, question answering |
| Unigram Subword Tokenization	| Starts with a set of words, and then iteratively splits the most probable word into smaller parts. Assigns a probability to the newly created subwords based on their frequency in the text.	| No	| Less popular |	Language modeling, text-to-speech |
| WordPiece | Starts with a set of words, and then iteratively splits the most probable word into smaller parts. Assigns a probability to the newly created subwords based on their frequency in the text.	| No	| Less popular |	Neural machine translation | 
| SentencePiece | Based on the byte-pair encoding (BPE) algorithm. Unsupervised, which means that it does not require any external training data. Has a built-in mechanism for handling out-of-vocabulary words. Can handle multiple languages with a single model and can also be used for text normalization. Widely used in modern transformer-based models such as BERT, RoBERTa, and GPT-3.	| No	| Widely used	| Neural machine translation, text summarization, question answering | 

# References 

- [A New Algorithm for Data Compression](https://www.derczynski.com/papers/archive/BPE_Gage.pdf)
- [Byte-Pair Encoding Tokenization](https://huggingface.co/course/chapter6/5)
- [Byte-Pair Encoding Algorithm](https://leimao.github.io/blog/Byte-Pair-Encoding/)
- [Tokenizers: How Machines Read](https://blog.floydhub.com/tokenization-nlp/)
- [WordPiece Tokenization](https://huggingface.co/course/chapter6/6)
- [A Fast WordPiece Tokenization System](https://ai.googleblog.com/2021/12/a-fast-wordpiece-tokenization-system.html)
- [Google's Neural Machine Translation System: Bridging the Gap between Human and Machine Translation](https://arxiv.org/abs/1609.08144v2)
- [Training BPE, WordPiece, and Unigram Tokenizers from Scratch using Hugging Face](https://towardsdatascience.com/training-bpe-wordpiece-and-unigram-tokenizers-from-scratch-using-hugging-face-3dd174850713)
- [Subword Regularization: Improving Neural Network Translation Models with Multiple Subword Candidates](https://arxiv.org/pdf/1804.10959.pdf)
- [Summary of the tokenizers](https://huggingface.co/docs/transformers/tokenizer_summary)
- [Unsupervised text tokenizer for Neural Network-based text generation](https://github.com/google/sentencepiece)
