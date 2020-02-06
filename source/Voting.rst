Voting
======

.. _Ballot:

------
Ballot
------

``struct Ballot{}``

.. _ballotBox:

---------
ballotBox
---------

``Ballot[1024] ballotBox;``

.. _ElectionStates:

--------------
ElectionStates
--------------

``enum ElectionStates { announced, voting, tally, closed }``

.. _state:

-----
state
-----

``ElectionStates state;``

.. _title:

-----
title
-----

``bytes32 title;``

*name of voting*

Chinese is about 10 characters (utf8).

fix-sized title is convenient for developers.

.. _proposer:

--------
proposer
--------

``bytes32 proposer;``

bytes32 for cheaper gas

.. _condition:

---------
condition
---------

``uint ageMin;``

``uint ageMax;``

.. _startTime:

---------
startTime
---------

``uint startTime;``

.. _endTime:

-------
endTime
-------

``uint endTime;``

.. _submitBallot:

------------
submitBallot
------------

::

	function submitBallot(Ballot ballot) 
		duringVoting 
		matchAge
	{
		//check current state
		//check age of voters in ring
		//push "ballot" to "ballotBox"
	}

Voters of ring is provided by ``ballot``.