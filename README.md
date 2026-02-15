# TryCatch-

// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0; 
contract WillThrow {
    error NotAllowedError(string);
    function afunction() public pure{
      //  require(false, "Error Message");
      // asert(false);
        revert NotAllowedError("You are not allowed");
    } 
}

contract ErrorHandling {
    event ErrorLogging(string reason);
    event ErrorLogCode (uint Code);
    event ErrorLogBytes(bytes lowlevelData);
    function catchTheError() public { 
        WillThrow will = new WillThrow();
        try will.afunction(){

        }catch Error(string memory reason) { //for require
                emit ErrorLogging(reason);
            
        } catch Panic (uint errorCode) { // for assert
            emit ErrorLogCode(errorCode);
        }catch (bytes memory lowlevelData) { for lowleveldata
            emit ErrorLogBytes(lowlevelData);
        }

    }
}
