---
title: Additional Criteria for Nominating Committee Eligibility
abbrev: Additional Eligibility Criteria
docname: draft-carpenter-eligibility-expand-02
date: 2020-03-27

# stand_alone: true

ipr: trust200902
area: General
wg: Network Working Group
kw: Internet-Draft
cat: exp
#updates: 8713

coding: us-ascii
pi:
  toc: yes
  sortrefs:   # defaults to yes
  symrefs: yes

author:
      -
        ins: B. E. Carpenter
        name: Brian E. Carpenter
        org: The University of Auckland
        abbrev: Univ. of Auckland
        street:
        - School of Computer Science
        - PB 92019
        city: Auckland
        code: 1142
        country: New Zealand
        email: brian.e.carpenter@gmail.com

      -
        ins: S. Farrell
        name: Stephen Farrell
        org: Trinity College Dublin
        street: College Green
        city: Dublin
        country: Ireland
        email: stephen.farrell@cs.tcd.ie

normative:
  RFC3933:
  RFC8713:

--- abstract

This document defines a process experiment under RFC 3933 that
temporarily updates the criteria for qualifying volunteers
to participate in the IETF Nominating Committee. It therefore
also updates the criteria for qualifying signatories to a
community recall petition. The purpose is to make the criteria
more flexible in view of increasing remote participation in the
IETF and a probable decline in face-to-face meetings. This
document temporarily varies the rules in RFC 8713.

--- middle

# Introduction        {#intro}

According to {{RFC8713}}, the IETF Nominating Committee is populated
from a pool of volunteers with a specified record of attendance at
IETF plenary face-to-face meetings. In view of the unexpected cancellation
of the IETF 107 meeting, the risk of future cancellations, the probability
of less frequent meetings in future in support of sustainability, and
a general increase in remote participation, this document defines a
process experiment {{RFC3933}} of fixed duration to use additional criteria to qualify
volunteers.

Also according to {{RFC8713}}, the qualification for signing a community
petition for the recall of certain IETF office-holders is that same as
for the Nominating Committee. This document does not change that, but
see {{undone}}.

# Term of the Experiment {#term}

The cancellation of the in-person IETF 107 meeting, and the risk of IETF 108
also being cancelled, mean that the current criteria are in any case
seriously perturbed for the next two years. The experiment therefore
needs to start as soon as possible. However, the experiment does not apply
to the selection of the 2020-2021 Nominating Committee.

The experiment will cover the two IETF Nominating Committee cycles starting
in 2021 and 2022. As soon as the 2022-2023 Nominating Committee is seated,
the IESG must consult the Nominating Committee chairs involved and publish a
report on the results of the experiment. The IESG must then also begin a community
discussion of whether to amend {{RFC8713}} in time for the 2023 Nominating
Committee cycle.

# Goals        {#goals}

The goals of the additional criteria are as follows:

- Mitigate the issue of active remote (or rarely in-person) participants being disenfranchised in the NomCom and recall processes.

- Prepare for an era in which face-to-face plenary meetings are less frequent (thus extending the issue to many, perhaps a majority, of participants).

- Ensure that those eligible are true "participants" with enough current understanding of IETF practice and people to make informed decisions.

- The criteria must be algorithmic so that the Secretariat can check them mechanically.


# Criteria     {#crit}

There will be several alternative paths to qualification, replacing the single criterion in section 4.14 of {{RFC8713}}. Any one of the paths is sufficient, unless the person is otherwise disqualified under section 4.15 of {{RFC8713}}:

- Path 1: As per {{RFC8713}}, the person has attended 3 out of the last 5 in-person IETF meetings. 

- Path 2: Has been a WG Chair or Secretary within the last 3 years.

- Path 3: (Feedback on path 3 from draft-01 was uniformly negative so ignore this, we'll leave the text here for now just to avoid renumbering.)

- Path 4: Has served in the IESG or IAB, or has been appointed to a formal role by the IESG or IAB, within the last 5 years.

- Path 5: Has been a listed author of at least 2 IETF stream RFCs within the last 5 years. A draft that has been approved by the IESG and is in the RFC Editor queue counts.

# Open Questions {#open}

- Should we also consider authorship of drafts formally adopted by a WG? 

- Should BOF chairs qualify for Path 2?

- Should we consider remote meeting attendance and if so how do we measure it?
Is there any difference from this point of view between plenary and interim meetings?

- Should we consider how many nomcom voting members qualify via which paths? 
For example, would it be ok if all 10 nomcom voting members qualified via
path 4 in one year?

Certain criteria were rejected as not truly indicating effective IETF participation.
These included authorship of individual Internet-Drafts, sending email to IETF lists,
etc. Since the criteria must be objectively and mechanically measurable, no 
qualitative evaluation of an individual's contributions is considered. 

# Possible Future Work {#undone}

- Combined paths (e.g., a person who partly satisfies Path 2 and Path 5);
otherwise known as a "points system". That seems to involve work/complexity either
for the secretariat or for the volunteer.

- Tweaking the "time decay" in each of the path definitions that ensures
recent participation is more highly valued.

- Separating the NomCom volunteer criteria from the recall petitioner criteria.

# IANA Considerations

This document makes no request of IANA.

# Security Considerations

This document should not affect the security of the Internet.

# Acknowledgements

Useful comments were received from John Klensin, Warren Kumari, Michael Richardson, Martin Thomson, (to be completed)


--- back

# Change Log

## Draft-01 to -02

- Made this 3933 process experiment

- Eliminated path based on directorate reviews, used to be: "Has submitted at
  least 6 reviews as a member of an official IETF review team within the last 3
  years."

- Other comments from IETF107 virtual gendispatch meeting handled

## Draft-00 to -01

- Added author


