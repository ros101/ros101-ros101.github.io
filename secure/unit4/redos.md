---
layout: notes
---
# ReDOS

### What is ReDOS and what part do ‘Evil Regex’ play?

Algorithmic Complexity Attacks are low-bandwidth denial of services exploiting the worst case of algorithms (Crosby & Wallach, 2003). ReDos stands for Regex Denial of Service and is a type of attack that exploits the complexity of the algorithms of regular expressions. Since regex's worst case is exponential, some regex with specific inputs may require a long processing time, effectively causing a DOS. An Evil Regex is a regex vulnerable to this kind of attack. Evil regexes must contain repeating groups, and the group must also contain repetition or alternation with overlapping. (Weidman, N.A. a; Weidman, N.A. b)

### What are the common problems associated with the use of regex? How can these be mitigated?

The most common problem is probably their complexity. It is difficult to write a regex matching the desired input precisely without false positives or negatives. There are software to test regexes with a set of input, but they are not sufficient to cover all corner cases. The infamous case of the regex for email is a good example of how hard it is to write correct regex (Almost Perfect Email Regex, N.A.)

```regex
(?:[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*|"(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21\x23-\x5b\x5d-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])*")@(?:(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?|\[(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?|[a-z0-9-]*[a-z0-9]:(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21-\x5a\x53-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])+)\])
```

Regexes can validate input with a compact expression. However, a poorly crafted regex can accept invalid input resulting in a false sense of security (Futoransky et al., 2007).

An attacker could disrupt an application if he finds an evil regex. Vulnerable regexes could be present in network applications, including those security-related. The attacker could use ReDOS as a weapon to disable or delay security responses (Larson, 2018).

### How and why could regex be used as part of a security solution?

It is a compact way to validate input and it is a solid solution to extract portions from a string.

For example, give this input

```xml
<message><to>foo@bar.com</to><body>this is a test</body></message>
```

can be validated by

```regex
<message><to>.+@(.+)<\/to><body>.*<\/body><\/message>
```

additionally this regex can extract the domain of the email (`bar.com`) making it easy to validate that specific field.

## References

Almost Perfect Email Regex (N.A.) Email Address Regular Expression That 99.99% Works. Disagree? Join discussion!. Available from https://www.emailregex.com/ [Accessed: 16 March 2022]

Crosby, S. A. & Wallach, D. S. (2003) Denial of Service via Algorithmic Complexity Attacks. _Proceedings of the 12th USENIX Security Symposium. Washington_, D.C., USA. August 4-8, 2003. Available from https://www.usenix.org/conference/12th-usenix-security-symposium/denial-service-algorithmic-complexity-attacks. [Accessed: 16 March 2022]

Futoransky, A., Gutesman, E., & Waissbein, A. (2007). A dynamic technique for enhancing the security and privacy of web applications. Proc. Black Hat USA. Available from https://www.researchgate.net/profile/Ariel-Waissbein/publication/240822374_A_dynamic_technique_for_enhancing_the_security_and_privacy_of_web_applications/links/5b85523b92851c1e12377b76/A-dynamic-technique-for-enhancing-the-security-and-privacy-of-web-applications.pdf [Accessed 16 March 2022]

Larson, E. (2018) Automatic Checking of Regular Expressions. 18th IEEE International Working Conference on Source Code Analysis and Manipulation (SCAM). Available from http://fac-staff.seattleu.edu/elarson/web/Research/acre.pdf. [Accessed: 16 March 2022]

Weidman, A. (N.A.) Regular expression Denial of Service - ReDoS. Available from https://owasp.org/www-community/attacks/Regular_expression_Denial_of_Service_-_ReDoS. [Accessed: 16 March 2022]

Weidman, A. (N.A.) Regular expression Denial of Service - ReDoS. Available from https://checkmarx.com/wp-content/uploads/2015/03/ReDoS-Attacks.pdf. [Accessed: 16 March 2022]
