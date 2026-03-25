# Why Standards Always Get Messy in Healthcare

You've done the hard part. You got access to the FHIR API. The endpoints are responding. The data is coming back as clean JSON instead of some ancient HL7 pipe-delimited horror. You think you're almost done.

You're not.

FHIR is a more reasonable technology than what came before it, and it's genuinely easier to work with. But FHIR is a standard for data exchange, not a standard for data quality. And there's a gap between how a standard is defined and how it's implemented that no amount of clean API design can close.

---

Take a point-of-care lab test — something like an A1C or a lead test run in a pediatrician's office. Some organizations report it as a structured lab result. Some surface it as a flowsheet entry. Some bury it in the full text of a clinical note. This isn't a FHIR problem. It's the same test, documented three different ways, all three technically compliant with the standard.

When I was building Wingspan Health — software that aggregated clinical data across health systems — I had to build pipelines to go spelunking in notes, pull out whatever was potentially relevant, store it separately, and roll it into lab data so it could be displayed and analyzed as a lab result instead of as a piece of documentation. And this wasn't edge case behavior. It was the majority.

---

Why does this keep happening across every standard, no matter how well-designed?

Because healthcare delivery itself is inconsistent. Electronic medical records are extraordinarily configurable, and that variance ends up encoded in the data model. The same organization could document that point-of-care test three different ways in three different outpatient clinics — not because the software is messy, but because of the internal politics and decision-making patterns of large health systems. Sometimes the providers have more power. Sometimes the hospital owners do. Sometimes things are run by committee. Who gets to decide how the software is configured, who is willing to change their workflows when a new system comes in — all of that influences how things get documented.

The standard reflects the system it was built to describe. The system is not consistent. So the standard, however carefully designed, cannot produce consistent data.

---

This pattern predates FHIR. I've been working in healthcare data since 2012 — at Epic, at athenahealth, at a company I founded. In 2013, I was at an Epic staff meeting when Judy Faulkner explained why they weren't joining CommonWell Health Alliance, a new interoperability network founded by athenahealth, Cerner, McKesson, and others. A year later, I was at another staff meeting when she announced Epic was launching its own framework: Carequality.

Judy Faulkner built Epic with the conviction that everything would be better if everyone was on Epic. Jonathan Bush ran athenahealth as a free-market capitalist who believed healthcare needed more open data exchange. Opposite philosophies, competing incentives, actively antagonistic public postures. They built the same thing. CommonWell and Carequality eventually had to establish a connectivity agreement so their members could exchange data with each other. It took years.

This is how healthcare interoperability standards get made: competing organizations, large committees, people with widely varying backgrounds, all arriving at something functionally equivalent and then spending years getting it to talk to itself.

---

So the question isn't "how do we get a better standard?" That's the wrong question. The question is: how do you build enough robustness into your pipeline to meet the data where it is?

Accept reality. The data is messy. A standard can define what should be in a field. It cannot define what actually ends up there. If you're building on FHIR, build for variance, not for compliance. Assume the same clinical event will arrive in at least three different shapes. Test against real data from multiple organizations before you assume you've handled the edge cases — because in healthcare, the edge cases are the majority.

The gap between how a standard is defined and how it's implemented is not a gap that will eventually close. It's a structural feature of a system that accommodates clinical variation rather than forcing change to how medicine is practiced.

Plan accordingly.
