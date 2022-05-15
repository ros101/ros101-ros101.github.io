---
# to escape : -> &#58;
layout: course
prefix: secure
title: Secure Software Development
completed: false
learnings:
  - Explore the waterfall and agile approaches to software development, with a focus on the implications of developing secure software using each.
  - Become acquainted with the Unified Modelling Language and how it can be used to support software development.
  - Gain a familiarity with the standards which are used by industry to develop secure software.
  - Appreciate the importance of developing a risk-aware culture within an organisation.

artifacts:
  - artifact:
    url: ./unit1
    title: (Unit 1) Cross Site Request Forgery
  - artifact:
    url: ./unit2/csrf-attack
    title: (Unit 2) Cross Site Request Forgery - Discussion
  - artifact:
    url: ./unit2/blog
    title: (Unit 2) How to mitigate employees' risk (blog post)
  - artifact:
    url: ./unit2/table
    title: (Unit 2) Scrum Security review
  - artifact:
    url: ./unit2/sql-injection
    title: (Unit 2) SQL Injection (comment to a Unit 1 peer's post)
  - artifact:
    url: ./unit2/buffer-overflow
    title: (Unit 2) Buffer Overflow (comment to a Unit 1 peer's post)
  - artifact:
    url: ./unit3/csrf-attack-summary
    title: (Unit 3) Cross Site Request Forgery - Summary
  - artifact:
    url: ./unit3/codio-bufferoverflow
    title: (Unit 3) Codio - Buffer overflow
  - artifact:
    url: ./unit3/codio-producer-consumer
    title: (Unit 3) Codio - Producer Consumer
  - artifact:
    url: ./unit3/secure-languages
    title: (Unit 3) Secure languages (team discussion)
  - artifact:
    url: ./unit4/redos
    title: (Unit 4) ReDOS
  - artifact:
    url: ./unit4/hanoi
    title: (Unit 4) Towers of Hanoi
  - artifact:
    url: ./unit4/postcode
    title: (Unit 4) British Postcode
  - artifact:
    url: ./unit5/codio-equivalence
    title: (Unit 5) Codio - Equivalence Testing in Python
  - artifact:
    url: ./unit5/cyclomatic_complexity
    title: (Unit 5) Cyclomatic Complexity (team discussion)
  - artifact:
    url: ./unit6/codio
    title: (Unit 6) Codio - Testing tools
  - artifact:
    url: ./unit7/michelle
    title: (Unit 7) Codio - Michelle, a custom Shell in Python
  - artifact:
    url: ./unit7/flask
    title: (Unit 7) Developing an API for a Distributed Environment (Flask)
  - artifact:
    url: ./unit7/ontology
    title: (Unit 7) Ontology (VOWL)
  - artifact:
    url: ./unit8/encryption
    title: (Unit 8) Encryption in Python
  - artifact:
    url: ./unit8/truecrypt
    title: (Unit 8) Truecrypt report - Discussion
  - artifact:
    url: ./unit9/truecrypt
    title: (Unit 9) Truecrypt report - Follow-up
  - artifact:
    url: ./unit10/faceted
    title: (Unit 10) Faceted data
  - artifact:
    url: ./unit10/truecrypt
    title: (Unit 10) Truecrypt report - final summary
  - artifact:
    url: ./unit11/microkernels
    title: (Unit 11) Microkernels and Microservices

endOfModuleArtifacts:
  - endOfModuleArtifact:
    url: mid-module-system-design
    title: MyMONIT - Collecting measurements to monitor CERN’s experiments
reflections:
  # to escape : -> &#58;
  - reflections:
    url: ./reflections
    title: (Units 1 to 12) Notes-in-progress
  - reflection:
    url: ./unit5/cybersecurity
    title: (Unit 5) Cybersecurity considerations

readings:
  - group:
    title: Unit 1&#58; Introduction to Secure Software Development
    list:
    - Pillai, A.B. (2017) Software Architecture with Python. Birmingham, UK. Packt Publishing Ltd. Chapters 1&6.
    - Asghar, M. Z., Alam, K. A. & Javed, S. (2019) Software Design Patterns Recommendation &#58; A Systematic Literature Review, 2019 International Conference on Frontiers of Information Technology.
    - Royce, W. W. (1970) Managing the Development of Large Software Systems.
    - OMG (2017) Unified Modelling Language, Version 2.5.1.
    - Unified Modelling Homepage
    - Mitre (2017) Weaknesses in OWASP Top Ten.
    - Pohl, C. & Hof, H-J. (2015) Secure Scrum&#58; Development of Secure Software with Scrum, in Proc. of the 9th International Conference on Emerging Security Information, Systems and Technologies.
    - ISO/IEC (2018) ISO/IEC Standard 27000 Section 3.
    - Fowler, M. (2006) Code Smell.
    - Mougouei, D., Sani, F. M., & Almasi, M. (2013) S-Scrum&#58; a Secure Methodology for Agile Development of Web Service, Computer Science and Information Technology.
    - Wichers, D. (2008) Breaking the Waterfall Mindset of the Security Industry. In&#58; OWASP AppSec USA, New York.
    - Manadhata, P. & Wing, J. M. (2004) Measuring a System's Attack Surface, Carnegie Mellon.
    - Ofcom (2019) O2 Network Outage.
    - IBM (2015) 10 Essential Security Practices from IBM.
    - Open Group (2016) The SOA Source Book
    - Casteren, W. Van. (2017) The Waterfall Model and the Agile Methdologies&#58; A Comparison by Project Characteristics.
  - group:
    title: Unit 2&#58; UML Modelling to Support Secure System Planning
    list:
    - Dadzie, J. (2005) Understanding Software Patching, IEEE.
    - Pillai, A.B. (2017) Software Architecture with Python. Birmingham, UK. Packt Publishing Ltd. Chapters 1&6.
    - Accenture security (2020) The Cost of Cybercrime, Ninth Annual Cost of Cybercrime Study.
    - National Institute of Standards and Technology (2020) Cybersecurity Framework.
    - Object Management Group (2020) Unified Architecture Framework (UAF) Domain Metamodel. Version 1.1.
  - group:
    title: Unit 3&#58; Programming Languages&#58;History, Concepts & Design
    list:
    - Pillai, A.B. (2017) Software Architecture with Python. Birmingham, UK. Packt Publishing Ltd. ChapterS 2,6,7&8.
    - Cifuentes, C. & Bierman, G. (2019) What is a Secure Programming Language? 3rd Summit on Advances in Programming Languages (SNAPL).136(3)&#58; 1 - 15.
    - Aiello, J., Wheeler, S. & Koon, S. (2020) What Is Powershell? - Powershell Docs.microsoft.com.
    - Copeland, B. (2017) The Church-Turing Thesis (Stanford Encyclopedia Of Philosophy/Winter 2017 Edition) Stanford.library.sydney.edu.au.
    - VanRoy, P. (2009) Programming Paradigms&#58; What Every Programmer Should Know.
  - group:
    title: Unit 4&#58; Exploring Programming Language Concepts
    list:
    - Larson, E. (2016) Generating Evil Test Strings for Regular Expressions. IEEE International Conference on Software Testing, Verification and Validation (ICST).
    - Larson, E. (2018) Automatic Checking of Regular Expressions. 18th IEEE International Working Conference on Source Code Analysis and Manipulation (SCAM).
    - Jaiswal, S. (2020) Python Regular Expression Tutorial.
    - Weidman, A. (n.d.) Regular expression Denial of Service - ReDoS.
    - Cormen, T. & Balkcom, D. (n.d.) Khan Academy&#58; Towers of Hanoi.
    - Idealpostcodes (2020) The UK Postcode Format.
  - group:
    title: Unit 5&#58; An Introduction to Testing
    list:
    - Pillai, A. B (2017). Software Architecture with Python. Birmingham, UK. Packt Publishing Ltd. Chapters 3,4&10.
    - Ferrer, J., Francisco, C. & Enrique, A. (2012) Estimating Software Testing Complexity. Information and Software Technology.
    - ISO/IEC/IEEE (2015) Software and Systems Engineering – Software Testing – Part 4&#58; Test Techniques, ISO/IEC/IEEE 29119-4.
    - Shepperd, M. (1988) A Critique of Cyclomatic Complexity as a Software Metric, Software Engineering Journal.
    - Song, I. Guedea-Elizalde, F. & Karray, F (2007) CONCORD&#58; A Control Framework for Distributed Real-Time Systems. IEEE Sensors Journal 7(7)&#58;1078 – 1090.
    - Watson, A. H. & McCabe, T. J. (1996) Structured Testing&#58; A Testing Methodology Using the Cyclomatic Complexity Metric. US Department of Commerce Technology Administration National Institute of Standards and Technology. Available from&#58;https&#58;//nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication500-235.pdf.
    - Caldeira, J., Brito e Abreu, F., Cardoso, J. & Reis, J. (2020) Unveiling Process Insights from Refactoring Practices. Computer Science, Arxiv.
  - group:
    title: Unit 6&#58; Using Linters to Support Python Testing
    list:
    - Pillai, A.B. (2017) Software Architecture with Python. Birmingham, UK. Packt Publishing Ltd. Chapters 3,4&10.
    - Python.org (2020) PEP 0 -- Index of Python Enhancement Proposals (PEPs)&#58; Linters.
    - Mannino, J. (n.d.) Security in a Microservice World, OWASP.
  - group:
    title: Unit 7&#58; Introduction to Operating Systems
    list:
    - Saltzer, J. & Schroeder, M. (1975) The Protection of Information in Computer Systems. Proceedings of the IEEE 63(9)&#58; 1278-1308.
    - Szabo, G. (2018) Create your own interactive shell with cmd in Python.
    - Praka, D. (2018) Write a shell in Python.
    - Arnaut, W., Oliveira, K. & Lima, F. (2010) OWL-SOA&#58; A Service Oriented Architecture Ontology Useful during Development Time and Independent from Implementation Time, IEEE.
    - Silberschatz, A., Galvin, P. & Gagne, G. (2018) Operating System Concepts. 10th ed. Hoboken, N.J&#58; Wiley. Chapters 2-8, 16, 18 and 19
    - Garfinkel, S., Weise, D. & Strassmann, S., (1994) The Unix-Haters Handbook. 1st ed. San Mateo, Ca.&#58; IDG Books Worldwide.
    - Corbato F. & Vyssotsky V. (1965) Introduction and Overview of the Multics System. Proceedings of the Joint Computer Conference, ACM 1:185– 196.

  - group:
    title: Buffer Overflow (comment)
    list:
    - Chatole, V., & Nagar, G. (2018). Buffer overflow&#58; Mechanism and countermeasures. International Journal of Advanced Research. IDeas And Innovations In Technology, 4(6), 526-529. Available from https&#58;//www.academia.edu/download/58234152/V4I6-1337.pdf [Accessed 15 March 2022]
    - Nwokeji, C. E. (2019) An Overview of Buffer Overflow and Network Intrusion Detection and Prevention Systems. Internation Journal of Innovative Engineering, Technology And Science. ISSN&#58; 2533-7365 Vol. -2, No.-2, March – 2019. Available from https&#58;//ijiets.coou.edu.ng/wp-content/uploads/journal/published_paper/volume-2/issue-2/Sy133Z0o.pdf [Accessed 15 March 2022]
  - group:
    title: How to mitigate employees’ risk
    list:
    - Herath, T., Rao, H. R. (2009). Protection motivation and deterrence&#58; a framework for security policy compliance in organisations. European Journal of Information Systems 18(2)&#58; 106–125. Available from&#58;http&#58;//130.18.86.27/faculty/warkentin/BIS9613papers/EJIS_SpecialIssue/HerathRao2009_EJIS_18_2_secpolicy_compliance.pdf [Accessed 12/03/2022]
    - Johnston, A. C., Warkentin, M. (2010). Fear Appeals and Information Security Behaviors&#58; An Empirical Study. MIS Quarterly&#58; 34(3) 549–566. Available from https&#58;//www.researchgate.net/profile/Merrill-Warkentin/publication/299049399_Fear_Appeals_and_Information_Security_Behaviors_An_Empirical_Study/links/09e4150f98f11a78cf000000/Fear-Appeals-and-Information-Security-Behaviors-An-Empirical-Study.pdf [Accessed 12/03/2022]
    - Kerman, A., Borchert, O., Rose, S., Tan, A. (2020) Implementing a zero trust architecture. National Institute of Standards and Technology (NIST). Available from&#58; https&#58;//www.nccoe.nist.gov/sites/default/files/legacy-files/zt-arch-project-description-draft.pdf [Accessed 12/03/2022]
    - Monev, V. (2020) Organisational Information Security Maturity Assessment Based on ISO 27001 and ISO 27002. 2020 International Conference on Information Technologies (InfoTech). DOI&#58; 10.1109/InfoTech49733.2020.9211066
    - Rose, S., Borchert, O., Mitchell, S., Connelly, S. (2020) “Zero trust architecture”. No. NIST Special Publication (SP) 800-207). National Institute of Standards and Technology. Available from https&#58;//nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-207.pdf [Accessed 12/03/2022]
    - Sandhu, R. S., Samarati, P. (1994) Access control&#58; principle and practice. IEEE communications magazine&#58;32(9), 40-48. Available from https&#58;//profsandhu.com/cs6393_s16/SS-1994.pdf [Accessed 12/03/2022]
    - Sophos (2021) 54% Say Cyberattacks Are Too Advanced for Their IT Team to Handle on Their Own. Available from https&#58;//www.sophos.com/en-us/press-office/press-releases/2021/04/ransomware-recovery-cost-reaches-nearly-dollar-2-million-more-than-doubling-in-a-year [Accessed 12/03/2022]
  - group:
    title: Secure languages
    list:
    - Croft, R., Xie, Y., Zahedi, M., Babar, M. A., & Treude, C. (2022). An empirical study of developers’ discussions about security challenges of different programming languages. Empirical Software Engineering, 27(1), 1-52. Available from https&#58;//arxiv.org/pdf/2107.13723.pdf [Accessed 26 May 2022]
    - Fulton, K. R., Chan, A., Votipka, D., Hicks, M., & Mazurek, M. L. (2021). Benefits and drawbacks of adopting a secure programming language&#58;rust as a case study. In Seventeenth Symposium on Usable Privacy and Security (SOUPS 2021) (pp. 597-616). Available from https&#58;//www.usenix.org/system/files/soups2021-fulton.pdf [Accessed 26 May 2022]
  - group:
    title: ReDOS
    list:
    - Almost Perfect Email Regex (N.A.) Email Address Regular Expression That 99.99% Works. Disagree? Join discussion!. Available from https&#58;//www.emailregex.com/ [Accessed&#58;16 March 2022]
    - Crosby, S. A. & Wallach, D. S. (2003) Denial of Service via Algorithmic Complexity Attacks. Proceedings of the 12th USENIX Security Symposium. Washington, D.C., USA. August 4-8, 2003. Available from https&#58;//www.usenix.org/conference/12th-usenix-security-symposium/denial-service-algorithmic-complexity-attacks. [Accessed&#58;16 March 2022]
    - Futoransky, A., Gutesman, E., & Waissbein, A. (2007). A dynamic technique for enhancing the security and privacy of web applications. Proc. Black Hat USA. Available from https&#58;//www.researchgate.net/profile/Ariel-Waissbein/publication/240822374_A_dynamic_technique_for_enhancing_the_security_and_privacy_of_web_applications/links/5b85523b92851c1e12377b76/A-dynamic-technique-for-enhancing-the-security-and-privacy-of-web-applications.pdf [Accessed 16 March 2022]
    - Larson, E. (2018) Automatic Checking of Regular Expressions. 18th IEEE International Working Conference on Source Code Analysis and Manipulation (SCAM). Available from http&#58;//fac-staff.seattleu.edu/elarson/web/Research/acre.pdf. [Accessed&#58;16 March 2022]
    - Weidman, A. (N.A.) Regular expression Denial of Service - ReDoS. Available from https&#58;//owasp.org/www-community/attacks/Regular_expression_Denial_of_Service_-_ReDoS. [Accessed&#58;16 March 2022]
    - Weidman, A. (N.A.) Regular expression Denial of Service - ReDoS. Available from https&#58;//checkmarx.com/wp-content/uploads/2015/03/ReDoS-Attacks.pdf. [Accessed&#58;16 March 2022]
---
