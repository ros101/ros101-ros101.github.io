---
layout: notes
---
# How to mitigate employees' risk

Companies often underestimate the internal risks. The perimeters are solid, but, on the inside, there is no control, and employees can simply activate malware to cause immense damage. The costs of ransomware attacks more than doubled between 2020 and 2021, aggravated by a complete or partial loss of data (Sophos, 2021).

Zero-trust principles change the traditional strategy moving the security perimeter around every resource. Threats can come from any source regardless of their location (Kerman et al., 2020). No network or device can be inherently trusted. **Access control** should be as granular as possible aiming to a per-request authorization (Rose et al. 2020) following the principles of "least privilege" and "separation of duties" (Sandhu & Samarati, 1994).

This strategy minimizes the risk because the user can only access the resources he effectively needs for his role. However, it does not prevent abuses such as an employee snooping into data for personal reasons. Governance must define security requirements and make employees aware of them (Monev, 2020) by defining **policies** to inform the staff about how to comply with requirements. Employees comply with well-explained policies, especially when they see their peers following them (Herath, 2009; Johnston & Warkentin, 2010). Policies can prescribe technical solutions, such as the utilization of DRM, or promote behaviors to reduce the likelihood of incidents, such as prohibiting personal devices.

Unfortunately, no policy can prevent the most severe violations such as sabotage or espionage committed by an employee in possession of the right authorizations. **Monitoring** and **auditing** are essential to spot possible incidents and are a deterrent. However, the employees in full control of their systems, like system administrators, will always be able to bypass any security measure.

**Risk** can never be zero, but moving from a generalized trust to (almost) zero-trust is a way to reduce it dramatically.

## References

* Herath, T., Rao, H. R. (2009). Protection motivation and deterrence: a framework for security policy compliance in organisations. _European Journal of Information Systems_ 18(2): 106–125. Available from: http://130.18.86.27/faculty/warkentin/BIS9613papers/EJIS_SpecialIssue/HerathRao2009_EJIS_18_2_secpolicy_compliance.pdf [Accessed 12/03/2022]
* Johnston, A. C., Warkentin, M. (2010). Fear Appeals and Information Security Behaviors: An Empirical Study. _MIS Quarterly_: 34(3) 549–566. Available from https://www.researchgate.net/profile/Merrill-Warkentin/publication/299049399_Fear_Appeals_and_Information_Security_Behaviors_An_Empirical_Study/links/09e4150f98f11a78cf000000/Fear-Appeals-and-Information-Security-Behaviors-An-Empirical-Study.pdf [Accessed 12/03/2022]
* Kerman, A., Borchert, O., Rose, S., Tan, A. (2020) Implementing a zero trust architecture. _National Institute of Standards and Technology (NIST)_. Available from: https://www.nccoe.nist.gov/sites/default/files/legacy-files/zt-arch-project-description-draft.pdf [Accessed  12/03/2022]
* Monev, V. (2020) Organisational Information Security Maturity Assessment Based on ISO 27001 and ISO 27002. _2020 International Conference on Information Technologies (InfoTech)_. DOI: 10.1109/InfoTech49733.2020.9211066
* Rose, S., Borchert, O., Mitchell, S., Connelly, S. (2020) "Zero trust architecture". No. NIST Special Publication (SP) 800-207). _National Institute of Standards and Technology_. Available from https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-207.pdf [Accessed 12/03/2022]
* Sandhu, R. S., Samarati, P. (1994) Access control: principle and practice. _IEEE communications magazine_: 32(9), 40-48. Available from https://profsandhu.com/cs6393_s16/SS-1994.pdf [Accessed 12/03/2022]
* Sophos (2021) 54% Say Cyberattacks Are Too Advanced for Their IT Team to Handle on Their Own. Available from https://www.sophos.com/en-us/press-office/press-releases/2021/04/ransomware-recovery-cost-reaches-nearly-dollar-2-million-more-than-doubling-in-a-year [Accessed 12/03/2022]
