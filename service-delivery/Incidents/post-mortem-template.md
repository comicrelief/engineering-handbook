# Post Mortem Template
***

**Meeting Date:** Schedule the meeting for within 5 business days after the incident. Put the date/time here.

**Attendees:** Who was present at the meeting

## Overview

Include a short sentence or two summarising the contributing factors, timeline summary, and the impact. E.g. "On the morning of August 99th, we suffered a 1 minute SEV-1 due to a runaway process on our primary database machine. This slowness caused roughly 0.024% of alerts that had begun during this time to be delivered out of SLA."

## What Happened

Include a short description of what happened.

## Contributing Factors

Include a description of any conditions that contributed to the issue. If there were any actions taken that exacerbated the issue, also include them here with the intention of learning from any mistakes made during the resolution process.

## Resolution

Include a description what solved the problem. If there was a temporary fix in place, describe that along with the long-term solution.

## Impact

Be very specific here, include exact numbers.

| Impact                             | Statistic                                            |
|------------------------------------|------------------------------------------------------|
| Time in SEV-1                      | ?mins                                                |
| Time in SEV-2                      | ?mins                                                |
| Notifications Delivered out of SLA | ??% (?? of ??)                                       |
| Events Dropped / Not Accepted      | ??% (?? of ??) Should usually be 0, but always check |
| Accounts Affected                  | ??                                                   |
| Users Affected                     | ??                                                   |
| Support Requests Raised            | ?? Include any relevant links to tickets             |

## Responders

Who was involved, this should be generalized and the actual person involved should not be able to be discerned from it?

## Timeline

Some important times to include: (1) time the contributing factor began, (2) time of the page, (3) time that the status page was updated (i.e. when the incident became public), (4) time of any significant actions, (5) time the SEV-2/1 ended, (6) links to tools/logs that show how the timestamp was arrived at.

| Time (UTC) | Event               |
|------------|---------------------|
| 12:14      | This thing happened |

## How'd We Do?

### What Went Well?

* List anything you did well and want to call out. It's OK to not list anything

### What Didn't Go So Well?

* List anything you think we didn't do very well. The intent is that we should follow up on all points here to improve our processes.

## Action Items

Each action item should be in the form of a GitHub ticket, and each ticket should have the same set of two tags: “sev1_YYYYMMDD” (such as sev1_20150911) and simply “sev1”. Include action items such as: (1) any fixes required to prevent the contributing factor in the future, (2) any preparedness tasks that could help mitigate the problem if it came up again, (3) remaining post-mortem steps, such as the internal email, as well as the status-page public post, (4) any improvements to our incident response process.

## Messaging

### Internal Email

This is a follow-up for employees. It should be sent out right after the post-mortem meeting is over. It only needs a short paragraph summarising the incident and a link to this page.

Briefly summarise what happened and where the post-mortem page (this page) can be found.

### External Message

This is what will be included on the status.services.comicrelief.com website regarding this incident.
