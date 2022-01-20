---
layout: notes
---
# Alternatives to SQL

NoSQL databases use structures different from tables to organize information. Key-value databases use a simple key to refer to an aggregation. Column-oriented databases work similarly adding additional dimensions to the single key. Document databases are a special case of a key-value database where the aggregation is a structure in JSON or XML. Graph databases use nodes and links to optimize the navigation of networks of relationships (Sadalage & Fowler, 2013).

Each product optimizes a different aspect. Generally, key-value databases have the best performances, while document databases are the slowest (Martins et al., 2019), but make it possible to handle complex queries that would be impossible on SQL databases (Fowler, 2012). Graph databases optimize reading at the cost of insertion (Sadalage & Fowler, 2013). All NoSQL databases handle a large amount of data better than SQL (Fowler, 2012).

NoSQL databases are designed to work in clusters to achieve scalability (Fowler, 2012). Given the limits imposed by the CAP theorem, most products offer only “eventual consistency” with conflict detection to favor availability, while support for ACID transactions is costly and rarely supported (Davoudian et al, 2018). While NoSQL has an edge for rapid development, scalability, and costs, they are still immature and suffer from a lack of standardization compared to SQL databases (Ali et al., 2019).


## References

Ali, W., Shafique, M. U., Majeed, M. A., & Raza, A. (2019) Comparison between SQL and NoSQL databases and their relationship with big data analytics. Asian Journal of Research in Computer Science, 1-10. Available from: [journalajrcos.com](http://journalajrcos.com/index.php/AJRCOS/article/download/30108/56497). [Accessed on 20 January 2022]

Davoudian, A., Chen, L., & Liu, M. (2018) A survey on NoSQL stores. ACM Computing Surveys (CSUR), 51(2), 1-43. Available from: [researchgate.net](https://www.researchgate.net/profile/Ali-Davoudian-2/publication/333863590_Helios_An_Adaptive_and_Query_Workload-driven_Partitioning_Framework_for_Distributed_Graph_Stores/links/5d150eb892851cf440516bc1/Helios-An-Adaptive-and-Query-Workload-driven-Partitioning-Framework-for-Distributed-Graph-Stores.pdf) [Accessed on 20 January 2022]

Fowler, M. (2012) 'Introduction to NoSQL'. GOTO Aarhus 2012. Available from: https://youtu.be/qI_g07C_Q5I [Accessed on 19 January 2022]

Martins, P., Abbasi, M., & Sá, F. (2019) A study over NoSQL performance. World Conference on Information Systems and Technologies (pp. 603-611). Springer, Cham. Available from [researchgate.net](https://www.researchgate.net/profile/Maryam-Abbasi-15/publication/332028074_A_Study_over_NoSQL_Performance/links/5f20143392851cd5fa4e3cc4/A-Study-over-NoSQL-Performance.pdf). [Accessed on 19 January 2022]

Sadalage, P. J. and Fowler, M. (2013) NoSQL Distilled: a brief guide to the emerging world of polyglot persistence. Addison-Wesley Upper Saddle River, NJ. Available from [bigdata-ir.com](https://www.bigdata-ir.com/wp-content/uploads/2017/04/NoSQL-Distilled.pdf). [Accessed on 19 January 2022]
