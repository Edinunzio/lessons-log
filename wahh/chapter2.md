# Core Defense Mechanisms

*Core defense mechanisms against potentially malicious user input*
  * Handling user access to application's data and functionality to prevent users from gaining unauthorized access
  * Handling user input to the application's functions to prevent malformed input from causing undesirable behavior
  * Handling attackers to ensure that the application behaves appropriately when being targeted, taking suitable defensive and offensive measures to frustrate the attacker
  * Managing the application itself by enabling administrators to monitor its activities and configure its functionality

## Handling User Access
### Authentication
### Session Management
### Access Control
## Handling User Input
### Varieties of Input
### Approaches to Input Handling
#### "Reject Known Bad"
#### "Accept Known Good"
#### Sanitization
#### Safe Data Handling
#### Semantic Checks
### Boundary Validation
### Multistep Validation and Canonicalization
## Handling Attackers
### Handling Errors
### Maintaining Audit Logs
### Alerting Administrators
### Reacting to Attacks
## Managing the Application

### Questions
1. Why are an application's mechanisms for handling user access only as strong as the weakest of these components?
2. What is the difference between a session and a session token?
3. Why is it not always possible to use a whitelist-based approach to input validation?
4. You are attacking an application that implements an administrative function. You do not have any valid credentials to use the function. Why should you nevertheless pay close attention to it?
5. An input validation mechanism designed to block cross-site scripting attacks performs the following sequence of steps on an item of input:
  1. Strip any ```<script>``` expressions that appear
  2. Truncate the input to 50 characters.
  3. Remove any quotation marks within the input.
  4. URL-decode the input.
  5. If any of the items were deleted, return to step 1.

Can you bypass this validation mechanism to smuggle the following data past it?
 \\ "><script>alert("foo")</script>