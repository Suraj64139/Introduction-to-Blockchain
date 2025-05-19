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

