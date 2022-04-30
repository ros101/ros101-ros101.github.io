---
layout: notes
---
# Reflections

## Unit 1

I chose to describe a Cross-Site Forgery Attack because I am very familiar with it. I wanted to focus on the presentation of the vulnerability more than on the technical aspects because I often find it difficult to communicate such technical aspects to colleagues without a technical background. I chose to break down the logic with detailed activity diagrams and use as little code as possible.

## Unit 2

I did not want to dedicate much time to Scrum because it is not a topic I find interesting. The theory has its value, but in the market, the industry of certifications and consultants sell a version of Agile that result palatable to traditional management and diverges from the basic principles.

Reflecting on employees' cybersecurity risks is very useful for me because I often work in contexts where cyberattacks can severely harm my organization, and it is necessary to compromise security with practical everyday issues. It is arduous to synthesize the concept of acceptable risk and mitigation within the word limit while still maintaining clarity. I find my post barely sufficient to present the issue, but unable to make a dent in large organizations where initiatives require detailed descriptions to gain traction. It is a good exercise though.

For the discussion, I chose SQL Injection because it is probably the most common programming error I see professionally, and I think it is the one that requires the most attention. The other topic I chose is the exploitation of buffer overflows. I used to develop in C and I was fascinated by this issue when used to inject code. I am amazed by the fact that this is still a relatively common issue and that the industry did not abandon unsafe programming languages. Recently I was exploring Rust and I think it could replace C/C++ in all new projects.

## Unit 3

I am happy about the comments I received. Some questions were on points that I assumed were widely known, and this is a common mistake I make. I need to find a way to present concepts clearly, without assuming preexisting knowledge on the topic, and I need to synthesize them in a few words. Maybe creative writing with a focus on poetry may help. The usage of metaphors helps immensely to explain software architecture, and learning the basics of creative writing helped me in that.

The team discussion on secure programming does not seem to gain interest in Slack. I presume that not everyone is in line with the progress of the unit.

The Codio activities were not very valuable for me. Producer-consumer may be useful for the implementation of the final assignment, but the exercise's solution does not seem to be suitable for us.

## Unit 4

The discussion about secure programming eventually happened with a few other students in the general channel on Slack. I do not consider Python safe because it is really easy to make mistakes that are not immediately visible. However, it is interesting to know that Python is much better than Java in using different metrics. Java is the leading solution in many mission-critical contexts, and it is the technology I use the most, so I probably have a bias. I observe that the metrics consider the safety of the language in its pure form, which is unrealistic because, at least for Java, nobody uses the JDK directly anymore.

I was surprised by the reading about ReDOS because I implemented regexes for years and I have never heard about this risk. I even have a certification for secure software programming! I wonder how many vulnerable regexes I left behind me.

The towers of Hanoi is a classic I solved many times when I was younger, but now I cannot easily do it anymore. Part of the issue is that I know how it is supposed to be solved, and I block myself with my perfectionism. I will solve it in another moment before the end of the course.

I am very used to writing regexes, but I could not write a single one able to extract all the possible fields of a British postcode in all its combinations. I had to accept a solution that does not extract one field and relies on some code to reference the groups. It is not satisfactory because it is neither good code nor a comprehensive regex.

Again, the team discussion (this time about cyclomatic complexity) does not seem to start.

## Unit 5

I gave it a try at the tower of Hanoi and it was a simple exercise once I sketched the idea on paper. It took me more time to write the interface to show the results and eventually I settled for printing the size of the disks. It was taking too much time to make a generic solution.

I am not very familiar with the concept of equivalence partitioning, and I do not fully grasp this exercise. It is clear however what goal it tries to achieve. I find it hard to relate this to real-world testing.

Again, the team discussion (this time about cyclomatic complexity) does not seem to start.

Pylint is the solution I needed! Java does not use similar tools, so it was hard for me to know what to look for. It seems to be useful to spot unused variables and trivial errors. I wish I had it in the previous assignments. I'll make sure to use it for the final assignment too.

## Unit 6

This week is dedicated to the mid-course assignment. I avoid comments here.

## Unit 7

I have never seen an ontology before, and I wonder what could be the practical purpose of writing one. It seems a more general replacement for UML.

I often write simple tools to support my work, like token generators or scripts to execute long repetitive tasks, and I heavily customize my shell by adding aliases and functions. I never got the idea of writing a shell that could intercept my custom commands and forward the rest. It was a fun exercise. When I saved the project, I made a typo (and probably the autocorrection is an accomplice): I called it "Michelle" instead of "Myshell". I liked it, so I decided to leave it. I may actually develop it further for personal use. I would love to have a shell that autocompletes shell commands for Docker and Kubernetes and highlights elements of the output.

The Flask exercise comes too late. I already developed many APIs for the project, and this unit suggests using a different style. It was easy to refactor the code to use Flask Resources, but I noticed that exceptions are not handled anymore. The documentation is unclear about it, and for now, I will ignore it.

## Unit 8

I used Truecrypt many years ago, and I used to follow its community. I remember the concern for the sudden end of the project and the urban legends to explain what could have happened. I kept using it for a short period, and then I switched to alternatives like VeraCrypt and the native filesystem encryption on Linux and Mac. It was ironic to discover that, although not ideal, Truecrypt's vulnerabilities were not dramatic and I could have kept using it.

I have a better understanding of ontologies now: switching to Protégé helped me understand the potentiality. I am not confident that my model follows any good practice, but (after many attempts) at least it successfully represents the information. I tested the model exploring it from different points of view, and it was satisfactory (technical limitations aside). I briefly considered introducing ontologies at work: none of my colleagues ever heard about them, and there was no interest.

Python seems to have a good and simple-to-use cryptographic library compared to Java's implementation, but just like Java, it does not seem to support strong encryption out of the box. I did not investigate beyond the standard documentation because I am not interested in implementing cryptography and using better implementation is simply a matter of switching frameworks. I decided to expand the shell that I already developed. In a portfolio, it is better to have fewer repositories deeply developed than many shallow ones.

## Unit 9

...

## Unit 10

...

## Unit 11

...

## Unit 12

...
