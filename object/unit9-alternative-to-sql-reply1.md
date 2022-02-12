---
layout: notes
---
# Alternatives to SQL - Reply

***Question: Can you think of examples where some NoSQL databases are used successfully, commercially?***

NoSQL is an excellent solution for large e-commerce where speed is essential to showcase products to a large audience.  NoSQL is also a convenient solution to ingest large amounts of data, with the flexibility of little to no constraints in the schema. IoT is probably a common type of application where NoSQL is going to grow in the next future.

On top of all these well-known cases, I can add something from my work experience.

An internet provider wanted to collect metrics from the customers' routers to detect malfunctions. The metrics were just a single number, but the frequency of the input was extreme. The solution was a time-series database to store the measures associated with the time. It offered good performances even with limited resources. (Unfortunately, I cannot remember the name of the product)

For an application in the field of artificial intelligence, there was the need for horizontal scalability to improve response time and availability. The solution was to use Hazelcast as an in-memory key-value database. It made it possible to store Java objects in memory and share them across a cluster.

For a mission-critical project in aviation, the data model was extremely complex. The system was based on a NoSQL document database that was discontinued by the vendor. It was necessary to replace such a database with a modern solution. It was estimated that a normalized representation in SQL would have required a join of more than 50 tables to perform the most common operation. SQL was not an option. The application was migrated to MarklogicDB. MarklogicDB was preferred to the more famous MongoDB and CouchDB because it offers a stronger consistency model.
