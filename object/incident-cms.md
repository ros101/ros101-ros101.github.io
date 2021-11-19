---
layout: notes
---
# Clinical Management System failure in Hong Kong: Possible Measures
### Comment on peer's submission

## Possible measures

After brief research, it is clear that CMS has a central role in medical and scientific activity. CMS collects any sort of data: incidence and mortality rates (Wong, 2014), clinical information (Lee et al., 2018), the incidence rate of influenza, discharge diagnoses, laboratory results. "All patient information, including laboratory test results for every clinical admission, is routinely entered into the CMS" (Yeung et al., 2018).

Mission-critical systems developed twenty years ago could not take advantage of cloud-based techniques that guarantee high availability (intended as 99.999% or less than five minutes of downtime per year including maintenance, Nabi et al., 2016). For old systems, availability is achieved with redundancy, for example, a secondary instance of the software waiting in stand-by and ready to be activated with a switch. Depending on how the system is designed, switching can be fast or slow, but it is normally a manual activity requiring detection, diagnosis, and some specialistic activity. In case of a prolonged outage, the backup plan can vary but, for activities such as hospitals, normally includes taking notes on paper and publishing information on whiteboards. This is sometimes ridiculed in newspapers (Inews, 2019; Burrows, 2020), but it is part of the procedures and the staff is trained to do it correctly since the handwritten notes must be transcribed into the system at the earliest time.

Systems running for many years tend to be reliable and problems arise only from occasional and non-systematic events such as a faulty release, a hack, or hardware/network failure. It is possible to learn a lesson from the incident, but the one-time-only nature of some incidents does not always help prevent further incidents in the future. Although modernization would certainly improve the availability of such systems, the cost of the process can be so high that it is economically preferable to incur occasional incidents than starting a project.


## References

Inews (2019) 'Heathrow Airport forced to use flip charts after departure screens go blank'. Inews. Available from https://inews.co.uk/inews-lifestyle/travel/heathrow-staff-forced-to-use-whiteboards-after-departure-screens-go-blank-202299 [Accessed on 19/11/2021]

Lee, C. H., Chan, R. S., Wan, H. Y., Woo, Y. C., Cheung, C. Y., Fong, C. H., ... & Lam, K. S. (2018) Dietary intake of anti-oxidant vitamins A, C, and E Is inversely associated with adverse cardiovascular outcomes in Chinese—A 22-years population-based prospective study. Nutrients, 10(11), 1664.

Nabi, M., Toeroe, M., & Khendek, F. (2016) Availability in the cloud: State of the art. Journal of Network and Computer Applications, 60, 54-67.

Burrows. T. (2020) 'SYSTEMS DOWN Heathrow travel chaos as departure boards FAIL in huge IT glitch sparking cancellations and delays'. The Sun. Available from https://www.thesun.co.uk/news/10975547/heathrow-travel-chaos-departure-boards-fail-it-glitch/ [Accessed on 19/11/2021]

Yeung, K. H. T., Chan, K. C. C., Chan, P. K., Lam, D. S. Y., Sham, P. C. O., Yau, Y. S., ... & Nelson, E. A. S. (2018) Influenza vaccine effectiveness in hospitalised Hong Kong children: feasibility of estimates from routine surveillance data. Vaccine, 36(24), 3477-3485. DOI: https://doi.org/10.1016/j.vaccine.2018.04.081

Wong, G. K. C., Tam, Y. Y. W., Zhu, X. L., & Poon, W. S. (2014) Incidence and mortality of spontaneous subarachnoid hemorrhage in Hong Kong from 2002 to 2010: a Hong Kong hospital authority clinical management system database analysis. World neurosurgery, 81(3-4), 552-556.
