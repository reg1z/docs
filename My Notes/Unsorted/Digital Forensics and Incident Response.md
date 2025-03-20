---
tags:
  - cybersecurity
  - dfir
date: 2025-03-20
---
# Digital Forensics and Incident Response
aka DFIR

## Common Tools

- Eric Zimmerman's Tools
- KAPE - Kroll Artifact Parser and Extractor
- Autopsy
- [Redline](https://fireeye.market/apps/211364)
- [Velociraptor](https://docs.velociraptor.app/docs/overview/)

## Standardized Methods
There are many. This often creates confusion throughout the industry.

- [NIST SP-800-61 Incident Handling Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf) (PDF)
- [SANS Incident Handler's Handbook](https://www.sans.org/white-papers/33901/)

> [!quote]+ PICERL (SANS Acronym)
> 1. **Preparation**: Before an incident happens, preparation needs to be done so that everyone is ready in case of an incident. Preparation includes having the required people, processes, and technology to prevent and respond to incidents.
> 2. **Identification**: An incident is identified through some indicators in the identification phase. These indicators are then analyzed for False Positives, documented, and communicated to the relevant stakeholders.
> 3. **Containment**: In this phase, the incident is contained, and efforts are made to limit its effects. There can be short-term and long-term fixes for containing the threat based on forensic analysis of the incident that will be a part of this phase.
> 4. **Eradication**: Next, the threat is eradicated from the network. It has to be ensured that a proper forensic analysis is performed and the threat is effectively contained before eradication. For example, if the entry point of the threat actor into the network is not plugged, the threat will not be effectively eradicated, and the actor can gain a foothold again.
> 5. **Recovery**: Once the threat is removed from the network, the services that had been disrupted are brought back as they were before the incident happened.
> 6. **Lessons Learned**: Finally, a review of the incident is performed, the incident is documented, and steps are taken based on the findings from the incident to make sure that the team is better prepared for the next time an incident occurs.