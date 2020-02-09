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

^^^^^
admin
^^^^^

``address admin;``

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

^^^^^^^^^^^
constructor
^^^^^^^^^^^

::

	function constructor(address admin_){
    	admin=admin_;
    	//set votersAt and votingKey?
    }

``admin`` is not constant. It can change if we deploy to different network. ( Otherwise, we need to modify our contract for different network )

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