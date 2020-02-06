Voting
======

.. _types:

-----
types
-----

^^^^^^
Ballot
^^^^^^

``struct Ballot{}``

^^^^^^^^^^^^^^
ElectionStates
^^^^^^^^^^^^^^

``enum ElectionStates { announced, voting, tally, closed }``

.. _voting_states:

-------------
voting states
-------------

^^^^^^^^^
ballotBox
^^^^^^^^^

``Ballot[1024] ballotBox;``


^^^^^
state
^^^^^

``ElectionStates state;``


^^^^^
title
^^^^^

``bytes32 title;``

*name of voting*

Chinese is about 10 characters (utf8).fix-sized title is convenient for developers.


^^^^^^^^
proposer
^^^^^^^^

``bytes32 proposer;``

bytes32 for cheaper gas


^^^^^^^^^
condition
^^^^^^^^^

``uint ageMin;``

``uint ageMax;``


^^^^^^^^^
startTime
^^^^^^^^^

``uint startTime;``


^^^^^^^
endTime
^^^^^^^

``uint endTime;``


^^^^^^^^
votersAt
^^^^^^^^

``address votersAt;``

.. _functions:

---------
functions
---------

^^^^^^^^^^^
constructor
^^^^^^^^^^^

::

	constructor(
		bytes32 title_,
		bytes32 proposer_,
		uint age_min_,
		uint age_max_,
		uint start_time_,
		uint end_time_,
		address voters_at_
	) public {
	}


modifiers
^^^^^^^^^

hasAnnounced
""""""""""""

duringVoting
""""""""""""

duringTally
"""""""""""

votingClosed
""""""""""""

matchAge
""""""""


^^^^^^^^^^^^
submitBallot
^^^^^^^^^^^^

::

	function submitBallot(Ballot ballot) 
		duringVoting 
		matchAge
	{
		//Check current state
		//Check age of voters in ring
		//	open voters contract
		//	get voters' informations
		//Check no repeat voting ( key image )
		//Push "ballot" to "ballotBox"
	}

*Everone can submit his vote during voting.*

Voters of ring is provided by ``ballot``.
Get inforamtions from ``voters`` contract and check age.
May return some event.


^^^^^
tally
^^^^^

::

	function tally() 
		duringTally 
		returns(uint[128] result)
	{
		//access ballotBox
		//decrypt each vote
		//compute results
		//return results efficiently
	}