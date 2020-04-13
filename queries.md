
# Queries...

As part of developing draft-carpenter-eligibility-expand, the set of queries
we'd like to make against IETF data are:

0. If we don't change our BCP but also don't meet f2f for the rest of 2020, who
   would become ineligible in 2021?  (Output: list0, a list of names.)

1. Path#1: With our existing BCP, who would would remain eligible in 2021?
   (Output: list1, a list of names.)

1. Path#2: Who has been a WG chair or secretary in the last N years?  (Input:
   N, Output: list2, a list of names)

    1. Who gains from path#2? (Output: list2.1=list2\list1)
    1. Who doesn't gain from path#2? (Output: list2.2=list1\list2)

1. Path#3: n/a

1. Path#4: Who has been on the IAB or IESG in the last M years?  (Input: M,
   Output: list4, a list of names)

    1. Who gains from path#4? (Output: list4.1=list4\(list1 U list 2))
    1. Who doesn't gain from path#4? (Output: list4.2=(list1 U list 2)\list4)

1. Path#5: Who has been an author of L or more IETF-stream RFCs in the last P
   years?  (Input: L, P, Output: list 5, a list of names)

    1. Who gains from path#5? (Output: list5.1=list5\(list1 U list 2 U list4))
    1. Who doesn't gain from path#5? (Output: list5.2=(list1 U list 2 U
       list4)\list5)


Notation: "A U B" is the union of two lists, "A \ B" is the set of those in A
but not in B.

