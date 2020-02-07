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

.. _States-of-Voters:

------
states
------

^^^^^^
voters
^^^^^^

``Voter[1024] voters;``

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
		uint seed,
		uint size
	) 
	view
	returns (uint[1024] voters_){
		//return rand(getVoters(ageMin,ageMax),seed,size);
	}

^^^^^^^^
register
^^^^^^^^

::

	function register(Voter[1024] voters_)
		onlyAdmin{
		//write "voters_" to "voters" and "voterTable"
	}

https://ethereum.stackexchange.com/questions/70525/how-can-i-send-array-of-structs-as-arguments