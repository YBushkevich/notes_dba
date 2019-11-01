There’s an important difference between read consistency and rolling back, of course. For read
consistency we make a copy of the data block in memory and apply the undo records to that block, and
it’s a copy of the block that we can discard very rapidly once we’ve finished with it; when rolling back we
acquire the current block and apply the undo record to that. This has three important effects:

  • The data block is the current block, so it is the version of the block that must
eventually be written to disc.
  • Because it is the current block, we will be generating redo as we change it (even
though we are “changing it back to the way it used to be”).
  • Because Oracle has crash-recovery mechanisms that clean up accidents as
efficiently as possible, we need to ensure that the undo record is marked as “undo
applied” as we use it, and doing that generates even more redo.

### Summary 

In some ways redo is a very simple concept: every change to a block in a data file is described by a redo
change vector, and these change vectors are written to the redo log buffer (almost) immediately, and are
ultimately written into the redo log file.

## Transactions and consistency 

This chapter examines the mechanisms Oracle uses to create the linked lists through undo records
and, most importantly, how the code locates the end points of those lists. It also examines the third type
of linked list that was mentioned very briefly in Chapter 2, the linked list that gives us access to historic
commit SCNs (and I’ll describe how Oracle’s “lazy processing” makes that linked list necessary).

We’ll be looking at the transaction table that Oracle keeps in each undo segment header block to
anchor one set of linked lists, and the interested transaction list (ITL) that Oracle keeps in every single
data (and index) block as the anchor to another set of linked lists. Then we’ll take a closer look into the
undo segment header to examine the transaction table control section (hereinafter referred to as the
transaction control) that Oracle uses as the anchor point for the final linked list.

One of the first things we need so that we can coordinate our activity is some sort of focal point for
change. Since, in this scenario, you are the agent of change, you supply the focal point or, rather, two
focal points—the first is a single entry in a special part of the database to act as the primary reference
point for the transaction, and the second appears as an entry in every single table or index block that you
change. We’ll start by looking at the reference point for the transaction.

> Since a rollback call ends with a commit, this would also be used for the commit SCN at the end of a rollback

ITL LIST

Look carefully at the ITL: although we have executed three transactions affecting this block in the
very recent past, there are still only two ITL entries. This is because Oracle tries to keep the ITL as short
as possible, and will reuse ITL entries for committed transactions rather than extend the list. (The ITL
entries will be reused in the order of oldest commit SCN first.)
