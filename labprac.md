# Q1 Create a voting system with multiple candidates. Each address can vote only once.
<br>

```

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Voting {
    address public owner;
    string[] public candidates;
    mapping(address => bool) public hasVoted;
    mapping(string => uint256) public votes;

    constructor(string[] memory _candidates) {
        owner = msg.sender;
        candidates = _candidates;
    }

    function vote(string memory _candidate) public {
        require(!hasVoted[msg.sender], "You have already voted.");
        bool valid = false;
        for (uint i = 0; i < candidates.length; i++) {
            if (keccak256(bytes(candidates[i])) == keccak256(bytes(_candidate))) {
                valid = true;
                break;
            }
        }
        require(valid, "Invalid candidate.");
        votes[_candidate]++;
        hasVoted[msg.sender] = true;
    }

    function getVotes(string memory _candidate) public view returns (uint256) {
        return votes[_candidate];
    }
}

```
<br>

![Screenshot 2025-05-19 135825](https://github.com/user-attachments/assets/12c58483-00d6-467e-b9ef-9f9de0914681)
<br>
![Screenshot 2025-05-19 141801](https://github.com/user-attachments/assets/da7d78f2-baa8-400b-aaf9-17f51f939a98)

<br>

# Q2 Write a contract that manages a list of student records (name, roll number). Allow adding and retrieving student data
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StudentRecords {
    struct Student {
        string name;
        uint256 rollNumber;
    }

    Student[] public students;

    function addStudent(string memory _name, uint256 _rollNumber) public {
        students.push(Student(_name, _rollNumber));
    }

    function getStudent(uint256 index) public view returns (string memory, uint256) {
        require(index < students.length, "Invalid index");
        Student memory student = students[index];
        return (student.name, student.rollNumber);
    }
}

```
![Screenshot 2025-05-19 141508](https://github.com/user-attachments/assets/498caf2d-a1c2-4eac-8259-098c88d5d77b)

<br>

# Qs 3 Develop a contract that only allows the deployer (owner) to call a specific function (use modifiers).
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract OwnerOnly {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Not the owner");
        _;
    }

    function sensitiveFunction() public onlyOwner {
        // Only owner can call this
    }
}

```
![Screenshot 2025-05-19 142100](https://github.com/user-attachments/assets/068597bf-dd21-461a-be29-14861ad8cc43)
<br>

<br>
# Qs 4 Write a contract where people can donate Ether and the top 3 donors are tracked

```

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract TopDonors {
    struct Donor {
        address addr;
        uint amount;
    }

    Donor[3] public topDonors;

    function donate() public payable {
        require(msg.value > 0, "Must send some Ether");
        for (uint i = 0; i < 3; i++) {
            if (msg.value > topDonors[i].amount) {
                for (uint j = 2; j > i; j--) {
                    topDonors[j] = topDonors[j - 1];
                }
                topDonors[i] = Donor(msg.sender, msg.value);
                break;
            }
        }
    }

    function getTopDonors() public view returns (Donor[3] memory) {
        return topDonors;
    }
}
```
![Screenshot 2025-05-19 142635](https://github.com/user-attachments/assets/a9048a6b-2820-42ef-9be2-cfbfb44c4e7e)

<br>

# Qs 5 Implement a simple auction system where users can place bids, and the highest bidder wins.

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Auction {
    address public highestBidder;
    uint public highestBid;

    function bid() public payable {
        require(msg.value > highestBid, "Bid too low");

        if (highestBid != 0) {
            payable(highestBidder).transfer(highestBid); // Refund previous
        }

        highestBidder = msg.sender;
        highestBid = msg.value;
    }
}
```
![Screenshot 2025-05-19 142937](https://github.com/user-attachments/assets/7a3fce12-93ff-497c-8941-798f040563f7)

<br>

# Qs 6 Create a contract that splits incoming Ether between 3 fixed addresses.
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Splitter {
    address payable public addr1;
    address payable public addr2;
    address payable public addr3;

    constructor(address payable _a1, address payable _a2, address payable _a3) {
        addr1 = _a1;
        addr2 = _a2;
        addr3 = _a3;
    }

    receive() external payable {
        uint256 share = msg.value / 3;
        addr1.transfer(share);
        addr2.transfer(share);
        addr3.transfer(msg.value - 2 * share); // Handle remainder
    }
}
```
![Screenshot 2025-05-19 144418](https://github.com/user-attachments/assets/c06ffe41-7d86-41e2-87f0-561b4efb1e83)

<br>


