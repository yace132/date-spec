Voters
======

.. _Types-of-Voters:

-----
types
-----

^^^^^
Voter
^^^^^

::

	struct Voter{
		uint pubKey;
		uint age;
	}

``pubKey`` for sign ballot. May replace ``age`` with birth year in
future. And add more informations of ``Voter`` on blockchain.

.. _States-of-Voters:

------
states
------

^^^^^
admin
^^^^^

``address public admin;``

^^^^^^
voters
^^^^^^

``Voter[1024] public voters;``

^^^^^^^^^^
voterTable
^^^^^^^^^^

``mapping(uint=>Voter) public voterTable;``

.. _Functions-of-Voters:

---------
functions
---------

^^^^^^^^^
modifiers
^^^^^^^^^

onlyAdmin
"""""""""

^^^^^^^^^
getVoters
^^^^^^^^^

::

	function getVoters(
		uint ageMin,
		uint ageMax
	) view
	returns (uint[1024] voters_) 
	{
		for(uint i=1;i<=1024;i++){
			if(ageMin<=voters[i].age && voters[i].age<=ageMax)
			//voters_.push(voters[i]);
		}
		return voters_;
	}

^^^^^^^^^^^^
selectVoters
^^^^^^^^^^^^

::

	function selectVoters(
		uint ageMin,
		uint ageMax,
		uint seed
	) 
	view
	returns (uint[5] voters_){
		//return rand(getVoters(ageMin,ageMax),seed,5);
	}

Return only voters selected in ring to save bandwidth. Ring size 5 is fixed.

^^^^^^^^
register
^^^^^^^^

::

	constructor register(Voter[1024] voters_)
		onlyAdmin{
		//write "voters_" to "voters" and "voterTable"
	}

`how to send struct array as argument? <https://ethereum.stackexchange.com/questions/70525/how-can-i-send-array-of-structs-as-arguments>`_

Merge ``constructor`` and ``register`` now. b/c people who create ``Voters`` intend to ``register``.
We can optimize gas cost by split these two functions in the future. (Or if too much cost of contract creation)
 