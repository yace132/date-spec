VotingBoard
===========

.. _Types-of-VotingBoard:

-----
types
-----

^^^^^^^^
Election
^^^^^^^^

::

	struct Election{
		bytes32 title;
		address votingAt;
	}

.. _States-of-VotingBoard:

------
states
------

^^^^^^^^^
elections
^^^^^^^^^

``Election[512] elections;``

.. _Functions-of-VotingBoard:

---------
functions
---------

^^^^^^^^^
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
		bytes32[64] options,
		bytes32 proposer,
		uint ageMin,
		uint ageMax,
		uint startTime,
		uint endTime,
		uint votingKey,
		address votersAt
	) onlyAdmin {
		//Voting.new
		//Owner of VotingBoard deploy "Voting" contract
		//Write Voting's title and address to "elections"
	}

^^^^^^^^^^^^^^^
getAllElections
^^^^^^^^^^^^^^^

::

	function getAllElections(
	)returns(Election[512] elections_)

We can get ``title`` and address of every ``Voting`` on ``VotingBoard``.