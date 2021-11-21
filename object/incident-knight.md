---
layout: notes
---
# Knight's $440 million glitch&#58; Possible Measures
### Comment on peer's submission

## Possible measures

"On August 1, 2012, while processing 212 small retail orders, Knight Capital Americas LLC (“Knight”) routed millions of orders into the market and obtained over 4 million executions in 154 stocks for more than 397 million shares. Ultimately, Knight lost over $460 million from these unwanted positions." (Murphy, 2013)

SEC discovered that the problem stemmed from an old function called "power peg". Originally power peg was supposed to execute many child orders with a limit set by the maximum capacity of the parent order. Many years before the incident, the limit was moved to a different component, and power peg was hidden behind a flag that made the code unreachable at runtime. In 2012 two errors happened. The flag blocking power peg was repurposed and an old version of the code was installed by mistake in one of the eight servers. This combination activated power peg that kept running without limits (Murphy, 2013).

As pointed out by SEC, Knight made several mistakes ignoring all the rules that impose supervision and measures that can mitigate this kind of incident. From a software development perspective, keeping old dead code is a bad but very common practice. Especially dealing with legacy code (power keg already existed in 2003) very often the rule is "if it works, don't touch it", that is a good rule until an incident happens.

## References

Murphy, E. M. (2013) 'Order instituting administrative and cease-and-desist proceedings, pursuant to sections 15(b) and 21c of the securities exchange act of 1934, making findings, and imposing remedial sanctions and a cease-and-desist order'. Securities Exchange Act of 1934, Release No. 70694 / October 16, 2013. Administrative proceeding File No. 3-1557. Available from https://www.sec.gov/litigation/admin/2013/34-70694.pdf. [Accessed on 20/11/2021]
