---
layout: notes
---
# Buffer Overflow (comment)

There are modern techniques to prevent buffer overflows.

Some architectures use a combination of hardware and software called Data Execution Prevention to mark a portion of memory non-executable. It is called NX on AMD, XD on Intel, and XN on ARM (Chatole & Nagar, 2018; Nwokeji, 2019). This solution mitigates the issue, but it is still possible to divert the execution overwriting variables that control the flow.

Modern programming languages offer solutions to prevent overflows. Languages like Java do not let the user manage memory. Others implement bound checks. These solutions are available also in older languages such as C and it is up to the developer to avoid old unprotected functions (Chatole & Nagar, 2018).

Using Stack Canary consists in writing a canary value before a return address to detect an overflow (Nwokeji, 2019).

## Reference

Chatole, V., & Nagar, G. (2018). Buffer overflow: Mechanism and countermeasures. International Journal of Advanced Research. IDeas And Innovations In Technology, 4(6), 526-529. Available from https://www.academia.edu/download/58234152/V4I6-1337.pdf [Accessed 15 March 2022]

Nwokeji, C. E. (2019) An Overview of Buffer Overflow and Network Intrusion Detection and Prevention Systems. Internation Journal of Innovative Engineering, Technology And Science. ISSN: 2533-7365 Vol. -2, No.-2, March – 2019. Available from https://ijiets.coou.edu.ng/wp-content/uploads/journal/published_paper/volume-2/issue-2/Sy133Z0o.pdf [Accessed 15 March 2022]
