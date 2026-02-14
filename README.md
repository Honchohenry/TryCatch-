# TryCatch-

// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0; 
contract WillThrow {
    function afunction() public pure{
        require(false, "Error Message");
    } 
}

contract ErrorHandling {
    event ErrorLogging(string reason);
    function catchTheError() public {
        WillThrow will = new WillThrow();
        try will.afunction(){

        }catch Error(string memory reason) {
                emit ErrorLogging(reason);
            
        } 



    }
}
