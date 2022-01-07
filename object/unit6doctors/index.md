---
layout: notes
---
# Doctor's surgery

Premise: the scenario is unclear about the role of the nurses and I assumed to be possible to book an appointment with nurses too (in the Netherlands this is common). I also assumed that a patient may have only one doctor.


## Class diagram

I modeled the core of the application around the Calendar. A Calendar contains TimeSlots that represents the moments when the MedicalStaff is available. The TimeSlot can be used by one Appointment only.

Patients may have any number of Prescriptions.

<img class="img-responsive" src="doctors-class.png" alt="Class Diagram for Doctor's surgery">

## Object Diagram

I found it useful to model the objects too. This let me spot errors in my class diagram.

Calendar is a collection of TimeSlots, but TimeSlots can go indefinitely in the future. To avoid a problem with memory, the calendar implements lazy-loading so the instances of TimeSlot are only "virtual" until they are used.

For example: ___Calendar.getTimeSlot(25, 'December', 2999)___ should check if the TimeSlot already exists, create it if it does not, and return it to the caller.

<img class="img-responsive" src="doctors-object.png" alt="Object Diagram for Doctor's surgery">

## Sequence Diagram

I modeled the "human" components as actors in the system to distinguish them from the services. The "alt" blocks represent alternatives depending by what the patient does.

<img class="img-responsive" src="doctors-sequence.png" alt="Sequence Diagram for Doctor's surgery">

## Activity diagram

This diagram adds depth to the sequence diagram. I grouped the macro activities in blocks: booking, cancelling, visiting a nurse, and visiting a doctor. Each block also models the two parties interacting to complete the sub-activity.

<img class="img-responsive" src="doctors-activity.png" alt="Activity Diagram for Doctor's surgery">

[Source file](doctors.vpd) editable on [Visual Paradigm](https://online.visual-paradigm.com)
