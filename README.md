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
![image alt](https://github.com/Suraj64139/Introduction-to-Blockchain/blob/fb216ea76beb8a9122fd0d780bea2a8833fc85a8/Screenshot%202025-05-19%20135825.png)
