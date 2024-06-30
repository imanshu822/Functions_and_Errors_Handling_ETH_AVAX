### ErrorHandlingContract

#### Overview
The `ErrorHandlingContract` is a simple Solidity smart contract designed to demonstrate the use of error handling mechanisms in Solidity. The contract includes functionality to calculate the weight of an object based on its mass, ensuring that only the owner of the contract can perform this calculation and that the inputs are valid.

#### Prerequisites
- Solidity version 0.8.1 or higher

#### Error Handling Mechanisms
This contract utilizes three main error handling mechanisms in Solidity:
1. **Require Statement**
2. **Assert Statement**
3. **Revert Statement**

### Contract Details

#### State Variables
- `uint private constant gravity = 10;`
  - A constant value representing gravity, used in the weight calculation.
- `address private owner;`
  - The address of the contract owner, set during the contract deployment.

#### Constructor
```solidity
constructor() {
    owner = msg.sender;
}
```
- The constructor is executed once when the contract is deployed.
- It sets the `owner` state variable to the address that deploys the contract (`msg.sender`).

#### Function: `weight`
```solidity
function weight(uint _mass) public view returns (uint)
```
- A public function that calculates the weight of an object based on its mass.
- Takes a single argument `_mass` which represents the mass of the object.

##### Require Statement
```solidity
require(owner == msg.sender, "You are not the owner");
```
- Ensures that only the owner of the contract can call this function.
- If the condition fails, the transaction is reverted with the message "You are not the owner".

##### Assert Statement
```solidity
assert(_mass > 0);
```
- Ensures that the mass is greater than zero.
- If `_mass` is not greater than zero, the transaction is reverted without a specific error message.

##### Revert Statement
```solidity
if ((_mass * gravity) < 0) {
    revert("Weight of the object cannot be zero");
}
```
- Ensures that the calculated weight is non-negative.
- If the condition fails, the transaction is reverted with the message "Weight of the object cannot be zero".

##### Return Statement
```solidity
return _mass * gravity;
```
- Returns the calculated weight of the object.

### Summary
The `ErrorHandlingContract` provides a straightforward example of how to use error handling mechanisms in Solidity to ensure the integrity of the contract's functionality and restrict access to certain functions. The use of `require`, `assert`, and `revert` statements helps in validating inputs, enforcing conditions, and providing informative error messages.
