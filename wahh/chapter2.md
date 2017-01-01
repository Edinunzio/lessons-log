# Core Defense Mechanisms

*Core defense mechanisms against potentially malicious user input*
  * Handling user access to application's data and functionality to prevent users from gaining unauthorized access
  * Handling user input to the application's functions to prevent malformed input from causing undesirable behavior
  * Handling attackers to ensure that the application behaves appropriately when being targeted, taking suitable defensive and offensive measures to frustrate the attacker
  * Managing the application itself by enabling administrators to monitor its activities and configure its functionality

## Handling User Access

### Authentication
This is one of the most basic dependencies in an application's handling of user access. Involves establishing the user is who they say they are. Typically done with username and passwords.

### Session Management
Sessions are a way to identify and process the series of requests that originate from each user. The web application creates a session for each user, and issues the user a token that identifies the session. 

The majority of attacks seek to compromise the tokens issued to other users. If so, the attacker can masquerade as the authenticated victim.

### Access Control
Final logical step in user access control is to make and enforce correct decisions about whether each individual request should be permitted or denied.

## Handling User Input
Since a huge variety of attacks involve unexpected input, the application must handle user input in a safe manner. "Input validation" is commonly cited as a defense, but it is not bullet proof.

### Varieties of Input
Because of the many types of input, there is no one size fits all validation check. An application can impose strict limitations on specific fields, but other fields may require accepting arbitrary input.

**When an application detects that server-generated data has been modified in a way that is not possible for an ordinary user with a standard browser, the application should reject the request and log the incident for potential investigation.**

### Approaches to Input Handling
#### "Reject Known Bad"
This approach blacklists known bad entities. It's considered weak because clever encoding can bypass the list. For example:
  * If ```SELECT``` is blocked, try ```SeLeCt```
  * If ``` or 1=1--``` is blocked, try ``` or 2=2--```
  * If ```alert('xss')``` is blocked, try ```prompt('xss')```
  * Inserting a ```NULL``` byte anywhere before a blocked expression can cause some filters to stop processing the input and therefore not identify the expression

#### "Accept Known Good"
Mechanism allows data that matches the whitelist, and blocks everything else.

#### Sanitization
Approach that recognizes the need to accept data that can't be guaranteed as safe. Potentially malicious characters may be removed, or encoded, or escaped before further processing occurs.

#### Boundary Validation
Each individual component or functional unit of the server side application treats its inputs as coming from a potentially malicious source. Data validation is performed at each of the trust boundaries, in addition to between the client and the server.

### Multistep Validation and Canonicalization
Clever use of encoding and canonicalization can bypass filters. Very difficult to handle. Recursive based stripping may get stuck in infinite loops. These sorts of things might be better to be rejected outright.

## Handling Attackers
### Handling Errors
A key defense is for the application to handle unexpected errors gracefully. Recover or present suitable error message with no system generated messages nor debug information. Application code should make extensive use of try/catch blocks and checked exceptions.

Unexpected errors often point to defects within the application's defenses.
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
