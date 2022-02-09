---
layout: notes
---
# Alternatives to SQL - Peer review

NoSQL databases are typically schema-less, meaning that the data can be anything. However, it is normal to have a "de facto" schema in place because the data must be interpreted in some way. For example, key-value databases can store the record of a book indexed by its ISBN. Even if not enforced by the database, in this example the key will always be a string and probably the book will be a JSON or XML document with its own schema in order to parse it (Fowler, 2012).

Also SQL databases can have excellent performances, including updates (Reichardt, 2021). However, they tend to scale poorly beyond a certain amount of data. SQL databases scale only vertically, with hardware, while NoSQL scale horizontally adding nodes (Babucea, 2021).

## References

Babucea, A. G. (2021). SQL OR NoSQL DATABASES? CRITICAL DIFFERENCES. Annals of'Constantin Brancusi'University of Targu-Jiu. Economy Series, (1). Available from [www.utgjiu.ro](https://www.utgjiu.ro/revista/ec/pdf/2021-01/07_Babucea.pdf) [Accessed on 25 January 2022]

Fowler, M. (2012) 'Introduction to NoSQL'. GOTO Aarhus 2012. Available from: [youtu.be](https://youtu.be/qI_g07C_Q5I) [Accessed on 19 January 2022]
