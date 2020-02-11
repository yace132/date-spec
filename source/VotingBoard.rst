VotingBoard
===========

.. _pragma:

--------
encoding
--------

``pragma experimental ABIEncoderV2;``

*enable nested array and struct encoding*

e.g. string[64] as arguments

.. _Types-of-VotingBoard:

-----
types
-----

^^^^^^^^
Election
^^^^^^^^

::

	struct Election{
		string title;
		address votingAt;
	}

.. _States-of-VotingBoard:

------
states
------

^^^^^
admin
^^^^^

``address public admin;``

^^^^^^^^^
elections
^^^^^^^^^

``Election[512] public elections;``

^^^^^^^^^^^^
numElections
^^^^^^^^^^^^

``uint public numElections;``

*Total number of proposed elections*

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

	function constructor(address admin_)public{
    	admin=admin_;
    }

``admin`` is not constant. It can change if we deploy to different network. ( Otherwise, we need to modify our contract for different network )

^^^^^^^^^^^^^^^
proposeElection
^^^^^^^^^^^^^^^

::

	function proposeElection(
		string memory title,
		string[64] memory options,
		string memory proposer,
		uint ageMin,
		uint ageMax,
		uint startTime,//number of block
		uint endTime,//number of block
		uint votingKey,
		address votersAt
	) 
	onlyAdmin 
	public
	{
		//new Voting();
		//admin (server) deploys "Voting" contract
		//Write Voting's title and address to "elections"
		//numElections++;
	}

May change age to birth year and block number to date in future.

^^^^^^^^^^^^^^^
getAllElections
^^^^^^^^^^^^^^^

::

	function getAllElections(
	)public returns(Election[512] elections_)

We can get ``title`` and address of every ``Voting`` on ``VotingBoard``.