---
layout: notes
---
# Cybersecurity considerations

> Identify and manage security risks as part of a software development project.
Critically analyse development problems and determine appropriate methodologies, tools and techniques (including program design and development) to solve them.
Systematically develop and implement the skills required to be effective member of a development team in a virtual professional environment, adopting real-life perspectives on team roles and organisation.

Use cases and user stories capture the functional requirements of an application and aim to explain what the software should do. Abuse cases and abuse stories, on the other hand, describe cyberattacks and undesirable behaviors that the developer should prevent. A use case could be “login” with a user story like: “as a user, I want to login with my credentials”. The corresponding abuse case could be “break in” with a user story like: “as an unauthorized user, I want to send a brute force attack.

A method to identify abuse stories is to identify the attack surface and then describe attacks to each point. Once the risks are identified, it’s time to describe their mitigation. The process then iterates on the mitigation as a new attack surface. The login form is part of the attack surface and can have one an abuse story about brute force. The mitigation to brute force implies locking the account after too many failed attempts. The attacker could abuse the mitigation to cause a denial of service by purposely inserting the wrong credentials. A mitigation to this new attack is creating a reset button that sends a secret link to the user. The process can iterate as long as needed and, for every attack point, there can be multiple attacks.
When the system has been developed, it is possible to perform tests on the application. With white-box testing, a developer with proper training can spot errors in the code, and there are tools to perform a quick static analysis to spot code smells. Pen tests or black-box tests instead put the tester in the shoes of an attacker and are focused on the attack surface. The result of these tests are reports that the team can translate into stories to improve the application.

Cybersecurity is a very liquid discipline that requires a lot of experience and knowledge that could only stem from training. It also requires a mindset that differs significantly from a developer’s mindset. A developer tends to implement the simplest, most intuitive, and efficient solution, while an attacker looks into the corners to spot neglected areas and experiments with counterintuitive strategies.
