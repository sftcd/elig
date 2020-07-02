
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
[branch](https://svn.tools.ietf.org/svn/tools/ietfdb/personal/rjs/eligiblity-7.4.1.dev0)
that shows how to generate these lists.

The two most relevant files are
[code](https://svn.tools.ietf.org/svn/tools/ietfdb/personal/rjs/eligibility-7.4.1.dev0/ietf/nomcom/management/commands/list_eligible.py) and
[code](https://svn.tools.ietf.org/svn/tools/ietfdb/personal/rjs/eligibility-7.4.1.dev0/ietf/nomcom/utils.py). The functions at the end of the second file are the ones to look at.

To reproduce the results so far:
- follow the [code-sprint instructions](SprintCoderSetup) to setup an environment (I use the docker stuff)
- clone Robert's [branch](https://svn.tools.ietf.org/svn/tools/ietfdb/personal/rjs/6.127.1.dev1-eligibility)

Then when in the container, you should be able to run:

            user@container$ ./ietf/manage.py list_eligible --file_out=myrun

I don't 100% expect anyone to do all that, but feel free to ask me for
the limited help I can offer if you'd like to.

Note that list4 is generated from a manually curated set (see ietf/nomcom/utils.py above). Sources included the 
[IAB history](https://www.iab.org/about/history/)
and [past members of the IESG](https://www.ietf.org/about/groups/iesg/past-members/.

Results of runs of this were sent to https://mailarchive.ietf.org/arch/msg/eligibility-discuss/Z2eMQi3la9NtKsDQ-WQ-AViyPTM/. That message refers to the Venn diagrams here: (venn-2018-2019.pdf).

The output of the runs was:

    === 2019, looking back 5 years.
    
    $ ietf/manage.py list_eligible --date 2019-04-15 --iesg_iab_date 2014-04-15 --rfc_date 2014-04-15
    List1 has 797 members
    List2 has 253 members
    List2-i has 52 members
    List2-ii has 596 members
    List4 has 55 members
    List4-i has 3 members
    List4-ii has 797 members
    List5 has 759 members
    List5-i has 433 members
    List5-ii has 523 members
    union245 has 846 members
    List1_intersect_union245  has 361 members
    Volunteers in 2019 has 177 members
    List1_intersect_volunteers has 171 members
    union245_intersect_volunteers has 116 members
    intersect_1_union245_volunteers has 115 members
    
    === 2019, looking back 3 years.
    
    $ ietf/manage.py list_eligible --date 2019-04-15 --iesg_iab_date 2016-04-15 --rfc_date 2016-04-15
    List1 has 797 members
    List2 has 253 members
    List2-i has 52 members
    List2-ii has 596 members
    List4 has 43 members
    List4-i has 2 members
    List4-ii has 808 members
    List5 has 513 members
    List5-i has 250 members
    List5-ii has 586 members
    union245 has 638 members
    List1_intersect_union245  has 334 members
    Volunteers in 2019 has 177 members
    List1_intersect_volunteers has 171 members
    union245_intersect_volunteers has 114 members
    intersect_1_union245_volunteers has 113 members
    
    === 2018, looking back 5 years.
    
    $ ietf/manage.py list_eligible --date 2018-04-15 --iesg_iab_date 2013-04-15 --rfc_date 2013-04-15
    List1 has 779 members
    List2 has 253 members
    List2-i has 41 members
    List2-ii has 567 members
    List4 has 62 members
    List4-i has 2 members
    List4-ii has 760 members
    List5 has 838 members
    List5-i has 474 members
    List5-ii has 456 members
    union245 has 923 members
    List1_intersect_union245  has 407 members
    Volunteers in 2018 has 195 members
    List1_intersect_volunteers has 185 members
    union245_intersect_volunteers has 144 members
    intersect_1_union245_volunteers has 142 members
    
    === 2018, looking back 3 years
    
    $ ietf/manage.py list_eligible --date 2018-04-15 --iesg_iab_date 2015-04-15 --rfc_date 2015-04-15
    List1 has 779 members
    List2 has 253 members
    List2-i has 41 members
    List2-ii has 567 members
    List4 has 48 members
    List4-i has 1 members
    List4-ii has 773 members
    List5 has 640 members
    List5-i has 324 members
    List5-ii has 504 members
    union245 has 744 members
    List1_intersect_union245  has 379 members
    Volunteers in 2018 has 195 members
    List1_intersect_volunteers has 185 members
    union245_intersect_volunteers has 139 members
    intersect_1_union245_volunteers has 138 members

# Help

If you'd like me to produce other numbes the command line parameters that 
the tool has are:

			usage: manage.py list_eligible [-h] [--version] [-v {0,1,2,3}]
			                               [--settings SETTINGS] [--pythonpath PYTHONPATH]
			                               [--traceback] [--no-color] [--date DATE]
			                               [--summary]
			                               [--previous_five PREVIOUS_FIVE [PREVIOUS_FIVE ...]]
			                               [--officer_date OFFICER_DATE]
			                               [--officer_roles OFFICER_ROLES [OFFICER_ROLES ...]]
			                               [--group_types GROUP_TYPES [GROUP_TYPES ...]]
			                               [--group_states GROUP_STATES [GROUP_STATES ...]]
			                               [--iesg_iab_date IESG_IAB_DATE]
			                               [--rfc_date RFC_DATE] [--rfc_count RFC_COUNT]
			                               [--file_out FILE_OUT]
			
			List nomcom eligible people using various eligibility criterea.
			
			optional arguments:
			  -h, --help            show this help message and exit
			  --version             show program's version number and exit
			  -v {0,1,2,3}, --verbosity {0,1,2,3}
			                        Verbosity level; 0=minimal output, 1=normal output,
			                        2=verbose output, 3=very verbose output
			  --settings SETTINGS   The Python path to a settings module, e.g.
			                        "myproject.settings.main". If this isn't provided, the
			                        DJANGO_SETTINGS_MODULE environment variable will be
			                        used.
			  --pythonpath PYTHONPATH
			                        A directory to add to the Python path, e.g.
			                        "/home/djangoprojects/myproject".
			  --traceback           Raise on CommandError exceptions
			  --no-color            Don't colorize the command output.
			  --date DATE           Check eligibility as of this date
			  --summary             Show only summary results. Do not enumerate lists.
			  --previous_five PREVIOUS_FIVE [PREVIOUS_FIVE ...]
			                        IETF meeting numbers to use as the previous five
			                        meetings. Ignores --date.
			  --officer_date OFFICER_DATE
			                        Has been a group officer after date
			  --officer_roles OFFICER_ROLES [OFFICER_ROLES ...]
			                        What roles are consider group officer roles
			  --group_types GROUP_TYPES [GROUP_TYPES ...]
			                        What group types are considered for officer roles
			  --group_states GROUP_STATES [GROUP_STATES ...]
			                        What group states are considered for officer roles.
			                        Example: "active" "bof"
			  --iesg_iab_date IESG_IAB_DATE
			                        Was on the IESG or IAB since date
			  --rfc_date RFC_DATE   Was an author of some IETF stream RFCs since date
			  --rfc_count RFC_COUNT
			                        Was an author of at least this many IETF stream rfcs
			  --file_out FILE_OUT   Provide the base of a file name for list outputs

