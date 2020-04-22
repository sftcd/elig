
# Queries...

As part of developing draft-carpenter-eligibility-expand, the set of queries
we'd like to make against IETF data are:

1. Path#1: who has been at three of the last 5 f2f IETFs?
   (Output: list1, a list of names.)

1. Path#2: Who has been a WG chair or secretary in the last 3 years?  
   (Output: list2, a list of names)

    1. Who gains from path#2? (Output: list2.1=list2\list1)
    1. Who doesn't gain from path#2? (Output: list2.2=list1\list2)

1. Path#3: n/a

1. Path#5: Who has been an author of 2 or more IETF-stream RFCs in the last 5
   years?  (Output: list 5, a list of names)

    1. Who gains from path#5? (Output: list5.1=list5\(list1 U list 2 ))
    1. Who doesn't gain from path#5? (Output: list5.2=(list1 U list 2 U)\list5)

1. Path#4: Who has been on the IAB or IESG in the last 5 years?  
   (Output: list4, a list of names)

1. Who is on List2 or List5 or List4? 
   (Output: List6)

1. Who is on List1 but not (List2, List5 or List4)?
   (Output: List7)

1. Who is on List2 or, List5 or List4 but not List1?
   (Output: List8)

1. Who is on both List1 and List6?
   (Output: List9)

Notation: "A U B" is the union of two lists, "A \ B" is the set of those in A
but not in B.

Why is Path#4 after Path#5? The code to query the datatracker DB doesn't 
seem to find people for list4 who are no longer on the IAB or IESG. I
therefore put that last so I can auto-generate lists 5.1 and 5.2 and
the manually create lists 4, 4.1 and 4.2.

# Deviations from the I-D

This differs from [draft-02](https://tools.ietf.org/html/draft-carpenter-eligibility-expand-02)
in the following ways:

- List2 may also not be quite accurate - it seems we'll miss cases where
someone started as a WG chair 4 years ago and stopped 2 years ago for
example.

# Replication

Robert Sparks was hugely helpful here and made a 
[branch](https://svn.tools.ietf.org/svn/tools/ietfdb/personal/rjs/6.127.1.dev1-eligibility)
that shows how to generate these lists. The results below are from my modified
version of Robert's code. Since this is all early days, I haven't yet created
a branch of my own, but if you want to help/reproduce then:

    - follow the [code-sprint instructions](SprintCoderSetup) to setup an environment (I use the docker stuff)
    - clone Robert's [branch](https://svn.tools.ietf.org/svn/tools/ietfdb/personal/rjs/6.127.1.dev1-eligibility)
    - follow [this](https://pypi.org/project/backports-datetime-fromisoformat/) workaround for a python version issue
    - replace ietf/nomcom/management/commands/list_eligible.py with [this version](list_eligibele.py)

Then when in the container, you should be able to run:

            user@container$ ./ietf/manage.py list_eligible --file_out=myrun

I don't 1000% expect anyone to do all that, but feel free to ask me for
the limited help I can offer if you'd like to.

For list4, I manually created a list based on the [IAB history](https://www.iab.org/about/history/)
and [past members of the IESG](https://www.ietf.org/about/groups/iesg/past-members/). My version
of that list is [here](list4.csv).

# Results

Sizes:
- List1: 647
- List2: 252
- List2.1: 71
- List2.2: 466
- List5: 636
- List5.1: 380
- List5.2: 462
- List4: 48

- List6: 742
- List7: 357
- List8: 452
- List9: 290

A [venn diagram](venn.png) might help.

