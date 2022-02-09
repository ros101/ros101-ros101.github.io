---
layout: notes
---
# Alternatives to SQL - Peer review

It is uncommon, but some NoSQL databases support some form of transactionality. Notably, MongoDB, one of the market leaders, is one of the few supporting multi-document and even distributed multi-document ACID transactions. According to Mongo's team, 80-90% of applications can leverage the document model to avoid transactions entirely (MongoDB, N.D.), but this functionality may make the difference for some use cases.

Another example of transactionality comes from MarkLogicDB. MarkLogicDB supports multi-statement transactions where a statement is a single XQuery module or Javascript script that may span over several documents (MarkLogic, N.D.). Without diving into the intricacy of MarkLogicDB, I can add that transactionality comes at a high price. Statement updating the data lock every document involved, effectively blocking any read from concurrent transactions. Transactions can, and will, cause deadlocks that the database can solve automatically rolling back one of the involved transactions negatively affecting performances.

## References
MarkLogic (N.D.) Understanding Transactions in MarkLogic Server. Available from [docs.marklogic.com](https://docs.marklogic.com/guide/app-dev/transactions) [Accessed 09/02/2022]

MongoDB (N.D.) "What are ACID Transactions?". Available from [www.mongodb.com](https://www.mongodb.com/basics/acid-transactions) [Accessed 09/02/2022]
