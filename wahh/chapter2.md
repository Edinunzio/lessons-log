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
Valuable for investigations. Effective audit logs should allow owners to know:

  * general activity, key events, what activity took place
  * which vulnerabilities were exploited
  * whether attacker gained unauthorized access to data
  * whether attacker performed unauthorized actions
  * provide evidence of intruder's identity

Logs should be strongly protected against unauthorized read or write access.
### Alerting Administrators

A well designed alerting mechanism can use a combination of factors to diagnose that a determined attack is under way and can aggregate related events into a single alert where possible. Anomalous events monitored by alerting mechanisms often include the following:

  * large number of requests, shit that looks scripted
  * business logic usage anomalies
  * known attack strings
  * requests where data hidden from ordinary users has been modified

### Reacting to Attacks
You're not going to be able to block everything. But you can be annoying. Slow down or terminate sessions. Place more obstacles and be more annoying.

## Managing the Application
Admins are a prime target. Does one really need to go into full detail what a malicious admin can do? Plus, how many unit tests have you seen IRL on the admin side? Of those, how many are security mind set driven? There's an inherent danger in assuming admin users can be trusted.
