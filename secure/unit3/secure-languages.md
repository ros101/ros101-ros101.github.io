---
layout: notes
---
# Secure languages

## What factors determine whether a programming language is secure or not?

From a survey (Fulton et al., 2021) and a study (Croft et al. 2022) it is possible to list concerns and desirable language characteristics

* memory safety
* concurrency safety
* issues related to data mutability
* null pointers
* type safety
* type checking

## Could Python be classed as a secure language? Justify your answer.

Python offers some of the mentioned characteristics, but the lack of type checking leaves it vulnerable to programming errors. A language like offers most of the features, including a solution to deal with null pointers. Scala, also based on JVM, promotes immutability to strengthen concurrency safety.

## Python would be a better language to create operating systems than C. Discuss.

Assuming to be able to compile Python to achieve similar performances, Python may be a valid replacement for many components. I think that the lack of pointers may be an obstacle in the design of low-level components.

# References

Croft, R., Xie, Y., Zahedi, M., Babar, M. A., & Treude, C. (2022). An empirical study of developers’ discussions about security challenges of different programming languages. Empirical Software Engineering, 27(1), 1-52. Available from https://arxiv.org/pdf/2107.13723.pdf [Accessed 26 May 2022]

Fulton, K. R., Chan, A., Votipka, D., Hicks, M., & Mazurek, M. L. (2021). Benefits and drawbacks of adopting a secure programming language: rust as a case study. In Seventeenth Symposium on Usable Privacy and Security (SOUPS 2021) (pp. 597-616). Available from https://www.usenix.org/system/files/soups2021-fulton.pdf [Accessed 26 May 2022]
