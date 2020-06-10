# Incidents
***

It is important that we are overly transparent around any and all incidents that happen within our domain. By doing this 
we gain both the organisations and our supporters trust.

Effective incident management is key to limiting the disruption caused by an incident and restoring normal business 
operations as quickly as possible.

## Glossary

* [Declaration of an Incident](#declaration-of-an-incident)
* [Separation of Responsibilities](#separation-of-responsibilities)
* [Team Structure](#team-structure)
* [Incident Documentation](#incident-documentation)

## Declaration of an Incident
It is better to declare an incident early and then find a simple fix and close out the incident than to have to spin up 
the incident management framework hours into a burgeoning problem.

Please refer to the defined [Severity levels](severity-levels.md) for what the definition of an incident should be.

## Separation of Responsibilities

When an incident occurs, it is  important to make sure that everybody involved in the incident knows their role and 
doesn’t stray onto someone else’s turf. A clear separation of responsibilities allows individuals more autonomy than 
they might otherwise have, since they need not second-guess their colleagues.

## Team Structure

Upon the recognition of an incident, we should very quickly come to the consensus of who is in charge of the incident.
From this point, they will start team formation.

### Incident Commander

The incident commander holds the high-level state about the incident. They structure the incident response task force, 
assigning responsibilities according to need and priority. The commander holds all positions that they have 
not delegated. If appropriate, they can remove roadblocks that prevent the incident team from working most effectively.

### Operations Lead
The Operations lead works with the incident commander to respond to the incident by applying operational tools to the 
task at hand. The operations team should be the only group modifying the system during an incident.

## Incident Documentation

### Status Page
As part of documenting and communicating an incident, we should update the [status page](https://status.comicrelief.com)
as an incident progresses.

### Live Documentation
The incident commander’s most important responsibility during an incident is to keep a living incident document which
should ideally be editable by several people concurrently.

This living documentation can be messy, but must be functional as should be retained for postmortem analysis.

### Post Mortem
Within 5 days of the incident, a post mortem meeting should be held. This meeting should provide a root cause analysis
and timeline of the event. 

See the [post mortem template](post-mortem-template.md) for more information on how this should be formatted.

## Further Reading

Much of the above strategy and information was taken from the 
[Google SRE Handbook](https://landing.google.com/sre/sre-book/chapters/managing-incidents/) around managing incidents.
