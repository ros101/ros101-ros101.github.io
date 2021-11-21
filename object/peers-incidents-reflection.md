---
layout: notes
---
# Reviews of peers' incident reports - Reflections

After I analyzed the crash of the two 737 Max, I reviewed the incidents described by my peers to study the reason for the failures.

These are the findings:

<table class="table table-striped">
  <tr>
    <th class="text-center" scope="col">Incident</th>
    <th class="text-center" scope="col">Poor specifications</th>
    <th class="text-center" scope="col">Poor design</th>
    <th class="text-center" scope="col">Bug</th>
    <th class="text-center" scope="col">Detectable with testing</th>
    <th class="text-center" scope="col">Poor operations</th>
    <th class="text-center" scope="col">Poor management</th>
  </tr>
  <tr>
    <td scope="row"><a href="./incident">Crash of the 737 MAX</a></td>
    <td class="text-center"></td>
    <td class="text-center">Missing redundancy</td>
    <td class="text-center"></td>
    <td class="text-center">Easy to reproduce</td>
    <td class="text-center">Missing documentation</td>
    <td class="text-center">Economic pressure</td>
  </tr>
  <tr>
    <td scope="row"><a href="./incident-train">Train collision</a></td>
    <td class="text-center ">Lack of specifications</td>
    <td class="text-center"></td>
    <td class="text-center">Error in the code</td>
    <td class="text-center">Easy to reproduce</td>
    <td class="text-center"></td>
    <td class="text-center"></td>
  </tr>
  <tr>
    <td scope="row"><a href="./incident-cms">Unavailability of healthcare system</a></td>
    <td class="text-center"></td>
    <td class="text-center"></td>
    <td class="text-center"></td>
    <td class="text-center"></td>
    <td class="text-center">Old design</td>
    <td class="text-center">Lack of investments</td>
  </tr>
  <tr>
    <td scope="row"><a href="./incident-ada">Failed rocket launch</a></td>
    <td class="text-center"></td>
    <td class="text-center"></td>
    <td class="text-center">Misuse</td>
    <td class="text-center">Condition not tested</td>
    <td class="text-center"></td>
    <td class="text-center"></td>
  </tr>
  <tr>
    <td scope="row"><a href="./incident-knight">Trading application generating incorrect orders</a></td>
    <td class="text-center"></td>
    <td class="text-center"></td>
    <td class="text-center">Poor coding hygiene</td>
    <td class="text-center">Lack of testing</td>
    <td class="text-center">Lack of monitoring</td>
    <td class="text-center">Inobservance of rules</td>
  </tr>
</table>

Bugs and poor operation are the prevalent IT issues. Poor design and poor specifications are also IT problems. In four cases, testing could have detected the issue. It is also clear that management has a responsibility for the incidents. I would have expected a higher weight of responsibility on poor requirements and poor design. I wonder if the impact is so high on the latest stages of the SDLC because overall requirements and design are usually of sufficient quality, are not so determinant for the result, or because the sample is too small to be significant.

During my professional experience, I faced all the mentioned issues: poor specifications resulting in building the wrong product, bad coding standards or practices, testing as an afterthought, and very often management unable to understand the basics of software development or to evaluate its impact on the business.

I wish I could say that better engineers and practices could spare the world from such incidents, but nothing helps when a watered-down compromise on quality is accepted by management to prioritize deadlines or cost. It appears logical to conclude that it is of fundamental importance to adopt cost-effective practices to test and operate the software.

Test automation with the highest possible coverage and continuous monitoring of the operations could make the difference. In the case of 737 Max, testing with faulty inputs could have suggested a failure in the design. Several flights reported issues that could have given valid inputs to diagnose the problem before the first incident. In the case of the rocket launch, the language itself had features to test the implementation and suggest potential errors in a very early stage of development. In the case of the trading application, a better testing coverage could have triggered the faulty functionality alerting the development team. It was also discovered that actually there were warnings sent by the application and they were simply ignored for lack of monitoring.

In conclusion, it appears that investment in automatic testing and monitoring, keeping the eye on containing the costs, could mitigate many risks, including pressure from managers caused by cost and time.
