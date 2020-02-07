VotingBoard
===========

.. _Types-of-VotingBoard:

-----
types
-----

.. _States-of-VotingBoard:

------
states
------

^^^^^^^^^
elections
^^^^^^^^^

``address[512] elections;``

.. _Functions-of-VotingBoard:

---------
functions
---------

modifiers
^^^^^^^^^

onlyAdmin
"""""""""

^^^^^^^^^^^^^^^
proposeElection
^^^^^^^^^^^^^^^

::

	function proposeElection(
		bytes32 title,
		bytes32 proposer,
		uint ageMin,
		uint ageMax,
		uint startTime,
		uint endTime,
		address votersAt
	) onlyAdmin {
		//Owner of VotingBoard deploy "Voting" contract
		//Write Voting's address to "elections"
	}

^^^^^^^^^^^^^^^
getAllElections
^^^^^^^^^^^^^^^

::

	function getAllElections(
	)returns(elections)

