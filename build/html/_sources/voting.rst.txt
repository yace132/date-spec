Voting
======

.. _Types-of-Voting:

-----
types
-----

^^^^^^
Ballot
^^^^^^

::

	struct Ballot{
		encryptedmsg; //???
		uint keyImageX;
		uint keyImageY;
		uint[5] indices of voters;
		sig;
		//random # : c=q array ,r= w array 
		//uint256 for each q, wuint256[ring size]
	}

Point is represented as x,y not [x,y] or Point{x,y}. It is convenient to assign tuple, e.g. ``(x,y) = (newX,newY)``.


^^^^^^^^^^^^^^
ElectionStates
^^^^^^^^^^^^^^

``enum ElectionStates { announced, voting, tally }``

.. _States-of-Voting:

------
states
------

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

^^^^^^^
options
^^^^^^^

``bytes32[64] options;``

Proposer provides names of options. Option is 0, if there are less than 63 options. People can choose options[1], options[2], ... ,options[63].

*name of voting*

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

^^^^^^^^^
votingKey
^^^^^^^^^

``uint votingKey;``

^^^^^^^^
votersAt
^^^^^^^^

``address votersAt;``

.. _Functions-of-Voting:

---------
functions
---------

^^^^^^^^^^^
constructor
^^^^^^^^^^^

::

	constructor(
		bytes32 title_,
		bytes32[64] options_, 
		bytes32 proposer_,
		uint age_min_,
		uint age_max_,
		uint start_time_,
		uint end_time_,
		uint voting_key_,
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
		//	get voters' informations from "Voters.voterTable"
		//Check no repeat voting ( key image )
		//Push "ballot" to "ballotBox"
	}

*Everone can submit his vote during voting.*

Voters of ring is provided by ``ballot``.
Get inforamtions from ``voters`` contract and check age.
May return some event.
check ring signature size=5.


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

Accept at most 128 candicates.