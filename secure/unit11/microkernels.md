---
layout: notes
---
# Microkernels and Microservices

> “Torvalds has been proven wrong and it only took nearly thirty years. Microservices and microkernels are the future. “

Black and white positions on technology do not hold forever because the premise and the context continuously change.

Monolithic kernels had an indisputable success: Linux is one of the most widely used operating systems powering at least half of webservers worldwide (W3techs, 2022), 86% of the mobile phones (Make, 2009; W3school, 2022), and it is installed on all sort of devices (Kan, 2021). Microkernels are also still in active development today keeping the same principles of minimality (Isaac et al., 2021). They are everywhere: in embedded devices, industrial applications, and IoT.

It is hard to tell which model won.

In between micro and monolithic, there are the so called "hybrid kernels" such as NT and XNU powering Windows and MacOs respectively. For this discussion, the most interesting aspect is that there is no consensus on the definition of "hybrid" beyond having a certain degree of modularity (Papadimitriou & Moussiades 2018). In Linus Torvalds' words (2006) "it's just marketing" and "the real issue is the issue of sharing address spaces. Nothing else really matters.".

Similarly, in the discussion between monoliths and microservices I dare to say that the two models are more similar than different from a design perspective. The components of a monolith correspond to the microservices of a distributed application. In fact, one may say that microservices are the evolution of monoliths to address issues with complexity (Dragoni, 2017), flexibility and the organization (Di Francesco et al., 2017).

In my experience working with both models, the main differences sit in the processes for development and deployment: two aspects that reflect the structure of the organization (Conway's Law) more than a conscious technical choice.

Microservices are not hineritely better than monoliths. By breaking down one service in many modules, microservices trade the greater simplicity of each small module for a lot of new complexity in the deployment and the orchestration. It is not a coincidence that the model became popular only when new technologies (namely containers) addressed that issue. I am also sure that the pain points of microservices will be the spark for a new model sometimes in the future. It will take only one more step in the technology, and microservices may become the new dinosaurs we will try to replace with a new model. Or maybe there will be a split in the market depending on the problem to solve, just like it happened with kernels.

## References

Di Francesco, P., Malavolta, I., & Lago, P. (2017, April). Research on architecting microservices: Trends, focus, and potential for industrial adoption. In 2017 IEEE International Conference on Software Architecture (ICSA) (pp. 21-30). IEEE. Available from https://www.ivanomalavolta.com/files/papers/ICSA_2017.pdf

Dragoni, N., Giallorenzo, S., Lafuente, A. L., Mazzara, M., Montesi, F., Mustafin, R., & Safina, L. (2017). Microservices: yesterday, today, and tomorrow. Present and ulterior software engineering, 195-216. Available from https://arxiv.org/pdf/1606.04036.pdf

Liu B., Wu C. & Guo H. (2021), "A Survey of Operating System Microkernel," 2021 International Conference on Intelligent Computing, Automation and Applications (ICAA), 2021, pp. 743-748, doi: 10.1109/ICAA53760.2021.00135. Available from https://ieeexplore.ieee.org/abstract/document/9653483

Torvalds L. (2006) "Hybrid kernel, not NT". Available from https://www.realworldtech.com/forum/?threadid=65915&curpostid=65936

Kan M. (2021) "Linux Is Now on Mars, Thanks to NASA's Perseverance Rover", PC Magazine. Available from https://uk.pcmag.com/drones/131849/linux-is-now-on-mars-thanks-to-nasas-perseverance-rover

Maker, F., & Chan, Y. H. (2009). A survey on android vs. linux. University of California, 1-10.

Isaac O., Okokpujie K., Akinwumi H., Juwe J., Otunuya H. & Alagbe O. (2021) An Overview of Microkernel Based Operating System. IOP Conf. Ser.: Mater. Sci. Eng. Available from https://iopscience.iop.org/article/10.1088/1757-899X/1107/1/012052

Papadimitriou S. and Moussiades L. (2018) "Mac OS versus FreeBSD: A Comparative Evaluation," in Computer, vol. 51, no. 2, pp. 44-53, February 2018, doi: 10.1109/MC.2018.1451648. Available from https://ieeexplore.ieee.org/abstract/document/8301116

W3school (2022) "Mobile devices statistics". Available from https://www.w3schools.com/browsers/browsers_mobile.asp

W3techs (2022) "Usage statistics of operating systems for websites". Available from https://w3techs.com/technologies/overview/operating_system
